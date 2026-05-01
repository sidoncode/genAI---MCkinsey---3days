# Day 1 Instructor Guide: Foundations, Prompting & Evaluation

## Overview

**Theme:** Build the foundational skills for working with LLMs programmatically -- from raw API calls through prompt engineering to systematic evaluation.

**Learning Objectives:**
- Connect to LLMs via the OpenAI Python SDK and understand tokenization, context windows, and model parameters
- Master 6 prompt engineering patterns (few-shot, CoT, personas, JSON mode, multi-turn, LangChain templates)
- Build an evaluation toolkit: rubrics, LLM-as-Judge, sklearn metrics, G-Eval, and A/B testing
- Integrate all Day 1 concepts into end-to-end consulting AI pipelines

**Prerequisites & Setup Checklist:**
- [ ] Python 3.10+ installed
- [ ] `OPENAI_API_KEY` set in `.env` file
- [ ] Packages installed: `openai tiktoken matplotlib scikit-learn langchain langchain-openai langchain-core python-dotenv`
- [ ] Jupyter environment running (JupyterLab, VS Code, or Colab)
- [ ] Verify setup: `python -c "import openai; print(openai.__version__)"`

---

## Timetable

| Time | Duration | Activity |
|------|----------|----------|
| 09:00 -- 10:30 | 90 min | **Session 1:** Modern LLM Foundations |
| 10:30 -- 10:45 | 15 min | Break |
| 10:45 -- 12:15 | 90 min | **Session 2:** Prompt Engineering |
| 12:15 -- 13:15 | 60 min | Lunch Break |
| 13:15 -- 14:45 | 90 min | **Session 3:** Model Evaluation |
| 14:45 -- 15:00 | 15 min | Break |
| 15:00 -- 16:30 | 90 min | **Session 4:** Lab Review & Integration |
| 16:30 -- 17:00 | 30 min | Wrap-up & Q&A |

---

## Session 1: Modern LLM Foundations (09:00 -- 10:30)

### Notebooks
- **Demo:** `Day1-Foundations-Prompting-Evaluation/Session1-LLM-Foundations/D1S1_demos.ipynb`
- **Exercises:** `Day1-Foundations-Prompting-Evaluation/Session1-LLM-Foundations/D1S1_exercises.ipynb`

### Demo Walkthrough (45 min)

| Demo | Topic | Key Talking Points | Time |
|------|-------|--------------------|------|
| 1 | Setting Up LLM API Connections | Initialize OpenAI client, make first chat completion, explain `finish_reason` (`stop` vs `length`) | 5 min |
| 2 | Tokenization & Context Windows | `tiktoken` encoder, token-to-character ratios, context window sizes (128K for gpt-4o-mini), cost implications | 8 min |
| 3 | Model Parameters | Temperature (0 = deterministic, 1 = creative), `top_p` (nucleus sampling), `max_tokens` truncation. Run all 3 sub-demos (3a-3c) | 10 min |
| 4 | System Messages & Personas | 3 McKinsey personas (Strategy Partner, Operations Associate, Digital Expert) answering the same question -- show how system messages steer output | 7 min |
| 5 | LLM Pipeline | `call_llm` helper, 2-step pipeline: summarize -> extract key insights. Emphasize decomposition over mega-prompts | 8 min |
| 6 | Embeddings (Narrative) | Conceptual overview only -- embeddings are covered hands-on in Day 3 RAG session | 2 min |
| 7 | LLM Reasoning Capabilities | 4 sub-demos: Task Decomposition (MECE), Planning (engagement plan), Self-Reflection (partner review), Tool Selection (consulting tools) | 5 min |

**Delivery Tips:**
- Demo 1: Have students run the cell alongside you. If anyone gets an API key error, fix it immediately -- this blocks everything else.
- Demo 3: Run temperature=0 twice to show determinism. Ask: "Would you use this for a financial report or a brainstorm?"
- Demo 4: This is a "wow moment" -- same model, same question, 3 completely different analyses. Pause and let students absorb.
- Demo 7: Move quickly through sub-demos; the goal is to show *capabilities*, not deep-dive. These become hands-on on Day 2.

### Exercise Facilitation (45 min)

