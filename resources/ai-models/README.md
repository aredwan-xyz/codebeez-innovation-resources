# AI Models — Complete Reference Guide

A comprehensive comparison of foundation models, their capabilities, use cases, and how to choose between them.

---

## How to Choose a Model

```
Is speed critical?          → Groq + Llama, Claude Haiku, Gemini Flash
Is cost critical?           → Haiku, Gemini Flash, Mistral 7B local
Do you need long context?   → Gemini 2.5 Pro (1M), Claude (200K)
Do you need best quality?   → Claude Opus, GPT-4o, Gemini 2.5 Pro
Do you need open weights?   → Llama 3.3, Mistral, Qwen 2.5
Is it a coding task?        → Claude Sonnet, GPT-4o, DeepSeek-Coder
Is it a reasoning task?     → Claude + thinking, o3, DeepSeek-R2
Do you need image gen?      → Flux.1, Midjourney, DALL-E 3
Do you need video?          → Sora, Runway Gen-3, Kling
```

---

## Frontier Model Comparison (2025)

| Model | Context | Coding | Reasoning | Speed | Price/1M in | Price/1M out |
|-------|---------|--------|-----------|-------|------------|-------------|
| Claude Opus 4.7 | 200K | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Medium | $15 | $75 |
| Claude Sonnet 4.6 | 200K | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Fast | $3 | $15 |
| Claude Haiku 4.5 | 200K | ⭐⭐⭐⭐ | ⭐⭐⭐ | Very Fast | $0.25 | $1.25 |
| GPT-4o | 128K | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Fast | $2.5 | $10 |
| GPT-o3 | 128K | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Slow | $10 | $40 |
| Gemini 2.5 Pro | 1M | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Medium | $1.25 | $10 |
| Gemini 2.0 Flash | 1M | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Very Fast | $0.10 | $0.40 |
| DeepSeek-R2 | 128K | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Medium | $0.55 | $2.19 |

*Prices approximate as of April 2025. Check provider websites for current pricing.*

---

## Open Source Models

### Llama Family (Meta)

| Model | Params | Context | Best For |
|-------|--------|---------|----------|
| Llama 3.3 70B | 70B | 128K | General purpose, near-frontier quality |
| Llama 3.2 11B Vision | 11B | 128K | Vision tasks, efficient |
| Llama 3.2 3B | 3B | 128K | Edge devices, fast inference |
| Llama 3.1 8B | 8B | 128K | Efficient general tasks |

**License:** Custom Meta Llama License (allows commercial use up to 700M users)

### Mistral Family

| Model | Params | Context | Best For |
|-------|--------|---------|----------|
| Mistral 7B | 7B | 32K | Efficient, punches above weight |
| Mixtral 8x7B | 8×7B MoE | 32K | Code, multilingual |
| Mixtral 8x22B | 8×22B MoE | 64K | Near-frontier open model |
| Mistral Large | 123B | 128K | Frontier, API only |
| Codestral | 22B | 32K | Code generation |

**License:** Apache 2.0 (open weights)

### Qwen Family (Alibaba)

| Model | Params | Context | Best For |
|-------|--------|---------|----------|
| Qwen 2.5 72B | 72B | 128K | Best open 72B model |
| Qwen 2.5 Coder 32B | 32B | 128K | Code, competitive with GPT-4 |
| QwQ-32B | 32B | 128K | Reasoning, Chain-of-thought |
| Qwen-VL | Multi | 32K | Vision-language |

**License:** Apache 2.0

### DeepSeek Family

| Model | Params | Context | Best For |
|-------|--------|---------|----------|
| DeepSeek-R2 | 671B MoE | 128K | Reasoning, math, frontier-level |
| DeepSeek-V3 | 685B MoE | 128K | General, coding |
| DeepSeek-Coder-V2 | 236B MoE | 128K | Code generation |

**License:** MIT

---

## Embedding Models

Embeddings convert text into vectors for semantic search and RAG.

| Model | Dims | Max Tokens | Provider | Notes |
|-------|------|-----------|----------|-------|
| text-embedding-3-large | 3072 | 8192 | OpenAI | Best quality |
| text-embedding-3-small | 1536 | 8192 | OpenAI | Balanced |
| voyage-3 | 1024 | 32000 | Voyage AI | Best for Claude RAG |
| BGE-M3 | 1024 | 8192 | BAAI | Best open multilingual |
| E5-Mistral-7B | 4096 | 32768 | Microsoft | High quality open |
| Nomic-Embed-Text | 768 | 8192 | Nomic | Fast, open |

---

## Multimodal Models

### Vision-Language Models

| Model | Input | Output | Best For |
|-------|-------|--------|----------|
| GPT-4o | Text + Images | Text | Complex visual reasoning |
| Claude Vision | Text + Images | Text | Document analysis, charts |
| Gemini 2.5 Pro | Text + Images + Video | Text | Long visual content |
| LLaVA-1.6 | Text + Images | Text | Open source alternative |
| PaliGemma 2 | Text + Images | Text | Efficient open-source |
| InternVL2 | Text + Images | Text | Strong open-source VLM |

### Image Generation

| Model | Type | Quality | Speed | License |
|-------|------|---------|-------|---------|
| Flux.1 Pro | Diffusion | ⭐⭐⭐⭐⭐ | Fast | Commercial |
| Flux.1 Dev | Diffusion | ⭐⭐⭐⭐⭐ | Fast | Non-commercial |
| Flux.1 Schnell | Diffusion | ⭐⭐⭐⭐ | Very Fast | Apache 2.0 |
| DALL-E 3 | Diffusion | ⭐⭐⭐⭐⭐ | Medium | API only |
| Midjourney v6 | Diffusion | ⭐⭐⭐⭐⭐ | Medium | Subscription |
| SD3 Medium | Diffusion | ⭐⭐⭐⭐ | Fast | Stability AI |

---

## Model Selection for Common Tasks

### Customer Support Bot

```
System Prompt: Detailed product knowledge base
Model: Claude Haiku (speed + cost) or Gemini Flash
RAG: Yes — product docs, FAQs
Tools: Ticket creation, order lookup
```

### Code Review Tool

```
Model: Claude Sonnet 4.6 or GPT-4o
Context: 200K (for large files)
System: Expert code reviewer persona
Output: Structured JSON with issues
```

### Document Q&A

```
Architecture: RAG
Embedding: voyage-3 or text-embedding-3-large
Vector DB: Pinecone, Qdrant, or pgvector
Model: Claude Sonnet (good at following instructions)
```

### Creative Writing

```
Model: Claude Opus (richest language)
Temperature: 0.8-1.0
System: Detailed writing style guide
```

### Data Extraction

```
Model: Claude Haiku or GPT-4o-mini
Output: JSON mode
Temperature: 0.0 (deterministic)
Few-shot: 2-3 examples
```

---

*Last updated: April 2025 · [Back to main README](../../README.md) · by [CodeBeez Innovation](https://codebeez.xyz) & [Abid Redwan](https://aredwan.com)*
