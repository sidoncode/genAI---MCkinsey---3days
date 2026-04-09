# Session 4 — Student Notebook

## Day 1 Lab Review & Integration

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
   jupyter notebook Session4_Student_Lab_Review.ipynb
   ```

### What's Inside

- **3 Demos** — Follow along with the instructor. These demos show how Sessions 1-3 concepts combine into end-to-end consulting AI workflows.
- **4 Hands-On Tasks** — Complete the TODO sections. Each task includes hints to guide you.

### Task Summary

| Task | Topic | Difficulty |
|---|---|---|
| Task 1 | Build an end-to-end consulting deliverable generator with auto-evaluation | Intermediate |
| Task 2 | Build a multi-persona comparison across McKinsey practice areas | Intermediate |
| Task 3 | Build a consulting AI readiness assessment with test suite and scorecard | Advanced |
| Task 4 | Design a consulting AI system architecture mapping Day 1 concepts | Advanced |

### Tips

- This session integrates everything from Day 1 — review your work from Sessions 1-3 if needed
- Demo 1 establishes the `g_eval_quick()` and `consulting_pipeline()` functions — Tasks 1-3 build on these
- Task 4 is a design exercise — think about how each Day 1 concept maps to a real system component
- The Day 2 preview (Demo 3) shows where we are heading — composable chains replace raw API calls
- The `.env` file configures model names, temperature, and max tokens — you can change these without modifying code