| Exercise | Title | Difficulty | Time | What to Evaluate |
|----------|-------|------------|------|------------------|
| 1 | Simple Conversational Agent | Easy (Required) | 15 min | Message history grows correctly; Turn 2 remembers Turn 1 context |
| 2 | Token Budget Calculator | Easy (Required) | 10 min | Correct math: `available = max_context - reserved`, `fits = remaining >= 0` |
| 3 | Parameter Advisor | Easy (Required) | 10 min | Two new presets added (classification, creative_writing) + default fallback |
| 4 | Multi-Persona Pipeline | Intermediate (Optional) | -- | Loop through personas, collect responses, synthesize |
| 5 | Self-Improving Response | Intermediate (Optional) | -- | 3-step chain: generate -> critique -> improve |
| 6 | Token-Aware Summarization | Intermediate (Optional) | -- | Auto-compression when history exceeds 70% of context window |

### Skippable Exercises
- **Exercises 4, 5, 6** (all Intermediate/Optional) -- skip if short on time. Exercise 1-3 cover all core concepts.

### Common Student Mistakes
- **API key not set:** `AuthenticationError` -- check `.env` file exists and `load_dotenv()` was called
- **Exercise 1 TODO 2:** Students write `reply = response.message.content` instead of `response.choices[0].message.content`
- **Exercise 2:** Confusing `max_context` with `available` budget -- remind them to subtract `reserved_for_response` first
- **Cell execution order:** Students skip the imports/setup cell and get `NameError: name 'openai' is not defined`

### Engagement Questions
1. "You're building a tool that generates financial reports for clients. What temperature should you use and why?"
2. "A partner complains the AI summary 'cuts off mid-sentence.' What's the most likely cause, and where in the response object would you confirm it?"
3. "Why is chaining two focused LLM calls better than one mega-prompt?"

---

## Session 2: Prompt Engineering (10:45 -- 12:15)

### Notebooks
- **Demo:** `Day1-Foundations-Prompting-Evaluation/Session2-Prompt-Engineering/D1S2_demos.ipynb`
- **Exercises:** `Day1-Foundations-Prompting-Evaluation/Session2-Prompt-Engineering/D1S2_exercises.ipynb`

### Demo Walkthrough (45 min)

| Demo | Topic | Key Talking Points | Time |
|------|-------|--------------------|------|
| 1 | Zero-Shot vs Few-Shot | Compare classification with/without examples. Few-shot = implicit output schema. Show the dramatic format improvement | 7 min |
| 2 | Chain-of-Thought Prompting | Market sizing problem: without CoT (may get wrong answer) vs with CoT (step-by-step = correct). Caveat: CoT can overthink simple tasks | 8 min |
| 3 | Role-Based Personas | 3 new personas (Growth Strategy, Risk & Compliance, Org & People) on a banking question. Builds on S1 Demo 4 | 7 min |
| 4 | JSON Structured Output | `response_format={"type": "json_object"}` for client profile extraction. Parse with `json.loads()`. Gotcha: valid JSON != correct schema | 8 min |
| 5 | Multi-Turn Conversation | `ConversationManager` class. 3-turn insurance engagement planning. Show history length growing | 5 min |
| 6 | LangChain Templates | Part A: `ChatPromptTemplate` with variables. Part B: Pydantic `EngagementSummary` model + `JsonOutputParser`. Part C: Chain `prompt | llm | parser` | 10 min |

**Delivery Tips:**
- Demo 1: Run zero-shot first, then few-shot. Ask: "Which would you trust in a production pipeline?"
- Demo 2: Let students predict the answer before running CoT. The step-by-step reveal is more impactful.
- Demo 4: Emphasize the gotcha -- JSON mode guarantees valid JSON but NOT schema compliance. This is why Demo 6B uses Pydantic.
- Demo 6: This is the bridge to Day 2. Emphasize that `prompt | llm | parser` is the core abstraction behind every LangChain agent.

### Exercise Facilitation (45 min)

