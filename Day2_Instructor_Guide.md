# Day 2 Instructor Guide: LangChain, LangGraph & Multi-Agent Systems

## Overview

**Theme:** Progress from raw API engineering to framework-based development -- building chains, graphs, and multi-agent systems that plan, use tools, and self-correct.

**Learning Objectives:**
- Master advanced OpenAI API patterns: streaming, function calling, Pydantic validation, and structured extraction pipelines
- Build composable chains with LangChain's LCEL (prompt | llm | parser), custom tools, and simple RAG
- Design stateful workflows with LangGraph: linear, conditional, iterative, ReAct, and human-in-the-loop
- Architect multi-agent systems: supervisor-worker, handoff, parallel fan-out/fan-in, and collaborative patterns

**Prerequisites & Setup Checklist:**
- [ ] All Day 1 prerequisites still in place
- [ ] Additional packages: `langchain langchain-openai langchain-core langchain-text-splitters langgraph pydantic`
- [ ] `OPENAI_API_KEY` set in `.env`
- [ ] Verify: `python -c "import langgraph; print('LangGraph OK')"`

---

## Timetable

| Time | Duration | Activity |
|------|----------|----------|
| 09:00 -- 10:30 | 90 min | **Session 1:** Advanced OpenAI API & Structured Outputs |
| 10:30 -- 10:45 | 15 min | Break |
| 10:45 -- 12:15 | 90 min | **Session 2:** LangChain Development & Tool Integration |
| 12:15 -- 13:15 | 60 min | Lunch Break |
| 13:15 -- 14:45 | 90 min | **Session 3:** LangGraph Orchestration & Workflow Design |
| 14:45 -- 15:00 | 15 min | Break |
| 15:00 -- 16:30 | 90 min | **Session 4:** Multi-Agent Workflows & Agentic Systems |
| 16:30 -- 17:00 | 30 min | Wrap-up & Q&A |

---

## Session 1: Advanced OpenAI API & Structured Outputs (09:00 -- 10:30)

### Notebooks
- **Demo:** `Day2-LangChain-LangGraph-Multi-Agent/Session1-Advanced-API/D2S1_demos.ipynb`
- **Exercises:** `Day2-LangChain-LangGraph-Multi-Agent/Session1-Advanced-API/D2S1_exercises.ipynb`

### Demo Walkthrough (45 min)

| Demo | Topic | Key Talking Points | Time |
|------|-------|--------------------|------|
| 1 | Streaming & Token Usage | 1a: Token usage tracking (prompt vs completion tokens, cost awareness). 1b: Streaming responses (real-time output, `stream=True`) | 10 min |
| 2 | JSON Mode: Client Profile Extraction | `response_format={"type": "json_object"}`. Parse with `json.loads()`. Bridge from Day 1 Demo 4 to production-grade extraction | 8 min |
| 3 | Function Calling | 3a: Define tools schema + simulated function. 3b: Initial API call (model decides to call function). 3c: Execute function, send result back. This is the core of agentic tool use | 12 min |
| 4 | Pydantic Validation | 4a: Define `EngagementSummary` BaseModel. 4b: Request structured output + validate against schema. Pydantic catches what JSON mode misses | 8 min |
| 5 | Structured Data Extraction Pipeline | 5a: `TeamMember` model + extraction function. 5b: Test the pipeline. End-to-end: unstructured text -> validated structured data | 7 min |

**Delivery Tips:**
- Demo 1b (Streaming): Show the text appearing word-by-word in real time. This is a visual "wow" moment. Ask: "Why would a chatbot use streaming?"
- Demo 3: This is the most important demo of the session. Walk through the 3-step flow slowly: (1) model decides to call function, (2) you execute it, (3) you send the result back. This is how all tool-using agents work.
- Demo 4: Show what happens when the LLM returns a field with the wrong type. Pydantic catches it. Ask: "Why is this better than just checking keys manually?"
- Demo 5: Frame this as a production pattern -- "This is how you'd extract team data from engagement notes at scale."

### Exercise Facilitation (45 min)

