# Session 2 — Student Notebook

## Deployment and Scaling for Consulting AI

### Setup Instructions

1. Ensure Python 3.9+ is installed
2. Install required packages:
   ```bash
   pip install openai langchain langchain-openai pandas matplotlib
   ```
3. Set your API key:
   ```bash
   export OPENAI_API_KEY="your-api-key-here"
   ```
4. Open the notebook:
   ```bash
   jupyter notebook Session2_Student_Deployment.ipynb
   ```

### What's Inside

- **5 Demos** — Follow along with the instructor. Run each cell to see how consulting AI systems are deployed and optimized for McKinsey use cases.
- **4 Hands-On Tasks** — Complete the TODO sections to build production consulting AI components. Each task includes hints.

### Task Summary

| Task | Topic | Difficulty |
|---|---|---|
| Task 1 | Build a RateLimitedConsultingAI service | Beginner |
| Task 2 | Implement a ConsultingStreamingHandler for client briefings | Intermediate |
| Task 3 | Create a ConsultingTieredCache (exact → semantic → LLM) | Intermediate |
| Task 4 | Build a McKinseyAIGateway (routing + caching + rate limiting + monitoring) | Advanced |

### Tips

- Think about cost from the start — consulting AI calls across engagement teams add up fast
- Semantic caching is the single biggest optimization — many teams ask similar questions
- Monitor everything: latency, token usage, error rates, and consulting quality scores
- At the end of this session, you will choose your capstone track (A or B) for Session 3