| Exercise | Title | Difficulty | Time | What to Evaluate |
|----------|-------|------------|------|------------------|
| 1 | Design Effective System Prompts | Easy (Core) | 15 min | Fill in blanks: "MECE frameworks", "data and evidence". Agent returns structured response with all 5 sections |
| 2 | Few-Shot Feedback Classifier | Easy (Core) | 15 min | Add 4 missing few-shot examples (1 OPERATIONS, 1 DELIVERY, 2 COMMUNICATION). Test classifies all 5 correctly |
| 3 | Chain-of-Thought Market Sizing | Easy (Core) | 10 min | Uncomment the API call block, remove `pass`. Response shows step-by-step TAM/SAM/SOM |
| 4 | Multi-Turn Research Agent | Intermediate (Optional) | -- | ResearchConversationManager with `send()` and `send_json()` methods |
| 5 | Prompt Template Library | Intermediate (Optional) | -- | 3 LangChain template functions with Pydantic output models |
| 6 | Auto-Prompt Optimizer | Intermediate (Optional) | -- | Meta-learning pipeline: run -> evaluate -> optimize -> re-test |

### Skippable Exercises
- **Exercises 4, 5, 6** (all Intermediate/Optional) -- skip if short on time. Exercises 1-3 cover few-shot, CoT, and system prompt design.

### Common Student Mistakes
- **Exercise 1:** Students over-engineer the blank fills. Keep it simple: "MECE" and "data"/"evidence"
- **Exercise 2:** Students forget that each few-shot example needs TWO messages (user + assistant). A single message won't work
- **Exercise 3:** Students try to rewrite the function instead of just uncommenting the provided code
- **LangChain import errors:** If students didn't run `pip install langchain langchain-openai`, Demo 6 and Optional Exercise 5 will fail

### Engagement Questions
1. "When would you use zero-shot vs few-shot? Give a consulting scenario for each."
2. "A colleague says 'CoT always makes responses better.' Do you agree? Why or why not?"
3. "What's the risk of using JSON mode without Pydantic validation?"

---

## Session 3: Model Evaluation (13:15 -- 14:45)

### Notebooks
- **Demo:** `Day1-Foundations-Prompting-Evaluation/Session3-Evaluation/D1S3_demos.ipynb`
- **Exercises:** `Day1-Foundations-Prompting-Evaluation/Session3-Evaluation/D1S3_exercises.ipynb`

### Demo Walkthrough (45 min)

| Demo | Topic | Key Talking Points | Time |
|------|-------|--------------------|------|
| 1 | Evaluation Rubrics | 5 consulting-grade criteria (strategic relevance, analytical rigor, MECE structure, actionability, executive readiness) scored 1-5 | 5 min |
| 2 | LLM-as-a-Judge | `llm_judge()` function returns JSON scores + reasoning. The judge LLM evaluates another LLM's output | 8 min |
| 3 | Benchmarking Across Models | Side-by-side quality/latency/token comparison at T=0, T=0.7, T=1.0 | 7 min |
| 4 | Latency & Cost Analysis | Per-token cost estimation. Pricing table: gpt-4o-mini vs gpt-4o | 5 min |
| 5 | A/B Testing Framework | `ABTestFramework` class for controlled experiments between two model configs | 7 min |
| 6 | Sklearn Metrics | LLM-based sentiment classification evaluated with precision, recall, F1, confusion matrix | 8 min |
| 7 | G-Eval (LLM + CoT Scoring) | Research-backed (arXiv 2303.16634) chain-of-thought evaluation for Coherence, Fluency, Relevance | 5 min |

**Delivery Tips:**
- Demo 2: Explain that "LLM-as-Judge" is a standard industry pattern. The judge uses a rubric to score, just like a partner reviewing an associate's work.
- Demo 4: Walk through the cost math slowly. Students are often surprised by how cheap gpt-4o-mini is.
- Demo 6: This bridges ML fundamentals (precision/recall) with LLM evaluation. If students are unfamiliar with confusion matrices, spend an extra minute.
- Demo 7: Mention the G-Eval paper briefly but don't deep-dive into the research. Focus on the practical pattern: CoT scoring.

### Exercise Facilitation (45 min)

