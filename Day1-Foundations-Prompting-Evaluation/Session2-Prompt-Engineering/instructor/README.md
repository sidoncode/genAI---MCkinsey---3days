# Session 2 — Instructor Notebook

## Prompt Engineering for Agentic Behaviors

### Teaching Notes

**Duration:** 1 hour 45 minutes (11:00 – 12:45)

### Suggested Timing

| Segment | Duration | Content |
|---|---|---|
| Introduction | 8 min | Recap of Session 1, session objectives |
| Demo 1 | 10 min | Zero-shot vs. few-shot — client feedback classification |
| Demo 2 | 10 min | Chain-of-Thought — retail restructuring analysis |
| Demo 3 | 10 min | Role-based personas — McKinsey practice area leads |
| Demo 4 | 10 min | Structured output — client executive data extraction |
| Demo 5 | 10 min | Multi-turn conversation — engagement planning |
| Demo 6 | 10 min | LangChain templates — structured consulting deliverables |
| Task 1 | 5 min | McKinsey Industry Research Agent |
| Task 2 | 8 min | ReAct for PE due diligence |
| Task 3 | 6 min | McKinsey prompt template library |
| Task 4 | 8 min | McKinsey Analyst Agent with tools |
| Task 5 | 6 min | Few-shot consulting deliverable classifier |
| Task 6 | 6 min | Chain-of-Thought market sizing agent |
| Task 7 | 6 min | Extract structured data from meeting notes (JSON mode) |
| Task 8 | 8 min | Conversation summarizer for long engagements |
| Wrap-up | 5 min | Q&A and bridge to Session 3 |

### What's Inside

- **6 Demos** — Fully executed with detailed commentary and talking points
- **8 Solved Tasks** — Complete solutions with step-by-step explanations and approach descriptions

### Key Teaching Points

1. Show side-by-side comparisons of zero-shot vs. few-shot on client feedback to make the impact tangible
2. Chain-of-Thought mirrors McKinsey's structured problem-solving — connect it to MECE and hypothesis-driven thinking
3. The three practice-area personas (Demo 3) show how the same question gets different analyses from different specialist agents
4. LangChain (Demo 6) provides reusable patterns that scale across engagements — emphasize the composability
5. Few-shot classification (Task 5) teaches example selection and consistent label taxonomy — a foundation for automated document routing
6. The CoT vs. direct comparison (Task 6) makes reasoning benefits measurable — students can see the structural difference in outputs
7. JSON mode extraction (Task 7) previews Day 2 structured outputs — emphasize schema design and validation
8. Conversation summarization (Task 8) introduces context window management — a critical skill for building production agents

### Common Student Questions

- "How long should a system prompt be?" — As detailed as needed, but concise; 200–500 words is typical for agents
- "When to use CoT vs. ReAct?" — CoT for reasoning; ReAct when the agent needs to take actions
- "Can we combine techniques?" — Absolutely; real agents use multiple techniques together
- "Why classify documents with few-shot instead of fine-tuning?" — Few-shot is faster to iterate and needs no training data; fine-tuning for very high-volume production use
- "How does the conversation summarizer handle information loss?" — It prioritizes decisions and action items; some detail is lost, which is an acceptable trade-off for staying within context limits