| Exercise | Title | Difficulty | Time | What to Evaluate |
|----------|-------|------------|------|------------------|
| 1 | Financial Analysis Tool with Function Calling | Easy | 15 min | Define tool schema, handle function call response, send result back |
| 2 | Streaming Response Collector with Token Counter | Easy | 12 min | Collect streamed chunks, count tokens, display running total |
| 3 | Multi-Tool Financial Advisor | Easy | 13 min | Multiple tools registered, model selects the right one per query |
| 4 | Validated Data Pipeline | Intermediate (Optional) | -- | JSON mode + Pydantic validation combined |
| 5 | Auto-Retry with Schema Correction | Intermediate (Optional) | -- | Retry on validation failure with error feedback |
| 6 | Multi-Step Tool Orchestrator | Intermediate (Optional) | -- | Chain multiple tool calls sequentially |

### Skippable Exercises
- **Exercises 4, 5, 6** (all Intermediate/Optional) -- skip if short on time. Exercises 1-3 cover function calling, streaming, and multi-tool selection.

### Common Student Mistakes
- **Exercise 1:** Students define the function schema but forget to handle the `tool_calls` response -- they try to read `message.content` instead of `message.tool_calls`
- **Exercise 2:** Streaming chunks don't have `choices[0].delta.content` on every chunk (the first chunk may be empty). Students need a `None` check
- **Exercise 3:** Students register multiple tools but the model doesn't call the expected one. Explain that tool descriptions matter -- better descriptions = better tool selection
- **General:** `from pydantic import BaseModel` vs `from pydantic.v1 import BaseModel` -- LangChain historically used v1. Ensure students use standard Pydantic

### Engagement Questions
1. "You're building a client-facing chatbot. Why would you use streaming instead of waiting for the full response?"
2. "The model decides to call the wrong function. What can you change to fix this without changing the model?"
3. "What's the difference between JSON mode and Pydantic validation? When would you use both together?"

---

## Session 2: LangChain Development & Tool Integration (10:45 -- 12:15)

### Notebooks
- **Demo:** `Day2-LangChain-LangGraph-Multi-Agent/Session2-LangChain/D2S2_demos.ipynb`
- **Exercises:** `Day2-LangChain-LangGraph-Multi-Agent/Session2-LangChain/D2S2_exercises.ipynb`

### Demo Walkthrough (45 min)

| Demo | Topic | Key Talking Points | Time |
|------|-------|--------------------|------|
| 1 | LangChain Basics | 1a: `ChatOpenAI` + simple invoke. 1b: Message objects (`HumanMessage`, `SystemMessage`). 1c: `ChatPromptTemplate` with variables | 10 min |
| 2 | LCEL Chains (Pipe Operator) | 2a: Simple chain `prompt | llm | StrOutputParser`. 2b: JSON output chain. 2c: Multi-step chain (summarize -> translate). The `|` operator is the key abstraction | 10 min |
| 3 | Custom Tools | 3a: Define 3 tools using `@tool` decorator. 3b: Inspect tool metadata. 3c: Bind tools to LLM with `llm.bind_tools()` | 10 min |
| 4 | Document Loading & Text Splitting | 4a: Create sample `Document` objects. 4b: `RecursiveCharacterTextSplitter` with chunk size and overlap | 8 min |
| 5 | Simple RAG Pipeline | 5a: Knowledge base + retrieval function. 5b: RAG chain (retrieve context -> generate answer). Bridge to Day 3 full RAG | 7 min |

**Delivery Tips:**
- Demo 1: Explicitly contrast with Day 1's raw `openai.OpenAI()` calls. Ask: "What's the advantage of `ChatOpenAI` over the raw client?"
- Demo 2: The `|` pipe operator is the single most important concept. Show that `prompt | llm | parser` is readable and composable. Draw the data flow on a whiteboard if possible.
- Demo 3: The `@tool` decorator is magic -- it auto-generates the schema from the function signature and docstring. Show the metadata output.
- Demo 5: Keep this brief. The goal is to show the RAG pattern conceptually. Day 3 S1 covers RAG in depth with ChromaDB.

### Exercise Facilitation (45 min)

| Exercise | Title | Difficulty | Time | What to Evaluate |
|----------|-------|------------|------|------------------|
| 1 | Custom Consulting Tools | Easy | 15 min | Define tools with `@tool`, bind to LLM, show tool selection |
| 2 | LCEL Analysis Pipeline | Easy | 15 min | Multi-step chain with different output parsers at each stage |
| 3 | Custom RAG with Metadata Filtering | Easy | 10 min | RAG pipeline with metadata-based document filtering |
| 4 | Tool-Augmented Chain | Intermediate (Optional) | -- | Chain that decides whether to use a tool or answer directly |
| 5 | Document Chunking Optimizer | Intermediate (Optional) | -- | Compare different chunk sizes and overlap values |
| 6 | Full RAG Pipeline with Tool Selection | Intermediate (Optional) | -- | RAG + tool use combined |

