# Datasets & Benchmarks

A comprehensive guide to the data that trains, tests, and measures AI systems.

---

## Pre-Training Datasets

### Text & Language

| Dataset | Size | Language | License | Source |
|---------|------|----------|---------|--------|
| [Common Crawl](https://commoncrawl.org) | Petabytes | Multi | Open | Web crawl |
| [The Pile](https://pile.eleuther.ai) | 800GB | English | MIT | EleutherAI |
| [Dolma](https://huggingface.co/datasets/allenai/dolma) | 3T tokens | English | ODC-BY | AI2 |
| [FineWeb](https://huggingface.co/datasets/HuggingFaceFW/fineweb) | 15T tokens | English | ODC-BY | HuggingFace |
| [ROOTS](https://huggingface.co/bigscience/roots) | 1.6TB | 46 lang | Various | BigScience |
| [RedPajama v2](https://huggingface.co/datasets/togethercomputer/RedPajama-Data-V2) | 30T tokens | Multi | Apache 2.0 | Together AI |
| [C4](https://huggingface.co/datasets/allenai/c4) | 750GB | English | ODC-BY | Google/AI2 |
| [OpenWebText2](https://openwebtext2.readthedocs.io) | 65GB | English | Public domain | EleutherAI |

### Code Datasets

| Dataset | Size | Languages | License |
|---------|------|-----------|---------|
| [The Stack v2](https://huggingface.co/datasets/bigcode/the-stack-v2) | 900B tokens | 619 langs | Various |
| [CodeSearchNet](https://github.com/github/CodeSearchNet) | 6M functions | 6 langs | MIT |
| [GitHub Code](https://huggingface.co/datasets/codeparrot/github-code) | 1TB | Multi | Mixed |
| [MBPP](https://huggingface.co/datasets/google-research-datasets/mbpp) | 974 problems | Python | CC-BY-4.0 |

### Instruction & Alignment Datasets

| Dataset | Size | Type | License |
|---------|------|------|---------|
| [OpenHermes 2.5](https://huggingface.co/datasets/teknium/OpenHermes-2.5) | 1M | Chat | Apache 2.0 |
| [UltraChat](https://huggingface.co/datasets/stingning/ultrachat) | 1.5M | Chat | CC-BY-NC |
| [ShareGPT90K](https://huggingface.co/datasets/anon8231489123/ShareGPT_Vicuna_unfiltered) | 90K | Multi-turn | Unknown |
| [Alpaca](https://github.com/tatsu-lab/stanford_alpaca) | 52K | Instructions | CC-BY-NC |
| [Orca](https://huggingface.co/datasets/Open-Orca/OpenOrca) | 4M | Reasoning | MIT |
| [WizardLM Evol-Instruct](https://huggingface.co/datasets/WizardLM/WizardLM_evol_instruct_V2_196k) | 196K | Complex | Unknown |

---

## Benchmarks

### Language Understanding

| Benchmark | Tasks | Difficulty | Papers |
|-----------|-------|-----------|--------|
| **MMLU** | 57 subjects, 14K questions | High school–PhD | [Paper](https://arxiv.org/abs/2009.03300) |
| **BIG-Bench** | 200+ diverse tasks | Variable | [Paper](https://arxiv.org/abs/2206.04615) |
| **BIG-Bench Hard** | 23 hardest BIG-Bench | Hard | [Paper](https://arxiv.org/abs/2210.09261) |
| **HellaSwag** | Commonsense NLI | Medium | [Paper](https://arxiv.org/abs/1905.07830) |
| **WinoGrande** | Pronoun resolution | Medium | [Paper](https://arxiv.org/abs/1907.10641) |
| **ARC (Easy/Challenge)** | Science QA | Easy–Hard | [Paper](https://arxiv.org/abs/1803.05457) |

### Reasoning & Math

| Benchmark | Domain | Difficulty | Current SOTA |
|-----------|--------|-----------|-------------|
| **GSM8K** | Grade school math | Easy | ~97% |
| **MATH** | Competition math | Hard | ~90% |
| **GPQA** | Graduate-level QA | Very Hard | ~75% |
| **AIME** | Top math olympiad | Expert | ~60% |
| **FrontierMath** | Research-level math | Expert | ~5-10% |

### Coding

| Benchmark | Tasks | Language | Notes |
|-----------|-------|----------|-------|
| **HumanEval** | 164 functions | Python | Pass@1 |
| **MBPP** | 500 problems | Python | Pass@1 |
| **SWE-bench** | Real GitHub issues | Multi | Hard engineering |
| **SWE-bench Verified** | 500 verified issues | Multi | Curated subset |
| **LiveCodeBench** | Live coding contest | Multi | Contamination-free |

### Long Context

| Benchmark | Context Length | Tasks |
|-----------|---------------|-------|
| **RULER** | 4K–128K | Retrieval, tracking |
| **HELMET** | Various | Diverse long-context |
| **Needle-in-Haystack** | 100K+ | Single fact retrieval |
| **SCROLLS** | Documents | Summarization, QA |

### Multimodal

| Benchmark | Modalities | Tasks |
|-----------|-----------|-------|
| **MMBench** | Image + Text | Perception, reasoning |
| **MMMU** | Multi-discipline images | University-level QA |
| **VQAv2** | Image + Text | Visual QA |
| **DocVQA** | Documents | Document understanding |
| **ChartQA** | Charts | Chart understanding |
| **TextVQA** | Images with text | OCR + reasoning |

### Safety & Alignment

| Benchmark | Tests | Purpose |
|-----------|-------|---------|
| **TruthfulQA** | 817 Q | Truthfulness vs memorized falsehoods |
| **BBQ** | Ambiguous QA | Bias measurement |
| **WinoBias** | Gender bias | Coreference resolution bias |
| **HarmBench** | Harm categories | Safety evaluation |

---

## Vision & Multimodal Datasets

### Image Classification

| Dataset | Images | Classes | License |
|---------|--------|---------|---------|
| ImageNet-1K | 1.2M | 1,000 | Research |
| ImageNet-21K | 14M | 21,841 | Research |
| CIFAR-10/100 | 60K | 10/100 | MIT |
| Places365 | 1.8M | 365 | Research |

### Image-Text Pairs (For Foundation Models)

| Dataset | Pairs | License |
|---------|-------|---------|
| [LAION-5B](https://laion.ai/blog/laion-5b/) | 5.85B | CC-BY |
| [DataComp-1B](https://www.datacomp.ai) | 1.28B | CC-BY |
| [CC3M](https://ai.google.com/research/ConceptualCaptions/) | 3.3M | Research |
| [COCO Captions](https://cocodataset.org) | 330K | CC-BY |

### Object Detection

| Dataset | Images | Objects | Tasks |
|---------|--------|---------|-------|
| COCO | 330K | 1.5M | Detection, segmentation |
| Objects365 | 600K | 10M+ | Detection |
| Open Images v7 | 9M | 16M | Detection, relationships |

---

## How to Use Datasets

### Loading with Hugging Face

```python
from datasets import load_dataset

# Classification
dataset = load_dataset("glue", "sst2")

# Math
dataset = load_dataset("gsm8k", "main")

# Custom splits
train = dataset["train"]
test = dataset["test"]

# Stream large datasets
dataset = load_dataset("HuggingFaceFW/fineweb", streaming=True)
for example in dataset["train"]:
    print(example["text"][:100])
    break
```

### Evaluating a Model

```python
import anthropic
from datasets import load_dataset

client = anthropic.Anthropic()

def evaluate_gsm8k(num_samples: int = 100) -> float:
    dataset = load_dataset("gsm8k", "main", split=f"test[:{num_samples}]")
    correct = 0
    
    for example in dataset:
        response = client.messages.create(
            model="claude-haiku-4-5",
            max_tokens=512,
            messages=[{
                "role": "user",
                "content": f"Solve this math problem step by step. End with 'Answer: X' where X is the number.\n\n{example['question']}"
            }]
        )
        
        predicted = response.content[0].text.split("Answer: ")[-1].strip()
        actual = example["answer"].split("####")[-1].strip()
        
        if predicted == actual:
            correct += 1
    
    return correct / num_samples

accuracy = evaluate_gsm8k(100)
print(f"GSM8K accuracy: {accuracy:.1%}")
```

---

## Benchmark Leaderboards

- **[LMSYS Chatbot Arena](https://chat.lmsys.org)** — Human preference ranking (most trusted)
- **[Open LLM Leaderboard](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard)** — Open models
- **[Papers With Code SOTA](https://paperswithcode.com/sota)** — Task-specific rankings
- **[BIG-Code Models Leaderboard](https://huggingface.co/spaces/bigcode/bigcode-models-leaderboard)** — Coding models
- **[LiveBench](https://livebench.ai)** — Contamination-free dynamic benchmark

---

*Last updated: April 2025 · [Back to main README](../../README.md)*
