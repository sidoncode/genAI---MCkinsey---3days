# Session 4: Day 1 Lab Review & Integration

**Time:** 3:30 – 5:00 (1 hour 30 minutes)

## Overview

This capstone session integrates all Day 1 concepts — LLM foundations (Session 1), prompt engineering (Session 2), and model evaluation (Session 3) — into practical consulting AI exercises. Participants build end-to-end pipelines, compare model configurations, and design consulting AI system architectures that preview Day 2 frameworks.

## Key Topics

- End-to-end consulting analysis pipelines (generate → evaluate → report)
- Cost-quality trade-off analysis across model configurations
- Multi-persona comparison for consulting deliverables
- Consulting AI readiness assessment and deployment criteria
- Day 2 preview: from raw API calls to LangChain LCEL chains

## Notebooks

| Notebook | Description |
|---|---|
| `student/Session4_Student_Lab_Review.ipynb` | 3 guided demos + 4 TODO exercises with hints |
| `instructor/Session4_Instructor_Lab_Review.ipynb` | 3 demos + 4 exercises with full solutions and approach explanations |

## Demos (3)

1. **Demo 1:** End-to-End Consulting Analysis Pipeline — generate structured analysis with persona prompting, then auto-evaluate with G-Eval scoring
2. **Demo 2:** Cost-Quality Trade-off Analysis — compare configurations on quality, latency, and cost to find the optimal operating point
3. **Demo 3:** Day 2 Preview — same task done with raw API calls vs. LangChain LCEL chains

## Exercises (4)

| Task | Topic | Difficulty |
|---|---|---|
| Task 1 | Build an end-to-end consulting deliverable generator with auto-evaluation | Intermediate |
| Task 2 | Build a multi-persona comparison across McKinsey practice areas | Intermediate |
| Task 3 | Build a consulting AI readiness assessment with test suite and scorecard | Advanced |
| Task 4 | Design a consulting AI system architecture mapping Day 1 concepts to components | Advanced |

## Environment Variables

All notebooks load configuration from the project root `.env` file via `python-dotenv`. Key variables used in this session:

| Variable | Default | Purpose |
|---|---|---|
| `OPENAI_API_KEY` | *(required)* | OpenAI API authentication |
| `OPENAI_MODEL_NAME` | `gpt-4o-mini` | Chat model used across demos and tasks |
