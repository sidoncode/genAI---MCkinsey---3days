# Session 2: Deployment and Scaling for Consulting AI

**Time:** 11:00 – 12:45 (1 hour 45 minutes) | **Shared session — all participants**

## Overview

This session bridges the gap between notebook prototypes and production consulting AI systems. Participants will learn architecture patterns for McKinsey AI services, cost optimization through semantic caching of recurring consulting queries, monitoring per engagement, model routing by consulting complexity, and cost tracking — the patterns needed to deploy consulting AI at scale. Track selection for the afternoon capstone happens at the close of this session.

## Key Topics

- Consulting AI service architecture (McKinseyAIService with knowledge_search, engagement_assistant, briefing_generator)
- Cost optimization: semantic caching for recurring consulting queries
- Monitoring and observability per engagement (ConsultingAIMonitor)
- Model routing by consulting complexity (simple → gpt-4o-mini, complex → gpt-4o)
- Cost tracking per engagement (ConsultingCostTracker)

## Notebooks

| Notebook | Description |
|---|---|
| `student/Session2_Student_Deployment.ipynb` | Guided demos + TODO exercises with hints |
| `instructor/Session2_Instructor_Deployment.ipynb` | Fully solved demos + exercises with explanations |

## Demos (5)

1. **Demo 1:** McKinseyAIService — consulting AI service with request/response models
2. **Demo 2:** SemanticCache for recurring consulting queries
3. **Demo 3:** ConsultingAIMonitor — structured logging per engagement
4. **Demo 4:** ConsultingModelRouter — routing by consulting complexity
5. **Demo 5:** ConsultingCostTracker — cost tracking per engagement

## Exercises (4)

1. **Task 1:** Build a RateLimitedConsultingAI service
2. **Task 2:** Implement a ConsultingStreamingHandler for client briefings
3. **Task 3:** Create a ConsultingTieredCache (exact → semantic → LLM)
4. **Task 4:** Build a McKinseyAIGateway combining routing + caching + rate limiting + monitoring + cost tracking