| Exercise | Title | Difficulty | Time | What to Evaluate |
|----------|-------|------------|------|------------------|
| 1 | Custom Rubric | Easy (Core) | 12 min | 3 criteria provided, student adds 2 more (e.g., client_readiness, recommendation_quality) |
| 2 | LLM Judge | Easy (Core) | 15 min | `custom_judge()` function using the student's rubric; test on high-quality vs mediocre responses |
| 3 | Classification Metrics | Easy (Core) | 13 min | Sklearn eval of LLM doc classifier across 5 consulting document types |
| 4 | A/B Test Runner | Intermediate (Optional) | -- | `run_ab_test()` with scoring and winner determination |
| 5 | G-Eval Implementation | Intermediate (Optional) | -- | `g_eval_actionability()` chain-of-thought scorer |
| 6 | End-to-End Pipeline | Intermediate (Optional) | -- | `evaluate_ai_system()` combining generation + LLM judge + G-Eval |

### Skippable Exercises
- **Exercises 4, 5, 6** (all Intermediate/Optional) -- skip if short on time. Exercises 1-3 build the core evaluation skills.

### Common Student Mistakes
- **Exercise 1:** Students define vague rubric criteria. Push for specificity: "What does a score of 5 look like vs a score of 1?"
- **Exercise 2:** The LLM judge returns inconsistent JSON. Remind students to use `response_format={"type": "json_object"}`
- **Exercise 3:** Confusion between macro/micro averaging in sklearn. Explain: macro = equal weight per class, micro = equal weight per sample
- **matplotlib not installed:** Confusion matrix visualization fails. Run `pip install matplotlib`

### Engagement Questions
1. "If you were evaluating an AI system for a client, which 3 criteria would be most important and why?"
2. "What are the limitations of using an LLM to judge another LLM's output?"
3. "A model scores 95% precision but only 60% recall. What does that mean in practice for a document classifier?"

---

## Session 4: Lab Review & Integration (15:00 -- 16:30)

### Notebooks
- **Demo:** `Day1-Foundations-Prompting-Evaluation/Session4-Lab-Review-Integration/D1S4_demos.ipynb`
- **Exercises:** `Day1-Foundations-Prompting-Evaluation/Session4-Lab-Review-Integration/D1S4_exercises.ipynb`

### Demo Walkthrough (35 min)

| Demo | Topic | Key Talking Points | Time |
|------|-------|--------------------|------|
| 1 | End-to-End Consulting Pipeline | `consulting_pipeline()`: generate response -> G-Eval scoring on 3 criteria -> verdict (PARTNER-READY / NEEDS REVISION / REWORK) with bar chart | 12 min |
| 2 | Cost-Quality Trade-off Analysis | Same query at 3 configs (Fast/Cheap, Standard, Creative). Compare quality score, latency, tokens, cost side-by-side in a DataFrame | 12 min |
| 3 | Day 2 Preview: Raw API vs LangChain | Same task done with raw OpenAI API (Day 1 style) vs LangChain LCEL chain with parameterized prompts. Bridge to Day 2 | 11 min |

**Delivery Tips:**
- Demo 1: This is the "capstone moment" for Day 1. Show how everything connects: API call (S1) + system prompt (S2) + G-Eval (S3) = production pipeline.
- Demo 2: Let students vote on which config they'd choose before revealing the cost-quality trade-off.
- Demo 3: This is the hook for Day 2. Show that LangChain reduces boilerplate. Don't go deep -- just tease.

### Exercise Facilitation (55 min)

| Exercise | Title | Difficulty | Time | What to Evaluate |
|----------|-------|------------|------|------------------|
| 1 | Consulting Deliverable Generator | Easy (Core) | 20 min | `generate_deliverable()` with persona selection from 4 practice areas, auto-evaluation via `g_eval_quick`, cost estimation |
| 2 | Multi-Persona Comparison | Easy (Core) | 20 min | `compare_perspectives()` generates responses from 4 personas, ranks in DataFrame, recommends strongest |
| 3 | AI Readiness Assessment | Intermediate (Optional) | -- | `readiness_assessment()` runs test suite of 4 consulting categories, scores each, produces READY/CONDITIONAL/NOT READY |
| 4 | System Architecture Design | Intermediate (Optional) | -- | Complete a `system_design` spec dict documenting AI system components, configs, quality thresholds |

### Skippable Exercises
- **Exercises 3, 4** (Intermediate/Optional) -- skip if short on time. Exercises 1-2 integrate all Day 1 concepts.

