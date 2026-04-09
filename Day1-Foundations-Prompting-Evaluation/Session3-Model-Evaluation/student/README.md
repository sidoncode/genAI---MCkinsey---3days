# Session 3 — Student Notebook

## Model Evaluation and Comparison

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
   jupyter notebook Session3_Student_Model_Evaluation.ipynb
   ```

### What's Inside

- **7 Demos** — Follow along with the instructor. Run each cell and observe the outputs. All examples use McKinsey consulting scenarios.
- **8 Hands-On Tasks** — Complete the TODO sections. Each task includes hints to guide you.

### Task Summary

| Task | Topic | Difficulty |
|---|---|---|
| Task 1 | Create a custom evaluation rubric for McKinsey consulting AI | Beginner |
| Task 2 | Compare multiple models on McKinsey consulting tasks | Intermediate |
| Task 3 | Build an automated evaluation pipeline with consulting test cases | Advanced |
| Task 4 | Visualize evaluation results with bar charts, radar charts, and scatter plots | Intermediate |
| Task 5 | Build a G-Eval rubric scorer for consulting deliverables | Intermediate |
| Task 6 | Build a pairwise model comparison judge | Advanced |
| Task 7 | Evaluate LLM consistency with repeated sampling | Intermediate |
| Task 8 | Build a model selection report generator | Advanced |

### Tips

- Think about what "McKinsey quality" means before defining metrics — MECE, actionability, executive readiness
- Use consistent test prompts across models for fair comparison
- Demo 6 introduces scikit-learn metrics — Demo 7 implements G-Eval from scratch
- Tasks 5-8 build on Demos 2 and 7 — combine rubrics, G-Eval, and benchmarking into production-ready tools
- The `.env` file configures model names, temperature, and max tokens — you can change these without modifying code
