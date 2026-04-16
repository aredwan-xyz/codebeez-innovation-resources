# Prompt Engineering Mastery

A comprehensive, practical guide to writing prompts that actually work.

---

## The Mental Model

Think of prompting like **hiring a brilliant but literal employee on their first day**. They're incredibly capable but need:
- Clear context about what you want
- Examples of what "good" looks like
- Constraints on what to avoid
- Format for the output

The better you communicate the task, the better the result.

---

## Foundational Techniques

### 1. Zero-Shot Prompting

Directly asking without examples.

```
Classify the sentiment of this review as positive, negative, or neutral:
"The product arrived on time but the quality was disappointing."
```

**Best for:** Simple, well-defined tasks the model already understands well.

---

### 2. Few-Shot Prompting

Providing examples before your actual request.

```
Classify the sentiment:

Review: "Amazing product, exceeded expectations!" → positive
Review: "It broke after one day." → negative
Review: "Arrived as described." → neutral

Review: "The battery life could be better but overall I'm satisfied." → ?
```

**Best for:** Tasks requiring specific formatting, classification with custom categories, or domain-specific judgment.

---

### 3. Chain-of-Thought (CoT)

Ask the model to reason step-by-step before answering.

```
Q: A store buys items for $15 each and sells them for $25. They sold 
40 items. What's their profit?

Think through this step by step before giving the final answer.
```

**Output with CoT:**
```
Step 1: Revenue = 40 items × $25 = $1,000
Step 2: Cost = 40 items × $15 = $600  
Step 3: Profit = $1,000 - $600 = $400

The profit is $400.
```

**Best for:** Math, logic, multi-step reasoning, complex analysis.

---

### 4. System Prompts

Set the context, persona, and constraints before the conversation begins.

```
System: You are an expert Python code reviewer at a senior engineering level.
When reviewing code, you:
- First summarize what the code does in 1-2 sentences
- Identify bugs and security vulnerabilities (critical issues)
- Suggest performance improvements (optional improvements)
- Provide specific, actionable feedback with code examples
- Format your response with clear sections

Never rewrite the entire code. Only suggest targeted improvements.
```

**Best for:** Building applications, setting personas, enforcing output formats.

---

### 5. Structured Output

Force specific formats (JSON, XML, Markdown, etc.).

```
Extract the key information from this job posting and return it as JSON.

Job posting: [TEXT]

Return this exact structure:
{
  "title": "string",
  "company": "string",
  "location": "string",
  "salary_range": "string or null",
  "required_skills": ["string"],
  "experience_years": "number or null",
  "remote": "boolean"
}

Return only valid JSON. No explanation or markdown code blocks.
```

---

### 6. Role / Persona Prompting

Give the model a specific expert identity.

```
You are a McKinsey senior partner with 20 years of strategy consulting experience.
A client's SaaS startup is growing revenue at 40% YoY but burning cash at $500K/month.
They have 14 months of runway. What are the 3 highest-leverage actions they should take?
Respond with the brevity and directness of a senior consultant in a client meeting.
```

---

### 7. Constraint Prompting

Explicitly define what NOT to do.

```
Summarize this article in exactly 3 bullet points.
- Each bullet must be under 20 words
- Do not use the word "however" or "additionally"
- Focus only on actionable insights, not background information

Article: [TEXT]
```

---

### 8. Self-Consistency

Generate multiple responses and take the majority.

```python
import anthropic
from collections import Counter

client = anthropic.Anthropic()

def self_consistent_answer(question: str, samples: int = 5) -> str:
    answers = []
    for _ in range(samples):
        response = client.messages.create(
            model="claude-sonnet-4-6",
            max_tokens=200,
            messages=[{
                "role": "user",
                "content": f"{question}\n\nProvide only the final answer, no explanation."
            }]
        )
        answers.append(response.content[0].text.strip())
    
    # Return most common answer
    return Counter(answers).most_common(1)[0][0]
```

**Best for:** High-stakes decisions, factual questions where consistency matters.

---

## Advanced Techniques

### ReAct (Reason + Act)

Interleave reasoning and tool use.

```
You have access to these tools:
- search(query) — search the web
- calculator(expression) — evaluate math
- get_current_date() — get today's date

To use a tool, write: TOOL: tool_name(argument)
After getting a result, reason about it, then either use another tool or provide a final answer.

Question: What is the GDP per capita of the country that won the most recent FIFA World Cup?
```

---

### Tree of Thoughts

Explore multiple reasoning paths before choosing.

```
I need to solve: [PROBLEM]

Generate 3 different approaches to solving this problem.
For each approach:
1. Describe the strategy
2. Identify potential failure points
3. Rate confidence (1-10)

Then select the best approach and execute it fully.
```

