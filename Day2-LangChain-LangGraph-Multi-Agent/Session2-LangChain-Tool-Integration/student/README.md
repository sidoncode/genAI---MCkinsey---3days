# Session 2 — Student Notebook

## LangChain Development & Consulting Tool Integration

### Setup Instructions

1. Ensure Python 3.9+ is installed
2. Install required packages:
   ```bash
   pip install langchain langchain-openai langchain-community tiktoken
   ```
3. Set your API key:
   ```bash
   export OPENAI_API_KEY="your-api-key-here"
   ```
4. Open the notebook:
   ```bash
   jupyter notebook Session2_Student_LangChain_Tool_Integration.ipynb
   ```

### What's Inside

- **5 Demos** — Follow along with the instructor. Run each cell to see how LangChain enables McKinsey consulting analysis pipelines.
- **4 Hands-On Tasks** — Complete the TODO sections to build consulting tools and RAG systems. Each task includes hints.

### Task Summary

| Task | Topic | Difficulty |
|---|---|---|
| Task 1 | Build a consulting analysis chain with JSON output | Beginner |
| Task 2 | Create custom consulting tools (competitor analysis, market sizing, engagement ROI) | Intermediate |
| Task 3 | Implement a ConsultingAdvisor with conversation memory | Intermediate |
| Task 4 | Build a ConsultingRAG class with document splitting and retrieval | Advanced |

### Tips

- Read the hints carefully before writing code
- Run demo cells first to understand the patterns
- LCEL uses the `|` (pipe) operator — think of it as Unix pipes for consulting analysis chains
- The `@tool` decorator is your best friend for creating custom consulting tools