### Skippable Exercises
- **Exercises 4, 5, 6** (all Intermediate/Optional) -- skip if short on time. Exercises 1-3 cover tools, chains, and RAG basics.

### Common Student Mistakes
- **Exercise 1:** Tool docstrings are empty. LangChain uses the docstring as the tool description -- without it, the LLM can't select the right tool
- **Exercise 2:** Students try to chain incompatible types. Remind them: each `|` step must accept the output type of the previous step
- **Exercise 3:** Metadata filtering syntax confusion. Show the pattern: `filter={"key": "value"}`
- **Import confusion:** `from langchain_core.tools import tool` (lowercase `tool` decorator) vs `from langchain.tools import Tool` (uppercase class). Use the decorator pattern

### Engagement Questions
1. "How does the LCEL pipe operator `|` make your code more maintainable than manually chaining function calls?"
2. "You have a tool with a vague description and the LLM keeps picking the wrong one. What do you fix?"
3. "Why would you split documents into chunks instead of feeding the whole document to the LLM?"

---

## Session 3: LangGraph Orchestration & Workflow Design (13:15 -- 14:45)

### Notebooks
- **Demo:** `Day2-LangChain-LangGraph-Multi-Agent/Session3-LangGraph/D2S3_demos.ipynb`
- **Exercises:** `Day2-LangChain-LangGraph-Multi-Agent/Session3-LangGraph/D2S3_exercises.ipynb`

### Demo Walkthrough (45 min)

| Demo | Topic | Key Talking Points | Time |
|------|-------|--------------------|------|
| 1 | Linear Pipeline | State schema with `TypedDict`, 3 node functions, `StateGraph` construction. Consulting engagement pipeline: intake -> analyze -> recommend | 10 min |
| 2 | Conditional Routing | Routing function that returns different next nodes based on state. Route by engagement complexity (simple / complex / expert) | 10 min |
| 3 | ReAct Agent | Think -> Act -> Observe loop with simulated tools. Market research analyst that reasons about which tool to use | 10 min |
| 4 | Iterative Refinement | Generate -> Review -> Refine loop that repeats until quality threshold met. Like a partner review cycle | 8 min |
| 5 | Human-in-the-Loop | Partner sign-off gate before client delivery. Graph pauses, waits for human input, then continues | 7 min |

**Delivery Tips:**
- Demo 1: Draw the graph on a whiteboard: `intake -> analyze -> recommend -> END`. This visual helps students understand the abstraction.
- Demo 2: Ask students: "What real-world consulting workflow has conditional routing?" (e.g., triage by complexity, route by industry)
- Demo 3: This is the most complex demo. Walk through ONE iteration of Think -> Act -> Observe slowly. The loop is the key insight.
- Demo 4: Connect to Day 1 S3 (evaluation). The review node uses the same LLM-as-Judge pattern, now embedded in a graph.
- Demo 5: Emphasize that human-in-the-loop is essential for production AI. Ask: "Where in your consulting workflow would you want a human gate?"

### Exercise Facilitation (45 min)

| Exercise | Title | Difficulty | Time | What to Evaluate |
|----------|-------|------------|------|------------------|
| 1 | Client Onboarding Pipeline | Easy | 15 min | 3-node linear `StateGraph`: collect info -> validate -> create profile |
| 2 | Conditional Routing Pipeline | Easy | 15 min | Route to different analysis nodes based on engagement type |
| 3 | Iterative Report Writer | Easy | 10 min | Write -> Review -> Rewrite loop with max iterations |
| 4 | ReAct Research Agent | Intermediate (Optional) | -- | Think -> Act -> Observe with multiple tools |
| 5 | Pipeline with Human Gate | Intermediate (Optional) | -- | Graph that pauses for human approval |
| 6 | Multi-Stage Engagement Pipeline | Intermediate (Optional) | -- | Combines linear + conditional + iterative patterns |

### Skippable Exercises
- **Exercises 4, 5, 6** (all Intermediate/Optional) -- skip if short on time. Exercises 1-3 cover linear, conditional, and iterative graph patterns.