---

### Retrieval-Augmented Generation (RAG)

Ground responses in external knowledge.

```
Answer the user's question using ONLY the information provided in the context below.
If the answer is not in the context, say "I don't have information about that."
Do not use your training knowledge.

CONTEXT:
[Retrieved documents go here]

QUESTION: [User's question]
```

---

### Constitutional AI / Self-Critique

Have the model check its own output.

```
Step 1: Answer this question: [QUESTION]

Step 2: Review your answer against these criteria:
- Is it factually accurate?
- Is it helpful and actionable?
- Does it avoid harmful content?
- Is it appropriately uncertain where needed?

Step 3: Revise your answer based on your self-review.
Output only the final revised answer.
```

---

## Prompt Templates Library

### Template: Technical Documentation

```
You are a technical writer creating documentation for developers.

Write documentation for the following function/API/component:
[CODE OR DESCRIPTION]

Include:
1. Overview (1-2 sentences)
2. Parameters table (name | type | required | description)
3. Return value
4. Example usage (with code)
5. Common errors / edge cases

Format as Markdown. Be precise and concise.
```

### Template: Code Review

```
Review the following [LANGUAGE] code as a senior engineer.

Code:
```[LANGUAGE]
[CODE]
```

Structure your review as:
## Summary
One-sentence description of what this code does.

## Critical Issues
Bugs, security vulnerabilities, or logic errors that MUST be fixed.

## Suggestions
Optional improvements for performance, readability, or maintainability.

## Verdict
[APPROVE / REQUEST CHANGES] — one sentence rationale.
```

### Template: Content Strategy

```
You are a content strategist helping a [COMPANY TYPE] grow their audience.

Context:
- Audience: [TARGET AUDIENCE]
- Platform: [PLATFORM]
- Goal: [AWARENESS / ENGAGEMENT / CONVERSION]
- Tone: [PROFESSIONAL / CASUAL / TECHNICAL]

Generate 10 content ideas for the next month.
For each idea include:
- Title/hook
- Content format (thread, article, video, etc.)
- Key message
- Call to action

Rank by estimated engagement potential.
```

### Template: Decision Analysis

```
Help me think through this decision systematically.

Decision: [YOUR DECISION]
Context: [RELEVANT BACKGROUND]

Analyze using:
1. **Pros and Cons** — List 5 of each
2. **Second-order effects** — What happens after the immediate result?
3. **Reversibility** — How easy is it to undo if wrong?
4. **Key assumptions** — What must be true for each option to work?
5. **Recommendation** — Given the above, what would you choose and why?

Be direct. I want analysis, not hedging.
```

---

## Common Mistakes & Fixes

| Mistake | Problem | Fix |
|---------|---------|-----|
| Too vague | "Write something about AI" | "Write a 200-word LinkedIn post about how AI is changing product management, targeting mid-level PMs" |
| No format specified | Long prose when you wanted bullets | Add "Format your response as a bulleted list" |
| No context | Model makes wrong assumptions | Add relevant background before the task |
| No constraints | Responses too long/short | Specify length ("in 3 sentences", "under 100 words") |
| Ambiguous pronouns | "Make it better" — better how? | Be specific: "Make it more concise and direct" |
| Missing examples | Generic output | Add 1-2 examples of what "good" looks like |

---

## Evaluation Framework

How to know if your prompt is good:

```
1. Clarity:     Would a human new to this task understand what's needed?
2. Completeness: Are all necessary constraints and context included?
3. Specificity: Are vague terms replaced with precise ones?
4. Examples:    For complex tasks, is there at least one example?
5. Format:      Is the desired output format explicit?
```

Run your prompt through 3-5 test cases. If more than 1 fails, revise.

---

## Model-Specific Tips

### Claude (Anthropic)

- Responds well to explicit XML tags for structure: `<task>`, `<context>`, `<output_format>`
- Excellent for long-context tasks (200K tokens)
- Use "Think step by step" or enable extended thinking for hard problems
- Constitutional prompting works well — state what you want AND what you want to avoid

### GPT-4o (OpenAI)

- JSON mode (`response_format: {"type": "json_object"}`) for reliable structured output
- Tool/function calling is very capable
- System prompt is strongly respected

### Gemini (Google)

- Handles ultra-long context well (1M tokens)
- Strong with multimodal inputs
- Good for data analysis tasks

---

*Last updated: April 2025 · [Back to main README](../README.md) · by [CodeBeez Innovation](https://codebeez.xyz) & [Abid Redwan](https://aredwan.com)*
