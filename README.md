# n8n-autonomous-market-research-agent
# 🤖 Autonomous n8n workflow for competitive intelligence using AI Agents.

This project demonstrates a production-grade AI Agent workflow built using n8n for automated competitive intelligence and strategic analysis.

**Problem Solved:** Elimination of manual, expensive, and biased competitor research processes.

## Architecture & Features

### 1. The Autonomous Core (Agentic Logic)
The workflow employs a **Google Gemini Pro AI Agent** that acts as a Senior Market Analyst. The Agent is configured with specialized tools and logic to:
* **Dynamic Tool Calling:** Autonomously decide whether to use the Web Research tool or the Internal RAG tool based on the prompt.
* **Structured Output:** Forced JSON generation to ensure clean data for downstream services.

### 2. Modular Tooling (Sub-Workflows)
The Agent interacts with two key internal sub-workflows (Tools):
* **Web Research Tool:** Simulates real-time public data gathering.
* **Internal RAG Tool:** Simulates accessing proprietary, historical business context.

### 3. Data Flow & Result
The system processes competitors in a loop, parses the LLM output using JavaScript with null-check error handling, and routes the final data to Slack for immediate alerting and Google Sheets for audit logging.



## Files in this Repository

* `autonomous_research_agent.json`: The sanitized n8n workflow file.
* `README.md`: This document.

## How to Run Locally

1.  Install n8n (or use n8n Cloud).
2.  Import the `autonomous_research_agent.json` file.
3.  Configure the **Gemini API Key** and Slack/Google Sheets credentials.
4.  Execute the Schedule Trigger.