### Common Student Mistakes
- **Exercise 1:** Students forget to return the updated state dict from node functions. Every node must return `{key: value}` to update state
- **Exercise 2:** Routing function returns a node name that doesn't exist in the graph. The name must exactly match `graph.add_node("name", func)`
- **Exercise 3:** Infinite loop -- students forget to increment an iteration counter or check a termination condition
- **TypedDict confusion:** Students use regular dicts instead of `TypedDict` for the state schema. LangGraph requires typed state
- **Import:** `from langgraph.graph import StateGraph, END` -- students sometimes import from wrong package

### Engagement Questions
1. "What consulting workflow would benefit from conditional routing? Sketch it on paper."
2. "In the iterative refinement pattern, how do you decide when to stop refining?"
3. "Why is human-in-the-loop important for production AI systems? Give a real-world example where skipping it would be dangerous."

---

## Session 4: Multi-Agent Workflows (15:00 -- 16:30)

### Notebooks
- **Demo:** `Day2-LangChain-LangGraph-Multi-Agent/Session4-Multi-Agent/D2S4_demos.ipynb`
- **Exercises:** `Day2-LangChain-LangGraph-Multi-Agent/Session4-Multi-Agent/D2S4_exercises.ipynb`

### Demo Walkthrough (45 min)

| Demo | Topic | Key Talking Points | Time |
|------|-------|--------------------|------|
| 1 | Supervisor-Worker Pattern | Partner delegates to 3 associate agents. 1a: State + supervisor. 1b: 3 worker nodes + review. 1c: Routing. 1d: Test cases. Like a real engagement team hierarchy | 12 min |
| 2 | Agent Handoff | Strategy agent -> Operations agent -> Implementation agent. Sequential handoff where each agent builds on the previous one's output | 8 min |
| 3 | Parallel Execution (Fan-out/Fan-in) | 3 due diligence workstreams run in parallel, then a synthesis agent combines results. M&A scenario | 10 min |
| 4 | Collaborative Deliverable | EM creates storyline -> Associate drafts content -> Partner reviews. Engagement team building a client presentation together | 8 min |
| 5 | End-to-End Multi-Agent System | Intent classifier routes to 3 specialist agents + quality gate. Full system with intake, routing, execution, and QA | 7 min |

**Delivery Tips:**
- Demo 1: This is the most important pattern. Draw the supervisor-worker hierarchy. Ask: "How is this like a real McKinsey engagement team?"
- Demo 3: Explain fan-out/fan-in with a diagram. 3 agents run simultaneously, then a synthesis agent merges. Ask: "Why is parallel better than sequential for due diligence?"
- Demo 4: This mirrors real engagement workflow -- EM scopes, associate drafts, partner reviews. Students relate to this immediately.
- Demo 5: Run through quickly. The goal is to show how all patterns combine into a production system.

### Exercise Facilitation (45 min)

| Exercise | Title | Difficulty | Time | What to Evaluate |
|----------|-------|------------|------|------------------|
| 1 | Two-Agent Supervisor-Worker | Easy | 15 min | Supervisor routes to 2 worker agents based on query type |
| 2 | Three-Agent Handoff Pipeline | Easy | 15 min | Sequential A -> B -> C handoff with state accumulation |
| 3 | Collaborative Report Builder | Easy | 10 min | Multiple agents contribute sections to a shared report |
| 4 | Intent-Based Router with 4 Specialists | Intermediate (Optional) | -- | Classifier + 4 specialist agents |
| 5 | Parallel Analysis with Synthesis | Intermediate (Optional) | -- | Fan-out to parallel agents, fan-in to synthesis |
| 6 | Full Engagement Delivery System | Intermediate (Optional) | -- | Combines supervisor + handoff + quality gate |

### Skippable Exercises
- **Exercises 4, 5, 6** (all Intermediate/Optional) -- skip if short on time. Exercises 1-3 cover supervisor-worker, handoff, and collaborative patterns.

### Common Student Mistakes
- **Exercise 1:** Supervisor routing logic returns wrong agent name. Debug by printing the supervisor's decision before routing
- **Exercise 2:** State doesn't accumulate across handoffs. Each agent overwrites instead of appending. Use `Annotated[list, operator.add]` for list accumulation
- **Exercise 3:** Students try to run agents in parallel without proper graph structure. In LangGraph, parallel execution requires multiple edges from the same source node
- **General:** Students confuse LangGraph patterns with LangChain chains. Clarify: LangChain chains are linear pipelines; LangGraph is for branching, looping, and stateful workflows

