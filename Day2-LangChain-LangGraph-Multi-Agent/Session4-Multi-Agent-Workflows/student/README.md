# Session 4 — Student Notebook

## Multi-Agent Workflows for McKinsey Engagement Teams

### Setup Instructions

1. Ensure Python 3.9+ is installed
2. Install required packages:
   ```bash
   pip install langgraph langchain langchain-openai
   ```
3. Set your API key:
   ```bash
   export OPENAI_API_KEY="your-api-key-here"
   ```
4. Open the notebook:
   ```bash
   jupyter notebook Session4_Student_Multi_Agent_Workflows.ipynb
   ```

### What's Inside

- **5 Demos** — Follow along with the instructor. Run each cell to see how multi-agent systems model McKinsey engagement team structures.
- **4 Hands-On Tasks** — Complete the TODO sections to build consulting multi-agent systems. Each task includes hints.

### Task Summary

| Task | Topic | Difficulty |
|---|---|---|
| Task 1 | Build an Engagement Manager that routes quantitative vs. strategic requests | Intermediate |
| Task 2 | Implement an industry landscape assessment pipeline (renewable energy for PE) | Intermediate |
| Task 3 | Create a cross-functional transformation system ($5B consumer goods) | Advanced |
| Task 4 | Design a complete M&A due diligence system (MedTech Solutions $200M acquisition) | Advanced |

### Tips

- Read the hints carefully before writing code
- Run demo cells first to understand the patterns
- Think about McKinsey engagement teams: who leads, who does the analysis, how do workstreams coordinate?
- Consider what information each agent needs from other agents — just like Associates sharing findings with the Partner
