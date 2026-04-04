# Session 2 — Instructor Notebook

## LangChain Development & Consulting Tool Integration

### Teaching Notes

**Duration:** 1 hour 45 minutes (11:00 – 12:45)

### Suggested Timing

| Segment | Duration | Content |
|---|---|---|
| Introduction | 10 min | LangChain overview — why frameworks matter for consulting AI |
| Demo 1 | 10 min | ChatModels with McKinsey partner persona, PromptTemplates |
| Demo 2 | 12 min | LCEL chains for MECE and Porter's Five Forces analysis |
| Demo 3 | 12 min | Custom consulting tools (market sizing, benchmarks, financial ratios) |
| Demo 4 | 10 min | Document splitting for McKinsey consulting reports |
| Demo 5 | 10 min | Simple RAG over McKinsey knowledge base |
| Task 1 | 10 min | Consulting analysis chain with JSON output |
| Task 2 | 10 min | Custom tools (competitor analysis, engagement ROI) |
| Task 3 | 10 min | ConsultingAdvisor with memory |
| Task 4 | 15 min | ConsultingRAG class |
| Wrap-up | 6 min | Q&A and key takeaways |

### What's Inside

- **5 Demos** — Fully executed with detailed commentary and McKinsey consulting talking points
- **4 Solved Tasks** — Complete solutions with step-by-step explanations

### Key Teaching Points

1. LangChain provides composable building blocks — emphasize the Runnable interface as the unifying abstraction for consulting pipelines
2. LCEL is the modern way to build chains — show how McKinsey frameworks (MECE, Porter's) map naturally to chain composition
3. Custom tools make consulting agents useful — the `@tool` decorator simplifies creation of market sizing, benchmarking, and financial analysis tools
4. RAG over consulting knowledge bases is the most common production pattern — connect to the full RAG pipeline on Day 3

### Common Student Questions

- "Why use LangChain instead of raw OpenAI calls?" — Composability, consulting tool integration, memory, and ecosystem
- "What is LCEL vs. the old chain API?" — LCEL is the current standard; old chains are legacy
- "How does RAG differ from fine-tuning?" — RAG adds consulting knowledge at inference time; fine-tuning changes model weights
