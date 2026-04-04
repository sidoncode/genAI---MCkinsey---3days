# Session 3 — Instructor Notebook

## LangGraph Orchestration for Consulting Workflows

### Teaching Notes

**Duration:** 1 hour 45 minutes (1:30 – 3:15)

### Suggested Timing

| Segment | Duration | Content |
|---|---|---|
| Introduction | 10 min | Why graphs? LangGraph for consulting engagement lifecycles |
| Demo 1 | 10 min | EngagementState pipeline (scope → industry → brief) |
| Demo 2 | 12 min | Conditional routing by engagement complexity |
| Demo 3 | 12 min | ReAct agent as McKinsey market research analyst |
| Demo 4 | 10 min | Iterative partner-quality refinement cycle |
| Demo 5 | 10 min | Human-in-the-loop partner sign-off |
| Task 1 | 10 min | Client onboarding pipeline |
| Task 2 | 10 min | PE due diligence router |
| Task 3 | 10 min | MECE analysis refinement loop |
| Task 4 | 15 min | Market entry assessment agent |
| Wrap-up | 6 min | Q&A and key takeaways |

### What's Inside

- **5 Demos** — Fully executed with detailed commentary and McKinsey consulting talking points
- **4 Solved Tasks** — Complete solutions with step-by-step explanations

### Key Teaching Points

1. LangGraph makes consulting workflow control flow explicit — contrast with implicit chain execution
2. EngagementState is the central concept — all consulting context flows through the shared TypedDict
3. Conditional edges route engagements by complexity — just as a Partner assigns different team structures based on engagement scope
4. Iterative refinement cycles model the consulting review process — draft → feedback → revision until partner-quality

### Common Student Questions

- "How is LangGraph different from LangChain?" — LangChain is for linear chains; LangGraph adds branching, cycles, and state — think engagement workflows vs. simple analyses
- "Can I use LangGraph without LangChain?" — Yes, but they integrate well together
- "When should I use cycles vs. linear graphs?" — Cycles for iterative refinement (partner review loops), retries, or quality improvement
