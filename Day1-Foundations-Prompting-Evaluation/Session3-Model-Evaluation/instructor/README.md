# Session 3 — Instructor Notebook

## Model Evaluation and Comparison

### Teaching Notes

**Duration:** 1 hour 45 minutes (1:30 – 3:15)

### What's Inside

- **7 Demos** — Fully executed with detailed commentary and talking points
- **8 Solved Tasks** — Complete solutions with step-by-step explanations and approach descriptions

### Suggested Timing

| Segment | Duration | Content |
|---|---|---|
| Introduction | 8 min | Why evaluation matters for consulting AI systems |
| Demo 1 | 8 min | McKinsey evaluation criteria rubric |
| Demo 2 | 10 min | LLM-as-Judge on digital transformation analysis |
| Demo 3 | 8 min | Benchmarking on consulting prompts |
| Demo 4 | 8 min | Cost analysis across models |
| Demo 5 | 8 min | A/B testing with McKinsey persona |
| Demo 6 | 10 min | Scikit-learn metrics on client feedback |
| Demo 7 | 10 min | DeepEval/G-Eval on consulting outputs |
| Task 1 | 5 min | Custom consulting rubric |
| Task 2 | 6 min | Model comparison on consulting tasks |
| Task 3 | 6 min | Evaluation pipeline |
| Task 4 | 5 min | Visualization and analysis |
| Task 5 | 5 min | G-Eval rubric scorer |
| Task 6 | 6 min | Pairwise model comparison judge |
| Task 7 | 5 min | LLM consistency with repeated sampling |
| Task 8 | 6 min | Model selection report generator |
| Wrap-up | 5 min | Q&A and key takeaways |

### Key Teaching Points

1. Evaluation must be defined BEFORE building — not as an afterthought
2. McKinsey-quality criteria (MECE, strategic relevance, executive readiness) make evaluation concrete
3. LLM-as-Judge is powerful but has biases — discuss limitations
4. DeepEval provides a framework-level approach to LLM evaluation — compare with manual scoring
5. Cost and latency matter as much as quality for production consulting agents

### Common Student Questions

- "Is LLM-as-a-judge reliable?" — Generally yes for relative rankings; less so for absolute scores
- "How many test cases do we need?" — At least 20–50 for meaningful comparison; more for production
- "Which model is best for consulting agents?" — It depends on the use case — that's why we evaluate!
