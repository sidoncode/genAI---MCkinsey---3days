# Day 1 — Foundations, Prompting & Evaluation

Welcome to Day 1 of the **McKinsey Agentic AI Systems** training program. This day establishes the core building blocks — LLM fundamentals, prompt engineering for agentic behaviors, and model evaluation — all applied to **McKinsey consulting scenarios** including strategy analysis, M&A due diligence, client engagement planning, and consulting deliverable generation.

---

## Schedule

| Time | Session | Focus |
|---|---|---|
| 9:00–10:45 | Session 1 | Module 1: Modern LLM Foundations — API setup, tokenization, parameters, embeddings, reasoning |
| 10:45–11:00 | Break | |
| 11:00–12:45 | Session 2 | Module 2: Prompt Engineering — few-shot, CoT, ReAct, personas, LangChain templates |
| 12:45–1:30 | Lunch | |
| 1:30–3:15 | Session 3 | Module 3: Model Evaluation — rubrics, LLM-as-Judge, benchmarking, sklearn, DeepEval |
| 3:15–3:30 | Break | |
| 3:30–5:00 | Session 4 | Day 1 Lab Review & Integration (facilitated discussion) |

---

## Folder Structure

```
Day1-Foundations-Prompting-Evaluation/
├── README.md
├── Session1-Modern-LLM-Foundations/
│   ├── README.md
│   ├── student/
│   │   ├── README.md
│   │   └── Session1_Student_LLM_Foundations.ipynb
│   └── instructor/
│       ├── README.md
│       └── Session1_Instructor_LLM_Foundations.ipynb
├── Session2-Prompt-Engineering/
│   ├── README.md
│   ├── student/
│   │   ├── README.md
│   │   └── Session2_Student_Prompt_Engineering.ipynb
│   └── instructor/
│       ├── README.md
│       └── Session2_Instructor_Prompt_Engineering.ipynb
├── Session3-Model-Evaluation/
│   ├── README.md
│   └── student/
│       ├── README.md
│       └── Session3_Student_Model_Evaluation.ipynb
└── Session4-Lab-Review-Integration/
    └── README.md
```

---

## How to Use

### For Students
- Open the **student/** notebook for the current session.
- Each notebook contains **guided demos** to follow along and **hands-on tasks** with TODO placeholders and hints.
- All scenarios use McKinsey consulting context — think about how each technique applies to real engagement work.
- Complete each task by filling in the code where indicated.

### For Instructors
- Open the **instructor/** notebook for the current session.
- Each notebook contains the **same demos** with detailed commentary and **fully solved tasks** with explanations.
- Use McKinsey scenarios to make concepts tangible — connect each technique back to real consulting work.
- Session 4 is a facilitated review discussion (no notebook required).

---

## Prerequisites

- Python 3.9+
- Jupyter Notebook / JupyterLab
- An OpenAI API key (set as `OPENAI_API_KEY` environment variable)
- Required packages:

```bash
pip install openai tiktoken pandas matplotlib numpy scikit-learn deepeval langchain langchain-openai
```

---

## Learning Outcomes

By the end of Day 1, participants will be able to:

1. Explain modern LLM architectures, embeddings, and reasoning capabilities for agentic consulting systems
2. Apply prompt engineering techniques (few-shot, CoT, ReAct, LangChain templates) to McKinsey consulting analysis
3. Evaluate and compare LLM models using structured rubrics, sklearn metrics, and DeepEval/G-Eval
4. Integrate foundations, prompting, and evaluation into an agentic consulting system prototype
