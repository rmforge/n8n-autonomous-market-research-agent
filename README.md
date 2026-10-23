# n8n-autonomous-market-research-agent

> **Reference build:** a public demo of a pattern. The data sources are simulated, and this is not a client deployment.

An n8n workflow that uses an AI agent for competitive intelligence: it researches a list of competitors and routes a structured brief to Slack and Google Sheets.

**Problem addressed:** manual competitor research is slow, costly and open to bias. This workflow shows how an agent can do the research and formatting, so a person only reads the finished brief.

## Architecture and features

### 1. The agent core
A Google Gemini Pro AI agent acts as a senior market analyst. It is configured with specialized tools and logic to:

* **Dynamic tool calling:** decide on its own whether to use the web research tool or the internal RAG tool, based on the prompt.
* **Structured output:** produce forced JSON, so the data is clean for downstream steps.

### 2. Modular tools (sub-workflows)
The agent uses two internal sub-workflows as tools:

* **Web research tool:** simulates real-time public data gathering.
* **Internal RAG tool:** simulates access to proprietary, historical business context.

### 3. Data flow and result
The workflow processes competitors in a loop, parses the model output with JavaScript that includes null-check error handling, and routes the result to Slack for immediate alerting and to Google Sheets for audit logging.

## Files in this repository

* `autonomous_research_agent.json`: the sanitized n8n workflow file.
* `README.md`: this document.

## How to run locally

1. Install n8n (or use n8n Cloud).
2. Import the `autonomous_research_agent.json` file.
3. Configure the Gemini API key and the Slack and Google Sheets credentials.
4. Execute the Schedule Trigger.
