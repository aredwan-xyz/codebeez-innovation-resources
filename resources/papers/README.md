# AI Research Papers — Navigation Guide

How to find, read, and stay current with AI research without drowning in papers.

---

## The Essential Reading List

### Foundation Papers (Read These First)

These are the papers that created the field as it exists today.

| Year | Paper | Why It Matters |
|------|-------|----------------|
| 1986 | [Learning Representations by Back-propagating Errors](https://www.nature.com/articles/323533a0) | Backprop — how neural nets learn |
| 1989 | [Multilayer Feedforward Networks](https://www.sciencedirect.com/science/article/abs/pii/0893608089900208) | Universal approximation theorem |
| 1997 | [Long Short-Term Memory](https://www.bioinf.jku.at/publications/older/2604.pdf) | LSTMs — first practical RNNs |
| 2012 | [AlexNet — ImageNet Classification with CNNs](https://papers.nips.cc/paper/2012/hash/c399862d3b9d6b76c8436e924a68c45b-Abstract.html) | The "moment" that started deep learning |
| 2014 | [Generative Adversarial Networks](https://arxiv.org/abs/1406.2661) | GANs — generative AI foundation |
| 2017 | [**Attention Is All You Need**](https://arxiv.org/abs/1706.03762) | Transformer — the architecture behind everything |
| 2018 | [**BERT: Pre-training of Deep Bidirectional Transformers**](https://arxiv.org/abs/1810.04805) | First major pre-trained language model |
| 2020 | [**Language Models are Few-Shot Learners (GPT-3)**](https://arxiv.org/abs/2005.14165) | Emergence: scale changes everything |
| 2021 | [**CLIP: Learning Transferable Visual Models**](https://arxiv.org/abs/2103.00020) | Connecting language and vision |
| 2021 | [**DALL-E**](https://arxiv.org/abs/2102.12092) | Text-to-image generation |
| 2022 | [**InstructGPT / RLHF**](https://arxiv.org/abs/2203.02155) | Aligning LLMs with human preferences |
| 2022 | [**Constitutional AI**](https://arxiv.org/abs/2212.08073) | Principles-based AI training |
| 2022 | [**Chain-of-Thought Prompting**](https://arxiv.org/abs/2201.11903) | Reasoning through step-by-step |
| 2023 | [**Llama 2**](https://arxiv.org/abs/2307.09288) | Open-source frontier democratization |
| 2023 | [**Toolformer**](https://arxiv.org/abs/2302.04761) | LLMs learning to use tools |
| 2024 | [**DeepSeek-R1**](https://arxiv.org/abs/2501.12948) | Reasoning via reinforcement learning |
| 2024 | [**Claude's Character**](https://anthropic.com/research/claude-character) | Building character in AI systems |

---

## Topic-Based Reading Lists

### For Prompt Engineering

1. [Chain-of-Thought Prompting Elicits Reasoning in LLMs](https://arxiv.org/abs/2201.11903)
2. [Self-Consistency Improves Chain of Thought Reasoning](https://arxiv.org/abs/2203.11171)
3. [Tree of Thoughts](https://arxiv.org/abs/2305.10601)
4. [Large Language Models are Zero-Shot Reasoners](https://arxiv.org/abs/2205.11916)
5. [ReAct: Synergizing Reasoning and Acting in LLMs](https://arxiv.org/abs/2210.03629)

### For RAG & Retrieval

1. [RAG: Retrieval-Augmented Generation for Knowledge-Intensive NLP](https://arxiv.org/abs/2005.11401)
2. [FAISS: A Library for Efficient Similarity Search](https://arxiv.org/abs/1702.08734)
3. [Dense Passage Retrieval](https://arxiv.org/abs/2004.04906)
4. [REALM: Retrieval-Augmented Language Model Pre-Training](https://arxiv.org/abs/2002.08909)
5. [Lost in the Middle: How LLMs Use Long Contexts](https://arxiv.org/abs/2307.03172)

### For Fine-Tuning & PEFT

1. [LoRA: Low-Rank Adaptation of Large Language Models](https://arxiv.org/abs/2106.09685)
2. [QLoRA: Efficient Finetuning of Quantized LLMs](https://arxiv.org/abs/2305.14314)
3. [Prefix-Tuning](https://arxiv.org/abs/2101.00190)
4. [The Power of Scale for Parameter-Efficient Prompt Tuning](https://arxiv.org/abs/2104.08691)

### For AI Safety & Alignment

1. [Constitutional AI](https://arxiv.org/abs/2212.08073)
2. [RLHF: Learning to Summarize from Human Feedback](https://arxiv.org/abs/2009.01325)
3. [Scalable Oversight](https://arxiv.org/abs/1610.09512)
4. [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565)
5. [Reward Hacking / Specification Gaming](https://arxiv.org/abs/1906.01820)
6. [Sleeper Agents: Training Deceptive LLMs](https://arxiv.org/abs/2401.05566)

### For Multimodal AI

1. [CLIP](https://arxiv.org/abs/2103.00020)
2. [DALL-E 2](https://arxiv.org/abs/2204.06125)
3. [Stable Diffusion (High-Resolution Image Synthesis)](https://arxiv.org/abs/2112.10752)
4. [Flamingo: a Visual Language Model](https://arxiv.org/abs/2204.14198)
5. [LLaVA: Visual Instruction Tuning](https://arxiv.org/abs/2304.08485)

---

## How to Read AI Papers

### The 3-Pass Method

**Pass 1: Overview (5-10 minutes)**
- Read title, abstract, introduction, conclusion
- Look at figures and tables
- Decide: is this worth more time?

**Pass 2: Understanding (30-60 minutes)**
- Read body, skip proofs and math details
- Focus on methods and results sections
- Write 3 sentences: problem, approach, result

**Pass 3: Deep Dive (2-4 hours)**
- Understand all technical details
- Reproduce key results if possible
- Identify weaknesses and future work

### Summary Template

```markdown
## Paper: [Title]

**Problem:** What problem does this solve?
**Approach:** What's the key idea/method?
**Results:** What did they achieve? (key numbers)
**Why It Matters:** How does this change things?
**Limitations:** What doesn't it address?
**Code:** [Link if available]
```

---

## Staying Current

### Daily / Weekly Routine

```
Monday:     Check arXiv cs.CL and cs.AI for the week
Tuesday:    Read Hugging Face Papers digest
Wednesday:  Papers With Code trending this week
Thursday:   Yannic Kilcher or AI Explained video
Friday:     Deep dive on one paper of interest
```

### Must-Follow Researchers on Twitter/X

- **Andrej Karpathy** (@karpathy) — OpenAI/Tesla, practical insights
- **Yann LeCun** (@ylecun) — Meta AI Chief Scientist, contrarian takes
- **Ilya Sutskever** (@ilyasut) — OpenAI co-founder
- **Sam Altman** (@sama) — OpenAI CEO
- **Dario Amodei** (@DarioAmodei) — Anthropic CEO
- **Lilian Weng** (@lilianweng) — OpenAI research blog
- **Sebastian Ruder** (@seb_ruder) — NLP researcher, Google
- **Yannic Kilcher** (@ykilcher) — Paper explainer

---

## Paper Search Tools

| Tool | Best For |
|------|----------|
| [arXiv](https://arxiv.org) | Latest preprints, daily |
| [Papers With Code](https://paperswithcode.com) | Reproducible research + leaderboards |
| [Semantic Scholar](https://semanticscholar.org) | Citation graph, recommendations |
| [Connected Papers](https://connectedpapers.com) | Visual citation network |
| [Elicit](https://elicit.com) | AI-assisted literature review |
| [Hugging Face Papers](https://huggingface.co/papers) | Community curated |
| [Google Scholar](https://scholar.google.com) | Broad academic search |

---

*Last updated: April 2025 · [Back to main README](../../README.md) · by [CodeBeez Innovation](https://codebeez.xyz) & [Abid Redwan](https://aredwan.com)*
