# Session 3: LangGraph Orchestration for Consulting Workflows

**Time:** 1:30 – 3:15 (1 hour 45 minutes)

## Overview

This session introduces LangGraph, a framework for building stateful, multi-step agentic workflows as directed graphs — modeled on McKinsey consulting engagement lifecycles. Participants will learn to orchestrate complex consulting workflows using nodes, edges, and shared state — enabling engagement complexity routing, iterative partner-quality refinement loops, and human-in-the-loop partner sign-off patterns.

## Key Topics

- LangGraph fundamentals: StateGraph, nodes, and edges for engagement pipelines
- TypedDict state schemas (EngagementState) and message passing
- Conditional edges for dynamic routing by engagement complexity (rapid/standard/transformation)
- ReAct agent pattern as a McKinsey market research analyst
- Cycles for iterative recommendation refinement until partner-quality
- Human-in-the-loop checkpointing for partner sign-off

## Notebooks

| Notebook | Description |
|---|---|
| `student/Session3_Student_LangGraph_Orchestration.ipynb` | Guided demos + TODO exercises with hints |
| `instructor/Session3_Instructor_LangGraph_Orchestration.ipynb` | Fully solved demos + exercises with explanations |

## Demos (5)

1. **Demo 1:** LangGraph basics — EngagementState pipeline (extract_scope → classify_industry → format_brief)
2. **Demo 2:** Conditional routing by engagement complexity (rapid / standard / transformation)
3. **Demo 3:** ReAct agent as a McKinsey market research analyst with simulated tools
4. **Demo 4:** Iterative recommendation refinement cycle until partner-quality
5. **Demo 5:** Human-in-the-loop partner sign-off before client delivery

## Exercises (4)

1. **Task 1:** Build a client onboarding pipeline (GlobalRetail Corp)
2. **Task 2:** Create a PE due diligence router (quick_screen / standard / deep_dive)
3. **Task 3:** Implement a MECE analysis refinement loop (cloud computing market)
4. **Task 4:** Build a market entry assessment agent (US digital health → India)