### Common Student Mistakes
- **Exercise 1:** Students forget to include cost estimation -- it's easy to miss among all the other requirements
- **Exercise 2:** DataFrame construction issues. Remind students: `pd.DataFrame(list_of_dicts)` is the easiest pattern
- **General:** By Session 4, students are fatigued. Keep energy high by celebrating progress: "You've built an evaluation pipeline from scratch today!"

### Engagement Questions
1. "Looking at the cost-quality trade-off, when would you choose the cheap/fast model over the expensive one?"
2. "How would you explain the value of automated evaluation to a non-technical partner?"
3. "What's one thing from today that surprised you about working with LLMs?"

---

## Best Practices for Day 1

### General Delivery Tips
- **Live-code, don't just run cells.** Explain what each line does as you run it. Students learn more from watching you think through the code than from seeing output appear.
- **Use the "Try This" prompts.** Each demo has a "Try This" suggestion (e.g., add a 4th persona, change the text). Use at least 2-3 of these to show experimentation.
- **Run temperature=0 twice** in Demo 3 to prove determinism. This is a reliable "aha" moment.
- **Reference the recap questions** built into the demo notebooks. They're designed as natural pause points.

### Handling API Rate Limits / Errors
- If you hit a rate limit (`429 Too Many Requests`): wait 30 seconds and retry. Explain to students that rate limits are normal in production.
- If the API is slow: use the wait time to discuss caching strategies (previewed in Day 3 Session 2).
- If `AuthenticationError`: check `OPENAI_API_KEY` in `.env`. Have a backup key ready.

### Pacing Guidance
- **Sessions 1-2** are the most demo-heavy. Aim for a 50/50 split between demos and exercises.
- **Session 3** has 7 demos -- move briskly through Demos 3-5 (benchmarking, cost, A/B) to leave time for exercises.
- **Session 4** is lighter on demos (only 3). Use the extra time for exercises and Q&A.
- If running behind: skip all Intermediate/Optional exercises across all sessions. The 11 Easy/Required exercises cover all core concepts.

---

## Troubleshooting

### Common Environment Issues

| Issue | Symptom | Fix |
|-------|---------|-----|
| API key not set | `AuthenticationError: No API key provided` | Create `.env` file with `OPENAI_API_KEY=sk-...` in project root. Ensure `load_dotenv()` runs first |
| Missing packages | `ModuleNotFoundError: No module named 'tiktoken'` | Run the `!pip install -q ...` cell at the top of each notebook |
| Kernel not restarted | Stale variables from a previous run causing unexpected behavior | Kernel -> Restart & Run All |
| tiktoken version mismatch | Token counts differ slightly from expected output | This is normal. Mention that exact counts may vary by version |
| LangChain import error | `ModuleNotFoundError: No module named 'langchain_openai'` | `pip install langchain langchain-openai langchain-core` |
| matplotlib backend | Plot doesn't display in notebook | Add `%matplotlib inline` at top of notebook |

### Notebook-Specific Gotchas

| Notebook | Gotcha |
|----------|--------|
| D1S1_demos | Demo 6 (Embeddings) is narrative-only -- no code to run. Don't search for runnable cells. |
| D1S1_exercises | Exercise 1 test cell is commented out. Students must uncomment before running. |
| D1S2_demos | Demo 6 requires `langchain`, `langchain-openai`, and `langchain-core`. If not installed, only Demo 6 fails -- Demos 1-5 work fine with just `openai`. |
| D1S2_exercises | Exercise 3 is the simplest -- just uncomment code. If students are stuck, start here for a confidence boost. |
| D1S3_demos | Demo 6 uses `sklearn.metrics`. If `scikit-learn` isn't installed, the confusion matrix won't render. |
| D1S3_exercises | Exercise 3 requires 5 document category labels -- students sometimes invent a 6th category. Stick to the 5 provided. |
| D1S4_demos | Demo 3 is the Day 2 preview. Don't over-explain LangChain -- just show the contrast. |
| D1S4_exercises | Exercise 2 builds a pandas DataFrame. Students unfamiliar with pandas may need help with `pd.DataFrame()`. |
