# Session 4 — Instructor Notebook

## Multi-Agent Workflows for McKinsey Engagement Teams

### Teaching Notes

**Duration:** 1 hour 30 minutes (3:30 – 5:00)

### Suggested Timing

| Segment | Duration | Content |
|---|---|---|
| Introduction | 8 min | Multi-agent motivation — McKinsey team structures as design patterns |
| Demo 1 | 10 min | Supervisor-worker: Partner → analyst + strategist + ops expert |
| Demo 2 | 10 min | Agent handoff: Strategy → Operations → Implementation |
| Demo 3 | 10 min | Parallel M&A due diligence workstreams |
| Demo 4 | 10 min | Collaborative presentation creation |
| Demo 5 | 10 min | End-to-end engagement intake & delivery |
| Task 1 | 8 min | EM routing (quantitative vs. strategic) |
| Task 2 | 8 min | Industry landscape assessment |
| Task 3 | 10 min | Cross-functional transformation |
| Task 4 | 12 min | Complete M&A due diligence system |
| Wrap-up | 4 min | Day 2 review and Day 3 preview |

### What's Inside

- **5 Demos** — Fully executed with detailed commentary and McKinsey consulting talking points
- **4 Solved Tasks** — Complete solutions with step-by-step explanations

### Key Teaching Points

1. McKinsey engagement teams naturally map to multi-agent architectures — Partner as supervisor, Associates as specialized workers
2. The supervisor pattern is the most common starting point — one Engagement Manager orchestrates many specialists
3. Agent handoff mirrors consulting workflow stages — Strategy → Operations → Implementation requires careful context management
4. Not everything needs multi-agent — use the simplest architecture that solves the consulting problem

### Common Student Questions

- "When should I use multi-agent vs. a single agent?" — When tasks require distinct expertise (financial analysis vs. strategy) or can be parallelized (M&A workstreams)
- "How do agents share information?" — Through shared engagement state in LangGraph, or structured message passing
- "What about error handling across agents?" — The Engagement Manager (supervisor) should handle failures and reassign or escalate
