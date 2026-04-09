# Session 2 — Student Notebook

## Prompt Engineering for Agentic Behaviors

### Setup Instructions

1. Ensure Python 3.9+ is installed
2. Install required packages from the project root:
   ```bash
   pip install -r requirements.txt
   ```
3. Configure your API key in the `.env` file at the project root:
   ```env
   OPENAI_API_KEY=your-api-key-here
   ```
4. Open the notebook:
   ```bash
   jupyter notebook Session2_Student_Prompt_Engineering.ipynb
   ```

### What's Inside

- **6 Demos** — Follow along with the instructor. Run each cell and observe the outputs. All examples use McKinsey consulting scenarios.
- **8 Hands-On Tasks** — Complete the TODO sections. Each task includes hints to guide you.

### Task Summary

| Task | Topic | Difficulty |
|---|---|---|
| Task 1 | Design system prompts for a McKinsey Industry Research Agent | Beginner |
| Task 2 | Implement ReAct-style prompting for PE due diligence | Intermediate |
| Task 3 | Create a reusable McKinsey prompt template library | Intermediate |
| Task 4 | Build a McKinsey Analyst Agent with consulting tools | Advanced |
| Task 5 | Build a few-shot consulting deliverable classifier | Intermediate |
| Task 6 | Chain-of-Thought market sizing agent with direct vs. CoT comparison | Intermediate |
| Task 7 | Extract structured data from client meeting notes (JSON mode) | Intermediate |
| Task 8 | Build a conversation summarizer for long engagements | Advanced |

### Tips

- Pay close attention to how small prompt changes lead to very different outputs
- All scenarios use McKinsey consulting context — think about how you would frame prompts for real client work
- ReAct (Task 2) follows a Thought → Action → Observation loop — keep this pattern
- For Task 4, the agent decides which consulting tool to call at each step — this previews Day 2 tool-calling
- Tasks 5-8 introduce patterns (classification, structured extraction, context management) that you will use extensively in Day 2 and Day 3
- The `.env` file configures model names, temperature, and max tokens — you can change these without modifying code
