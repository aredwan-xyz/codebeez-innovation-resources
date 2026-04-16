# Building with AI APIs — Ship Your First AI App

A practical guide to going from idea to deployed AI application.

---

## Architecture Patterns

### Pattern 1: Simple Completion App

```
User Input → [API Call] → LLM Response → Display to User
```

Use when: Simple Q&A, text generation, single-turn interactions.

### Pattern 2: Chat Application

```
User Message → [Context Window: System + History + Message] → Response → Update History
```

Use when: Multi-turn conversations, assistants, tutors.

### Pattern 3: RAG (Retrieval-Augmented Generation)

```
User Query → [Embedding] → [Vector Search] → [Retrieved Docs + Query] → LLM → Response
```

Use when: Q&A over your own documents, knowledge bases, customer support.

### Pattern 4: AI Agent

```
User Goal → [LLM: Plan] → [Tool Call] → [Result] → [LLM: Next Step] → ... → Final Answer
```

Use when: Multi-step tasks, web search, code execution, file manipulation.

---

## Quick Start: Python + Anthropic SDK

### Installation

```bash
pip install anthropic python-dotenv
```

### Basic Setup

```python
# .env
ANTHROPIC_API_KEY=sk-ant-...

# app.py
import os
from anthropic import Anthropic
from dotenv import load_dotenv

load_dotenv()
client = Anthropic()
```

### Simple Chat App

```python
import anthropic

client = anthropic.Anthropic()

def chat(messages: list[dict], system: str = "You are a helpful assistant.") -> str:
    response = client.messages.create(
        model="claude-sonnet-4-6",
        max_tokens=2048,
        system=system,
        messages=messages
    )
    return response.content[0].text

# Multi-turn conversation
history = []
while True:
    user_input = input("You: ")
    if user_input.lower() in ["exit", "quit"]:
        break
    
    history.append({"role": "user", "content": user_input})
    response = chat(history)
    history.append({"role": "assistant", "content": response})
    print(f"Claude: {response}\n")
```

### Streaming Responses

```python
def stream_chat(prompt: str) -> None:
    with client.messages.stream(
        model="claude-sonnet-4-6",
        max_tokens=1024,
        messages=[{"role": "user", "content": prompt}]
    ) as stream:
        for text in stream.text_stream:
            print(text, end="", flush=True)
    print()  # newline after stream
```

### Tool Use (Function Calling)

```python
tools = [
    {
        "name": "get_weather",
        "description": "Get the current weather for a location",
        "input_schema": {
            "type": "object",
            "properties": {
                "location": {
                    "type": "string",
                    "description": "City and country, e.g. 'Paris, France'"
                }
            },
            "required": ["location"]
        }
    }
]

def get_weather(location: str) -> dict:
    # Replace with real API call
    return {"temperature": "22°C", "condition": "Sunny", "humidity": "45%"}

def agent_with_tools(user_message: str) -> str:
    messages = [{"role": "user", "content": user_message}]
    
    while True:
        response = client.messages.create(
            model="claude-sonnet-4-6",
            max_tokens=1024,
            tools=tools,
            messages=messages
        )
        
        if response.stop_reason == "end_turn":
            return response.content[0].text
        
        if response.stop_reason == "tool_use":
            tool_use = next(b for b in response.content if b.type == "tool_use")
            tool_name = tool_use.name
            tool_input = tool_use.input
            
            # Execute the tool
            if tool_name == "get_weather":
                result = get_weather(**tool_input)
            
            # Add assistant + tool result to messages
            messages.append({"role": "assistant", "content": response.content})
            messages.append({
                "role": "user",
                "content": [{
                    "type": "tool_result",
                    "tool_use_id": tool_use.id,
                    "content": str(result)
                }]
            })
```

---

## RAG System from Scratch

