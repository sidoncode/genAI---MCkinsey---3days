# Day 3 — RAG, Deployment, Capstone & Debrief

Welcome to Day 3 of the **McKinsey Agentic AI Systems** training program. This final day brings everything together — deep-dive RAG engineering with McKinsey knowledge bases, deployment and scaling of consulting AI services, a hands-on capstone lab (choose your track), and a closing reflection on AI governance for consulting firms.

All demos and exercises use **McKinsey consulting scenarios**: building RAG systems over consulting frameworks and industry reports, deploying consulting AI services with caching and monitoring, and governance guardrails for AI-generated strategy recommendations.

---

## Schedule

| Time | Session | Focus |
|---|---|---|
| 9:00–10:45 | Session 1 | Module 9: Retrieval-Augmented Generation (shared) |
| 10:45–11:00 | Break | |
| 11:00–12:45 | Session 2 | Module 10: Deployment and Scaling (shared; track selection at close) |
| 12:45–1:30 | Lunch | |
| 1:30–3:15 | Session 3 | Parallel Capstone Labs — Track A: Production RAG Service / Track B: Multi-Agent Orchestration |
| 3:15–3:30 | Break | |
| 3:30–5:00 | Session 4 | Cross-Track Debrief, Module 11: Governance Framing & Closing Reflection |

---

## Folder Structure

```
Day3-RAG-Deployment-Capstone/
├── README.md
├── Session1-Retrieval-Augmented-Generation/
│   ├── README.md
│   ├── student/
│   │   ├── README.md
│   │   └── Session1_Student_RAG.ipynb
│   └── instructor/
│       ├── README.md
│       └── Session1_Instructor_RAG.ipynb
├── Session2-Deployment-Scaling/
│   ├── README.md
│   ├── student/
│   │   ├── README.md
│   │   └── Session2_Student_Deployment.ipynb
│   └── instructor/
│       ├── README.md
│       └── Session2_Instructor_Deployment.ipynb
├── Session3-Capstone-Labs/
│   ├── track-a-production-rag/
│   │   ├── README.md
│   │   ├── student/
│   │   │   ├── README.md
│   │   │   └── Session3A_Student_Production_RAG.ipynb
│   │   └── instructor/
│   │       ├── README.md
│   │       └── Session3A_Instructor_Production_RAG.ipynb
│   └── track-b-multi-agent/
│       ├── README.md
│       ├── student/
│       │   ├── README.md
│       │   └── Session3B_Student_Multi_Agent.ipynb
│       └── instructor/
│           ├── README.md
│           └── Session3B_Instructor_Multi_Agent.ipynb
└── Session4-Debrief-Governance/
    ├── README.md
    ├── student/
    │   ├── README.md
    │   └── Session4_Student_Debrief_Governance.ipynb
    └── instructor/
        ├── README.md
        └── Session4_Instructor_Debrief_Governance.ipynb
```

---

## How to Use

### For Students
- **Sessions 1 & 2** are shared — everyone works through the same material.
- **Session 3** is a parallel capstone — choose **Track A** (Production RAG Service with McKinsey knowledge base) or **Track B** (Multi-Agent Orchestration modeling consulting teams). Your instructor will guide the selection at the end of Session 2.
- **Session 4** brings both tracks together for a cross-team debrief and governance discussion.
- All scenarios use McKinsey consulting context — building knowledge systems for consulting firms, deploying AI services for engagement teams, and governing AI in client work.

### For Instructors
- Sessions 1 & 2 follow the standard demo + task format with McKinsey consulting scenarios.
- For Session 3, split the room by track. Each track has its own notebook with a self-contained capstone project.
- Session 4 is discussion-driven with guided exercises. Encourage cross-track presentations and reflection on AI governance in consulting.

---

## Prerequisites

- Completion of **Day 1** and **Day 2**
- Python 3.9+
- Jupyter Notebook / JupyterLab
- An OpenAI API key (set as `OPENAI_API_KEY` environment variable)
- Required packages:

```bash
pip install openai tiktoken pydantic langchain langchain-openai langchain-community langgraph chromadb faiss-cpu pandas matplotlib numpy
```

---

## Learning Outcomes

By the end of Day 3, participants will be able to:

1. Build production-grade RAG systems over McKinsey knowledge bases with chunking, embedding, retrieval, and reranking
2. Deploy consulting AI services with caching, monitoring, model routing, and cost controls
3. Complete an end-to-end capstone project (Production RAG Service or Multi-Agent Consulting System)
4. Articulate governance principles for responsible AI deployment in consulting engagements
5. Evaluate agentic consulting systems with structured metrics and deployment readiness criteria
