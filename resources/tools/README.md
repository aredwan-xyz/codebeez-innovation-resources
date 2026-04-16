# AI Tools Directory

Every tool you need to build, research, and deploy AI — organized by category.

---

## Quick Reference by Task

| I want to... | Best Tool |
|-------------|-----------|
| Run LLMs locally | Ollama |
| Fine-tune a model | Unsloth + LLaMA Factory |
| Build a RAG app | LlamaIndex or LangChain |
| Deploy an AI API | FastAPI + Modal or Railway |
| Experiment with prompts | Anthropic Workbench |
| Track ML experiments | Weights & Biases |
| Store vectors | Qdrant (self-hosted) or Pinecone (managed) |
| Generate images | Flux.1 Dev (local) or Midjourney (quality) |
| Monitor LLM apps | LangSmith or Helicone |
| Scrape web for AI | Firecrawl or Jina Reader |
| Convert documents to text | Unstructured.io |

---

## Development Frameworks

### LLM Orchestration

- **[LangChain](https://langchain.com)** `Python/JS` — Industry standard for chains, agents, RAG
- **[LlamaIndex](https://llamaindex.ai)** `Python/TS` — Best for data ingestion and RAG systems
- **[DSPy](https://dspy.ai)** `Python` — Programming (not prompting) foundation models
- **[Haystack](https://haystack.deepset.ai)** `Python` — Production NLP pipelines
- **[Semantic Kernel](https://github.com/microsoft/semantic-kernel)** `.NET/Python/Java` — Microsoft's AI SDK
- **[Pydantic AI](https://ai.pydantic.dev)** `Python` — Type-safe, validation-first AI apps
- **[Instructor](https://github.com/jxnl/instructor)** `Python` — Structured outputs with LLMs

### Agent Frameworks

- **[LangGraph](https://langchain-ai.github.io/langgraph/)** — Stateful multi-actor workflows
- **[AutoGen](https://microsoft.github.io/autogen/)** — Multi-agent conversation (Microsoft)
- **[CrewAI](https://crewai.com)** — Orchestrate role-playing agents
- **[OpenHands](https://github.com/All-Hands-AI/OpenHands)** — Open-source software dev agents
- **[AgentKit](https://github.com/coinbase/agentkit)** — Agents with crypto capabilities
- **[Smolagents](https://github.com/huggingface/smolagents)** — Minimal agent framework (HF)

### API Clients & SDKs

```bash
# Python
pip install anthropic openai google-generativeai cohere mistralai

# JavaScript/TypeScript
npm install @anthropic-ai/sdk openai @google/generative-ai
```

---

## Model Hosting & Serving

### Local Inference

| Tool | Interface | Models | GPU Required? |
|------|-----------|--------|--------------|
| **Ollama** | CLI + API | Llama, Mistral, Gemma+ | No (CPU slow) |
| **LM Studio** | GUI + API | Most GGUF models | Recommended |
| **GPT4All** | GUI | Curated selection | No |
| **llama.cpp** | CLI | GGUF format | No |
| **Jan** | GUI | Many open models | Recommended |
| **Koboldcpp** | GUI | GGUF + extras | Recommended |

### Cloud Inference APIs

| Provider | Models | Speed | Free Tier |
|----------|--------|-------|-----------|
| **Groq** | Llama, Gemma, Mixtral | Fastest | Yes |
| **Together AI** | 50+ open models | Fast | $25 credit |
| **Replicate** | 1000+ models | Medium | Pay per use |
| **Fireworks AI** | Open models | Fast | Yes |
| **Perplexity API** | + Search | Medium | No |

### Production Serving

- **[vLLM](https://vllm.ai)** — High-throughput, PagedAttention
- **[TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM)** — NVIDIA optimized
- **[Triton Inference Server](https://developer.nvidia.com/nvidia-triton-inference-server)** — Multi-model serving
- **[BentoML](https://bentoml.com)** — Package and deploy ML models

---

## Vector Databases

| Database | Type | Best For | Free Tier |
|----------|------|----------|-----------|
| **[Pinecone](https://pinecone.io)** | Managed | Production scale | 1 index |
| **[Weaviate](https://weaviate.io)** | Self/Cloud | Hybrid search | Yes |
| **[Qdrant](https://qdrant.tech)** | Self/Cloud | Performance | Yes |
| **[Chroma](https://trychroma.com)** | Self-hosted | Development | Always free |
| **[Milvus](https://milvus.io)** | Self/Cloud | Scale | Yes |
| **[pgvector](https://github.com/pgvector/pgvector)** | Postgres ext | Existing Postgres | Always free |
| **[LanceDB](https://lancedb.github.io/lancedb/)** | Embedded | Serverless | Always free |

---

## Data & Document Processing

### Web Scraping for AI

- **[Firecrawl](https://firecrawl.dev)** — Scrape any URL → clean markdown for LLMs
- **[Jina Reader](https://jina.ai/reader/)** — `r.jina.ai/URL` → markdown instantly
- **[Crawl4AI](https://github.com/unclecode/crawl4ai)** — Open-source LLM-optimized scraper
- **[Playwright](https://playwright.dev)** — Browser automation for dynamic pages

### Document Parsing

- **[Unstructured](https://unstructured.io)** — Parse PDFs, Word, HTML, images to text
- **[LlamaParse](https://llamaindex.ai/llama-parse)** — Advanced PDF parsing for RAG
- **[Docling](https://github.com/DS4SD/docling)** — IBM's document conversion library
- **[PyMuPDF](https://pymupdf.readthedocs.io)** — Fast PDF processing in Python
- **[Marker](https://github.com/VikParuchuri/marker)** — PDF to markdown with high accuracy

### Dataset Tools

- **[Hugging Face Datasets](https://huggingface.co/datasets)** — 150K+ datasets
- **[DataTrove](https://github.com/huggingface/datatrove)** — Large-scale data processing
- **[Argilla](https://argilla.io)** — Data labeling for LLM fine-tuning
- **[Label Studio](https://labelstud.io)** — Open-source annotation platform

---

## Evaluation & Monitoring

### LLM Evaluation

- **[Braintrust](https://braintrust.dev)** — Modern AI eval platform
- **[RAGAS](https://ragas.io)** — RAG evaluation framework
- **[DeepEval](https://deepeval.com)** — LLM evaluation framework
- **[TruLens](https://trulens.org)** — Evaluate + track LLM apps
- **[Evals (OpenAI)](https://github.com/openai/evals)** — Open-source evaluation framework

### Observability & Monitoring

- **[LangSmith](https://smith.langchain.com)** — Trace, debug, monitor LangChain apps
- **[Helicone](https://helicone.ai)** — Open-source LLM observability
- **[Phoenix (Arize)](https://phoenix.arize.com)** — ML observability
- **[Langfuse](https://langfuse.com)** — Open-source LLM observability
- **[Weave (W&B)](https://wandb.ai/site/weave)** — LLM tracing from W&B

---

## Fine-Tuning & Training

### Fine-Tuning Frameworks

| Tool | Speed | VRAM | Best For |
|------|-------|------|----------|
| **[Unsloth](https://unsloth.ai)** | 2x faster | 60% less | Consumer GPUs |
| **[Axolotl](https://axolotl.ai)** | Standard | Standard | Flexible configs |
| **[LLaMA Factory](https://github.com/hiyouga/LLaMA-Factory)** | Standard | Standard | Easy UI + CLI |
| **[TRL (HuggingFace)](https://github.com/huggingface/trl)** | Standard | Standard | RLHF, SFT, DPO |
| **[torchtune](https://pytorch.org/torchtune/)** | PyTorch native | Optimized | Custom training |

### Distributed Training

- **[DeepSpeed](https://www.deepspeed.ai)** — ZeRO optimizer, model parallelism
- **[Accelerate](https://huggingface.co/docs/accelerate)** — HuggingFace distributed training
- **[FSDP](https://pytorch.org/tutorials/intermediate/FSDP_tutorial.html)** — PyTorch Fully Sharded

### Experiment Tracking

- **[Weights & Biases](https://wandb.ai)** — Industry standard experiment tracking
- **[MLflow](https://mlflow.org)** — Open-source ML lifecycle
- **[ClearML](https://clear.ml)** — End-to-end MLOps platform
- **[Comet ML](https://comet.ml)** — Experiment and model management

---

## Creative AI Tools

### Image Generation Interfaces

- **[AUTOMATIC1111](https://github.com/AUTOMATIC1111/stable-diffusion-webui)** — Most feature-rich SD UI
- **[ComfyUI](https://github.com/comfyanonymous/ComfyUI)** — Node-based, most flexible
- **[InvokeAI](https://invoke.ai)** — Professional SD interface
- **[Fooocus](https://github.com/lllyasviel/Fooocus)** — Simplified Midjourney-like UI

### Editing & Manipulation

- **[Inpaint-Anything](https://github.com/geekyutao/Inpaint-Anything)** — Segment + inpaint any object
- **[InstantID](https://github.com/InstantX-Team/InstantID)** — Identity-preserving generation
- **[IP-Adapter](https://github.com/tencent-ailab/IP-Adapter)** — Image prompt adapter

---

## Security & Safety Tools

- **[Guardrails AI](https://guardrailsai.com)** — Validate and correct LLM outputs
- **[NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails)** — NVIDIA's safety rails
- **[Rebuff](https://github.com/protectai/rebuff)** — Prompt injection detector
- **[LLM Guard](https://llm-guard.com)** — Security toolkit for LLM interactions

---

*Last updated: April 2025 · [Back to main README](../../README.md)*