```python
import anthropic
from typing import List
import numpy as np

client = anthropic.Anthropic()

def get_embedding(text: str) -> List[float]:
    """Get text embedding using OpenAI (or any embedding provider)"""
    # Using Voyage AI (Anthropic's recommended embedding partner)
    import voyageai
    vo = voyageai.Client()
    result = vo.embed([text], model="voyage-3")
    return result.embeddings[0]

def cosine_similarity(a: List[float], b: List[float]) -> float:
    a_arr, b_arr = np.array(a), np.array(b)
    return np.dot(a_arr, b_arr) / (np.linalg.norm(a_arr) * np.linalg.norm(b_arr))

class SimpleRAG:
    def __init__(self):
        self.documents = []
        self.embeddings = []
    
    def add_document(self, text: str, metadata: dict = None):
        embedding = get_embedding(text)
        self.documents.append({"text": text, "metadata": metadata or {}})
        self.embeddings.append(embedding)
    
    def search(self, query: str, top_k: int = 3) -> List[dict]:
        query_embedding = get_embedding(query)
        similarities = [
            cosine_similarity(query_embedding, emb) 
            for emb in self.embeddings
        ]
        top_indices = np.argsort(similarities)[-top_k:][::-1]
        return [self.documents[i] for i in top_indices]
    
    def answer(self, question: str) -> str:
        relevant_docs = self.search(question)
        context = "\n\n".join([doc["text"] for doc in relevant_docs])
        
        response = client.messages.create(
            model="claude-sonnet-4-6",
            max_tokens=1024,
            system="""Answer the question using ONLY the provided context. 
                     If the answer isn't in the context, say so clearly.""",
            messages=[{
                "role": "user",
                "content": f"Context:\n{context}\n\nQuestion: {question}"
            }]
        )
        return response.content[0].text
```

---

## Building a FastAPI Backend

```python
# main.py
from fastapi import FastAPI, HTTPException
from fastapi.responses import StreamingResponse
from pydantic import BaseModel
import anthropic
import json

app = FastAPI()
client = anthropic.Anthropic()

class ChatRequest(BaseModel):
    message: str
    history: list[dict] = []
    system: str = "You are a helpful assistant."

@app.post("/chat")
async def chat(request: ChatRequest):
    messages = request.history + [{"role": "user", "content": request.message}]
    
    response = client.messages.create(
        model="claude-sonnet-4-6",
        max_tokens=2048,
        system=request.system,
        messages=messages
    )
    
    return {
        "response": response.content[0].text,
        "usage": {
            "input_tokens": response.usage.input_tokens,
            "output_tokens": response.usage.output_tokens
        }
    }

@app.post("/chat/stream")
async def chat_stream(request: ChatRequest):
    messages = request.history + [{"role": "user", "content": request.message}]
    
    def generate():
        with client.messages.stream(
            model="claude-sonnet-4-6",
            max_tokens=2048,
            system=request.system,
            messages=messages
        ) as stream:
            for text in stream.text_stream:
                yield f"data: {json.dumps({'text': text})}\n\n"
        yield "data: [DONE]\n\n"
    
    return StreamingResponse(generate(), media_type="text/event-stream")

# Run: uvicorn main:app --reload
```

---

## Frontend Integration (React/Next.js)

```typescript
// hooks/useChat.ts
import { useState, useCallback } from 'react'

interface Message {
  role: 'user' | 'assistant'
  content: string
}

export function useChat() {
  const [messages, setMessages] = useState<Message[]>([])
  const [isLoading, setIsLoading] = useState(false)

  const sendMessage = useCallback(async (userMessage: string) => {
    const newMessages = [...messages, { role: 'user' as const, content: userMessage }]
    setMessages(newMessages)
    setIsLoading(true)

    try {
      const response = await fetch('/api/chat', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ 
          message: userMessage,
          history: messages 
        })
      })

      const data = await response.json()
      setMessages([...newMessages, { role: 'assistant', content: data.response }])
    } finally {
      setIsLoading(false)
    }
  }, [messages])

  return { messages, sendMessage, isLoading }
}
```

---

## Deployment Options

### Vercel (Recommended for web apps)

```bash
npm install -g vercel
vercel --prod
```

Add `ANTHROPIC_API_KEY` to Vercel environment variables.

### Railway (Full-stack)

```bash
railway init
railway up
```

### Docker

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

---

## Cost Optimization

### Use Prompt Caching (Anthropic)

Cache your system prompts to reduce costs on repeated calls:

```python
response = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    system=[{
        "type": "text",
        "text": "Your long system prompt here...",
        "cache_control": {"type": "ephemeral"}  # Cache this!
    }],
    messages=messages
)
```

**Savings:** 90% cost reduction on cached tokens.

### Model Selection Strategy

```python
def select_model(task_complexity: str) -> str:
    models = {
        "simple": "claude-haiku-4-5",        # Fast, cheap — classification, extraction
        "medium": "claude-sonnet-4-6",        # Balanced — most tasks
        "complex": "claude-opus-4-7"          # Best quality — complex reasoning
    }
    return models.get(task_complexity, "claude-sonnet-4-6")
```

---

*Last updated: April 2025 · [Back to main README](../README.md) · by [CodeBeez Innovation](https://codebeez.xyz) & [Abid Redwan](https://aredwan.com)*