### Engagement Questions
1. "In a real consulting engagement, who is the 'supervisor' and who are the 'workers'? How would you map your team structure to agents?"
2. "When would you use parallel execution vs sequential handoff? Give examples of each."
3. "What's the most complex multi-agent system you can envision for your work? Sketch the graph."

---

## Best Practices for Day 2

### General Delivery Tips
- **Build on Day 1 explicitly.** Start each session with: "Yesterday you learned X. Today we're wrapping that in Y." For example: "Yesterday you wrote raw `client.chat.completions.create()` calls. Today we're replacing that with `ChatOpenAI` + LCEL chains."
- **Draw graphs on a whiteboard.** LangGraph concepts are inherently visual. A 30-second sketch of `node A -> node B -> END` is worth 5 minutes of verbal explanation.
- **Show the failure first.** When demonstrating tool calling (S1 Demo 3), show what happens when the model *doesn't* have tools. Then add tools and show the improvement.
- **Keep the energy up after lunch.** Session 3 (LangGraph) is the most technically dense session. Start with the simplest pattern (linear pipeline) and build complexity gradually.

### Handling API Rate Limits / Errors
- Day 2 makes more API calls per session (multi-agent = multiple LLM calls per query). If you hit rate limits:
  - Reduce the number of test cases in demos (e.g., run 2 instead of 4)
  - Add a 1-second delay between agent calls: `import time; time.sleep(1)`
  - Switch to `gpt-4o-mini` if using a more expensive model
- If LangGraph graphs fail to compile: check that all node names in `add_edge()` match names in `add_node()`

### Pacing Guidance
- **Session 1** is a bridge from Day 1. Students should feel comfortable quickly -- the patterns are similar to yesterday.
- **Session 2** introduces LangChain. The `|` pipe operator is the key concept. If students grasp this, everything else follows.
- **Session 3** is the hardest session of Day 2. Allocate extra time if needed. Consider skipping Demo 5 (human-in-the-loop) if running behind.
- **Session 4** is the "fun" session. Multi-agent systems are exciting and students are usually engaged. Let them experiment.
- If running behind: skip all Intermediate/Optional exercises. The 12 Easy/Required exercises cover all core patterns.

---

## Troubleshooting

### Common Environment Issues

| Issue | Symptom | Fix |
|-------|---------|-----|
| LangGraph not installed | `ModuleNotFoundError: No module named 'langgraph'` | `pip install langgraph` |
| LangChain version mismatch | `ImportError: cannot import name 'tool' from 'langchain_core'` | `pip install --upgrade langchain-core langchain-openai` |
| Pydantic v1 vs v2 | `ValidationError` with unexpected format | Ensure `pydantic>=2.0`. LangChain now uses Pydantic v2 |
| StateGraph compilation error | `ValueError: Node 'X' not found` | Node name in `add_edge()` must exactly match `add_node()` |
| Tool not called | Model responds with text instead of calling the tool | Improve tool description in the docstring. Add "Always use this tool when..." |
| Streaming not working | `AttributeError: 'NoneType' object has no attribute 'content'` | First chunk's `delta.content` may be `None`. Add: `if chunk.choices[0].delta.content:` |

### Notebook-Specific Gotchas

| Notebook | Gotcha |
|----------|--------|
| D2S1_demos | Demo 3 (Function Calling) has 3 cells that must run in sequence. If students run 3c before 3b, it will fail. |
| D2S1_exercises | Exercise 2 streaming: the final chunk has `finish_reason="stop"` but no content. Students must handle this. |
| D2S2_demos | Demo 5 (RAG) uses a simple dict-based retriever, not ChromaDB. Day 3 S1 uses ChromaDB. |
| D2S2_exercises | Exercise 1: `@tool` decorator requires a docstring. Missing docstring = LangChain can't generate the tool schema. |
| D2S3_demos | Demo 3 (ReAct) uses simulated tools (not real API calls). The loop is manually controlled. |
| D2S3_exercises | Exercise 3 (Iterative Report Writer): students must set a `max_iterations` to prevent infinite loops. |
| D2S4_demos | Demo 3 (Parallel Execution): LangGraph's parallel fan-out requires adding edges from one node to multiple targets. |
| D2S4_exercises | Exercise 2 (Handoff): state must use `Annotated[list, operator.add]` for accumulation, not plain `list`. |
