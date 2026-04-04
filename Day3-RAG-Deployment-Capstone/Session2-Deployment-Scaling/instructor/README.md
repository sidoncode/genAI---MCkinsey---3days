# Session 2 — Instructor Notebook

## Deployment and Scaling for Consulting AI

### Teaching Notes

**Duration:** 1 hour 45 minutes (11:00 – 12:45)

### Suggested Timing

| Segment | Duration | Content |
|---|---|---|
| Introduction | 10 min | Production vs. prototype mindset for consulting AI |
| Demo 1 | 10 min | McKinseyAIService — consulting AI service design |
| Demo 2 | 12 min | SemanticCache for recurring consulting queries |
| Demo 3 | 12 min | ConsultingAIMonitor — structured logging per engagement |
| Demo 4 | 10 min | ConsultingModelRouter — routing by complexity |
| Demo 5 | 10 min | ConsultingCostTracker — per-engagement cost tracking |
| Task 1 | 10 min | RateLimitedConsultingAI |
| Task 2 | 10 min | ConsultingStreamingHandler |
| Task 3 | 10 min | ConsultingTieredCache |
| Task 4 | 12 min | McKinseyAIGateway |
| Track Selection | 9 min | Explain tracks, let students choose |

### What's Inside

- **5 Demos** — Fully executed with detailed commentary and McKinsey consulting talking points
- **4 Solved Tasks** — Complete solutions with step-by-step explanations

### Key Teaching Points

1. Semantic caching is the #1 cost optimization for consulting AI — many engagement teams ask similar questions
2. Monitor per engagement: latency, token usage, error rates, and quality scores
3. Model routing (simple queries → gpt-4o-mini, complex analyses → gpt-4o) can cut consulting AI costs 60-80%
4. Design for failure: retries, circuit breakers, fallback responses — critical for client-facing consulting systems

### Track Selection Guidance (end of session)

- **Track A (Production RAG — McKinsey Knowledge Assistant):** Best for participants interested in consulting knowledge management, search, and information retrieval
- **Track B (Multi-Agent — McKinsey Engagement Team):** Best for participants interested in engagement team simulation, agent architectures, and autonomous consulting workflows
- Both tracks are equally valuable — choose based on interest, not difficulty

### Common Student Questions

- "How much does it cost to run a consulting AI app?" — Walk through a cost calculation with token prices per engagement
- "Should I self-host or use an API?" — API for most consulting use cases; self-host only for client data compliance requirements
- "How do I handle spikes in usage?" — Queue-based architecture with auto-scaling workers
