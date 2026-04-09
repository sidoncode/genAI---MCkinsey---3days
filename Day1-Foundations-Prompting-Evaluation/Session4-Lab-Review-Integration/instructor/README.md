# Session 4 — Instructor Notebook

## Day 1 Lab Review & Integration

### Teaching Notes

**Duration:** 1 hour 30 minutes (3:30 – 5:00)

### What's Inside

- **3 Demos** — Fully executed with detailed commentary and talking points
- **4 Solved Tasks** — Complete solutions with step-by-step explanations and approach descriptions

### Suggested Timing

| Segment | Duration | Content |
|---|---|---|
| Introduction | 5 min | Recap of Day 1 sessions, session objectives |
| Demo 1 | 10 min | End-to-end consulting analysis pipeline |
| Demo 2 | 10 min | Cost-quality trade-off analysis |
| Demo 3 | 10 min | Day 2 preview — raw API vs LangChain |
| Task 1 | 10 min | End-to-end consulting deliverable generator |
| Task 2 | 10 min | Multi-persona comparison |
| Task 3 | 10 min | Consulting AI readiness assessment |
| Task 4 | 15 min | System architecture design exercise |
| Wrap-up | 10 min | Q&A, key takeaways, Day 2 preview |

### Key Teaching Points

1. Demo 1 shows how Sessions 1-3 combine into a single pipeline — emphasize the generate-evaluate-report pattern
2. Cost estimation (Demo 2) is critical for scoping AI-augmented consulting engagements — connect to real engagement budgeting
3. Demo 3 previews LangChain — show how composability reduces boilerplate and enables reuse across engagements
4. Task 4 (system design) is the most important exercise — it forces participants to think architecturally about combining Day 1 concepts
5. Explicitly connect each component to what they will build on Day 2 and Day 3

### Common Student Questions

- "Which practice persona works best?" — It depends on the question; Task 2 demonstrates this empirically
- "How do we handle quality failures in production?" — Quality gates with retry loops (Day 2 LangGraph cycles)
- "Is the cost estimation accurate?" — It's directionally correct; production systems need usage monitoring (Day 3)
- "How does the readiness assessment scale?" — Add more test cases and criteria; automate with CI/CD pipelines

### Bridge to Day 2

Preview what comes next:
- **Session 1 (Day 2):** Structured outputs — JSON mode, function calling, Pydantic for consulting data extraction
- **Session 2 (Day 2):** LangChain — LCEL chains, custom consulting tools, RAG pipelines
- **Session 3 (Day 2):** LangGraph — StateGraph, conditional edges, cycles for consulting workflows
- **Session 4 (Day 2):** Multi-Agent — supervisor-worker teams modeling McKinsey engagement structures
