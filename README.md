# ReAct-AI

A ReAct (Reasoning + Acting) AI agent built with LangGraph and Gemini 2.5 Flash 
that autonomously reasons, selects tools, and chains them to solve multi-step problems.

## What it does
- Solves multi-step problems by chaining multiple tools together
- Exposes the full Thought → Action → Observation loop via LangGraph streaming
- Handles inconsistent LLM response formats gracefully

## Tech Stack
- LangGraph — agent graph orchestration
- Google Gemini 2.5 Flash — LLM backbone
- LangChain Core — tool definitions and message handling

## Tools
| Tool | Description |
|------|-------------|
| Calculator | Evaluates math expressions |
| Word Counter | Counts words in any text |
| Reverse Text | Reverses any string |

## Key Concept
The agent never directly answers — it reasons about the problem, picks the right 
tool, observes the output, and loops until confident. This is the foundation of 
how production AI agents work.

## Challenges
- **Rate limits** — Gemini 2.5 Flash free tier allows 5 RPM and 20 RPD. Added 
  delays between calls to handle this gracefully.
- **Inconsistent response formats** — Gemini 2.5 returns content as either a 
  plain string or a list of typed blocks. Wrote defensive parsing to handle both.
