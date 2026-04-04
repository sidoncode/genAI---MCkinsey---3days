# Session 2: LangChain Development & Consulting Tool Integration

**Time:** 11:00 – 12:45 (1 hour 45 minutes)

## Overview

This session introduces LangChain, the most widely adopted framework for building LLM-powered applications, through the lens of McKinsey consulting workflows. Participants will learn its core abstractions — models, prompts, chains, and tools — and use LangChain Expression Language (LCEL) to compose modular consulting analysis pipelines that integrate with custom McKinsey tools and knowledge bases.

## Key Topics

- LangChain architecture: ChatModels with McKinsey partner persona, PromptTemplates for consulting analysis
- LangChain Expression Language (LCEL) for framework analysis chains (MECE, Porter's Five Forces)
- Custom consulting tool creation (market sizing, benchmark lookup, financial ratios, competitor analysis)
- Document splitting for McKinsey consulting reports
- Retrieval-Augmented Generation (RAG) over a McKinsey knowledge base

## Notebooks

| Notebook | Description |
|---|---|
| `student/Session2_Student_LangChain_Tool_Integration.ipynb` | Guided demos + TODO exercises with hints |
| `instructor/Session2_Instructor_LangChain_Tool_Integration.ipynb` | Fully solved demos + exercises with explanations |

## Demos (5)

1. **Demo 1:** LangChain basics — ChatModels with McKinsey partner persona, PromptTemplates for consulting analysis
2. **Demo 2:** Building LCEL chains for framework analysis (MECE, Porter's Five Forces)
3. **Demo 3:** Creating custom consulting tools (market_sizing_tool, benchmark_lookup_tool, financial_ratio_tool)
4. **Demo 4:** Document splitting for McKinsey consulting reports
5. **Demo 5:** Building a simple RAG pipeline over a McKinsey knowledge base

## Exercises (4)

1. **Task 1:** Build a consulting analysis chain with JSON output
2. **Task 2:** Create custom consulting tools (competitor_analysis, market_sizing_estimate, engagement_roi)
3. **Task 3:** Implement a ConsultingAdvisor with conversation memory
4. **Task 4:** Build a ConsultingRAG class with document splitting and keyword retrieval
