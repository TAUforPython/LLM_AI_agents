# LLM AI Agents: 13 Practical Lessons & Architectures

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)

This repository is a structured, hands-on course for building **production-ready AI agents**. It moves from basic LLM inference to advanced techniques like **Multi-Agent coordination**, **MCP tools integration**, **HyDE retrieval**, and **DSPy components** — all with a focus on the **Mistral API** and practical healthcare-focused examples (e.g., clinical guideline verification).

## What You'll Learn

| Lesson | Topic | Key Technique / Tool |
|--------|-------|----------------------|
| 1-2 | Basic & Llama inference | Mistral, OpenAI, Llama |
| 3 | Simple agents | LangChain |
| 4 | **MCP Tools** | Model Context Protocol |
| 5 | Memory & Guardrails | Conversation buffers, content safety |
| 6 | **Multi-Agent** | Critic + Coordinator pattern |
| 7 | Answer scoring | Automated evaluation metrics |
| 8 | **RAG techniques** | Naive, advanced, and query transformations |
| 9 | **DSPy components** | Programmatic LM pipelines |
| 10 | **TAO** (Think-Act-Observe) | ReAct-like loop with Mistral |
| 11-13 | Applied projects | Medical claims, fact-checking, **HyDE** for clinical guidelines |

> All notebooks are fully executable and include API setup instructions (Mistral / OpenAI).

## Core Theoretical Concepts

### 1. Large Language Models (LLMs) as Agent Brains
LLMs (like Mistral, Llama, GPT) act as the reasoning engine of an agent. They don't just generate text — they:
- **Plan** (break down goals into steps)
- **Use tools** (via API calls)
- **Reflect** (evaluate their own outputs)
- **Remember** (short-term and long-term memory)

In this repo, you'll see how to switch between different LLM providers and how to control their “temperature,” system prompts, and structured outputs.

### 2. MCP – Model Context Protocol  
**MCP** (Model Context Protocol) is a standardized way to give LLMs **live access to external tools and data sources**. Instead of hard-coding each API, MCP defines:
- **Resources** (files, databases, web APIs)
- **Tools** (functions the LLM can call)
- **Prompts** (reusable templates)

**Why it matters:**  
Without MCP, an agent is a static text generator. With MCP, it can query a database, call a calculator, fetch a webpage, or send an email — all using a consistent interface.  
*Lesson 4 (`lesson-4_MCP_tools.ipynb`) demonstrates MCP integration with Mistral.*

### 3. HyDE – Hypothetical Document Embeddings  
**HyDE** is a retrieval technique that solves a common RAG problem: the user’s query might not match the wording of relevant documents.

**How it works:**
1. Given a user query, ask the LLM to **generate a hypothetical answer** (even if wrong).
2. Embed that **hypothetical answer**, not the original query.
3. Use that embedding to retrieve real documents.

**Why it works:**  
The hypothetical answer is semantically closer to actual relevant documents than the original short query is.  
*See `lesson-13_HyDE_Russian_Clinical_Guidelines.ipynb` for a real application with medical guidelines.*

### 4. Agent Architecture – From Simple to Multi-Agent

This repo evolved through several architectural patterns:

#### A. Basic ReAct (TAO – Think, Act, Observe)
- **Think**: LLM decides next action
- **Act**: Execute tool / API call
- **Observe**: Feed result back to LLM  
*(Lesson 10)*

#### B. Single Agent with Memory & Guardrails
- Short-term memory (conversation buffer)
- Long-term memory (vector store)
- Guardrails (block unsafe outputs, limit loops)  
*(Lesson 5)*

#### C. Multi-Agent Systems (Critic + Coordinator)
Instead of one LLM doing everything, you have:
- **Coordinator Agent**: Breaks down the task, delegates
- **Critic Agent**: Checks the work of other agents for errors, consistency, or bias
- **Worker Agents**: Execute subtasks

This pattern improves reliability, especially in high-stakes domains like medical claim verification or clinical fact-checking.  
*(Lessons 6, 11, 12)*

## Repository Structure

```
LLM_AI_agents/
├── lesson-1_LLM_base_inference.ipynb      # Mistral & OpenAI setup
├── lesson-2_Llama_example_inference.ipynb
├── lesson-3_simple_agent_Langchain.ipynb
├── lesson-4_MCP_tools.ipynb               # Model Context Protocol
├── lesson-5_Memory_and_Guardrails_Agents.ipynb
├── lesson-6_MultyAgent_Critical_and_Coordinator.ipynb
├── lesson-7_Score_Agent_Answer.ipynb
├── lesson-8_Different_RAG_techniques.ipynb
├── lesson-9_DSPy_components.ipynb
├── lesson-10_TAO_think_act_observe_techniques.ipynb
├── lesson-11_LLM_Agent_Graph_Verdict_Medical_Claims.ipynb
├── lesson-12_AI_agent_fact_cheking_Digital_Clinical_Requirements.ipynb
├── lesson-13_HyDE_Russian_Clinical_Guidelines.ipynb
├── README.md
└── LICENSE
```

##  Quick Start

1. **Clone the repo** or make Fork
   ```bash
   git clone https://github.com/D2718281828nis/LLM_AI_agents.git
   cd LLM_AI_agents
   ```

2. **Set up environment**  
   Create a virtual environment and install:
   ```bash
   pip install mistralai langchain openai dspy chromadb jupyter
   ```

3. **Add your API keys**  
   Create a `.env` file or set environment variables:
   ```text
   MISTRAL_API_KEY=your_key_here
   OPENAI_API_KEY=your_key_here   (if using OpenAI)
   ```

4. **Run the notebooks** in order, starting with `lesson-1_LLM_base_inference.ipynb`.

## Contributing

Contributions are welcome! Please follow:
- **Coding standards**: Keep notebooks clean, add comments for key steps.
- **Process**: Open an issue first for major changes, then submit a PR.
- **New lessons**: Should include a practical use case and theory explanation.


## Acknowledgements

- Built with [Mistral AI](https://mistral.ai/) and [LangChain](https://www.langchain.com/)
- HyDE inspired by Gao et al. (2022) – "Precise Zero-Shot Dense Retrieval without Relevance Labels"
- MCP based on Anthropic’s Model Context Protocol specification

---

**Start with Lesson 1 → then jump to Lesson 4 (MCP) or Lesson 13 (HyDE) for advanced techniques.**
```
