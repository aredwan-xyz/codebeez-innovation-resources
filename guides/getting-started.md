# Getting Started with AI — Zero to Productive in 30 Days

A practical, no-fluff roadmap for anyone who wants to go from "curious about AI" to "actually building things with AI."

---

## Who Is This For?

- Developers wanting to integrate AI into their work
- Students starting their AI/ML journey
- Product people wanting to understand AI capabilities
- Curious professionals exploring the AI landscape

---

## Week 1: Foundations & Orientation

### Day 1–2: Understand the Landscape

**Goal:** Know what's out there and why it matters.

1. Read [The State of AI — 2025 Overview](https://aiindex.stanford.edu) (Stanford AI Index)
2. Watch [3Blue1Brown's Neural Networks series](https://youtube.com/@3blue1brown) (4 videos, ~1 hour total)
3. Try [Claude](https://claude.ai), [ChatGPT](https://chatgpt.com), and [Gemini](https://gemini.google.com) for the same task — compare outputs

**Key questions to answer for yourself:**
- What is a language model?
- What is the difference between AI, ML, and deep learning?
- What can't AI do yet?

### Day 3–4: First Hands-On Experience

**Goal:** Get comfortable using AI tools directly.

1. Sign up for [Anthropic Console](https://console.anthropic.com) — free tier available
2. Read [Anthropic's Intro to Claude](https://docs.anthropic.com)
3. Complete [Learn Prompting](https://learnprompting.org) — Module 1 (free, 30 min)

**Try these prompts:**
```
"Explain [topic you know well] as if you're teaching it to a 12-year-old"
"Review this code and find potential bugs: [paste your code]"
"Help me write a professional email declining a meeting request"
```

### Day 5–7: Core Concepts

**Goal:** Build a mental model of how AI works.

1. Watch [Andrej Karpathy: Intro to Large Language Models](https://youtube.com/watch?v=zjkBMFhNj_g) (1 hour)
2. Read [How GPT Works](https://jaykmody.com/blog/gpt-from-scratch/) — if you're technical
3. Read [Co-Intelligence by Ethan Mollick](https://www.goodreads.com/book/show/198678736) — if you're less technical

---

## Week 2: Prompt Engineering

### Day 8–10: Prompting Fundamentals

**Goal:** Learn to communicate effectively with AI.

1. Complete [Prompt Engineering for Developers](https://deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/) (free, 2 hours)
2. Read [Anthropic's Prompt Engineering Guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
3. Read [Prompting Guide](https://promptingguide.ai)

**Core techniques to master:**
- Zero-shot and few-shot prompting
- Chain-of-thought prompting
- Role/persona prompting
- System prompt design

### Day 11–14: Advanced Prompting

**Goal:** Level up your prompt craft.

**Practice exercises:**
1. Write a system prompt for a customer support chatbot
2. Build a few-shot classifier for sentiment analysis
3. Use chain-of-thought for a math problem step-by-step
4. Create a structured output prompt that returns JSON

```markdown
## Template: Structured Output Prompt

You are a data extraction assistant. Extract the following information from the text and return it as valid JSON:

Required fields:
- name (string)
- date (ISO 8601 format)  
- amount (number)
- category (one of: food, transport, entertainment, utilities, other)

Text: [INPUT]

Return only valid JSON, no explanation.
```

---

## Week 3: Building with AI

### Day 15–17: Your First AI App

**Goal:** Ship something real.

**Option A (No-code):** Build a custom GPT or Claude Project
- Define a specific use case
- Write a detailed system prompt
- Test with real scenarios

**Option B (Low-code):** Use [Zapier AI](https://zapier.com) or [Make](https://make.com) to automate a workflow with AI

**Option C (Code):** Build a simple Python app with the Anthropic SDK

```python
import anthropic

client = anthropic.Anthropic()

def ask_claude(prompt: str, system: str = "You are a helpful assistant.") -> str:
    message = client.messages.create(
        model="claude-sonnet-4-6",
        max_tokens=1024,
        system=system,
        messages=[{"role": "user", "content": prompt}]
    )
    return message.content[0].text

# Try it
response = ask_claude("What are 3 innovative uses of AI in education?")
print(response)
```

### Day 18–21: Explore Specialized Tools

**Based on your goals, pick ONE area:**

| If you're a... | Focus on... | Tools to try |
|----------------|-------------|-------------|
| Developer | AI coding tools | GitHub Copilot, Cursor, Claude Code |
| Designer | AI design tools | Midjourney, Figma AI, Galileo |
| Writer | AI writing tools | Claude, Notion AI, Sudowrite |
| Researcher | AI research tools | Perplexity, Elicit, Semantic Scholar |
| Data person | ML/analytics AI | Google Colab + Gemini, DataBricks |

---

## Week 4: Go Deeper

### Day 22–25: Pick Your Specialization

**Track A: AI Engineer / Builder**
1. Complete [Full Stack LLM Bootcamp](https://fullstackdeeplearning.com/llm-bootcamp/)
2. Build a RAG system with [LlamaIndex](https://llamaindex.ai) or [LangChain](https://langchain.com)
3. Explore [vector databases](../resources/tools/README.md)

**Track B: AI Researcher**
1. Read [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
2. Complete [fast.ai Practical Deep Learning](https://course.fast.ai)
3. Start reading [Papers With Code](https://paperswithcode.com) weekly

**Track C: AI Product / Strategy**
1. Read [Co-Intelligence](https://www.goodreads.com/book/show/198678736) by Ethan Mollick
2. Follow [The Batch newsletter](https://deeplearning.ai/the-batch/)
3. Map AI opportunities in your current work/industry

### Day 26–28: Build Your Network

1. Join [Hugging Face Discord](https://huggingface.co/join/discord)
2. Follow key AI researchers on Twitter/X
3. Contribute to this repo by adding a resource you found valuable

### Day 29–30: Ship Something & Share

**Your 30-day project:** Build ONE thing that uses AI to solve a real problem you have.

Examples:
- A script that summarizes your emails
- A tool that reviews your writing
- A bot that answers questions about your codebase
- A workflow that generates social media content

**Share it:** Post on LinkedIn, tweet about it, or open-source it on GitHub.

---

## Resources Referenced

- [Anthropic Documentation](https://docs.anthropic.com)
- [Andrej Karpathy YouTube](https://youtube.com/@AndrejKarpathy)
- [3Blue1Brown Neural Networks](https://www.3blue1brown.com/topics/neural-networks)
- [Learn Prompting](https://learnprompting.org)
- [fast.ai](https://fast.ai)
- [Full Stack LLM Bootcamp](https://fullstackdeeplearning.com)
- [Papers With Code](https://paperswithcode.com)

---

*Last updated: April 2025 · [Back to main README](../README.md)*
