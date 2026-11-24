<div align="center">

<img src="https://raw.githubusercontent.com/Studio1HQ/Studio1HQ/main/assets/banners/deep-research.webp" alt="Local Deep Research Agent with Bright Data: Private research assistant on Bright Data, Ollama and ChromaDB" width="100%" />

<br />
<br />

# Local Deep Research Agent with Bright Data

### Private research assistant on Bright Data, Ollama and ChromaDB

A Streamlit app that collects web data with Bright Data, summarizes it with a local Ollama model, and stores each research session in a ChromaDB knowledge base.

<br />

[![Built by Studio1](https://img.shields.io/badge/Built_by_Studio1-f97316?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNjAgMTYwIiBmaWxsPSJub25lIj48cGF0aCBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTAgMzVDMCAxNi42ODA3IDE0LjA3NDQgMS42NDg0NCAzMiAwLjEyNjk1M1YxNDFINTEuMDUyM0M1Mi40MzA4IDEzNy4zNDQgNTQuNzQ0NiAxMzMuNjg5IDU3Ljk5MzggMTMwLjAzM0M2MS4xNDQ2IDEyNi41MDggNjQuNjg5MiAxMjMuNDQgNjguNjI3NyAxMjAuODI5QzcyLjU2NjIgMTE4LjM0OSA3Ni4zNTY5IDExNi43ODIgODAgMTE2LjEyOVY4Ni43NTQ0Qzc1LjQ3MDggODcuOTI5MiA3MS4zODQ2IDg5LjY5MTkgNjcuNzQxNSA5Mi4wNDE1QzY0IDk0LjUyMjUgNjAuNzUwOCA5Ny40NiA1Ny45OTM4IDEwMC44NTRDNTYuNTM0NSAxMDIuNzIgNTUuMjU0NSAxMDQuNjU5IDU0LjE1MzkgMTA2LjY3MVYwSDEyNUMxNDQuMzMgMCAxNjAgMTUuNjY5OSAxNjAgMzVWMTI1QzE2MCAxNDQuMzMgMTQ0LjMzIDE2MCAxMjUgMTYwSDEyNFYxOEgxMDQuOTQ4QzEwMy41NjkgMjEuNjgxNiAxMDEuMjU1IDI1LjM2MjggOTguMDA2MiAyOS4wNDQ0Qzk0Ljg1NTQgMzIuNTk0MiA5MS4zMTA4IDM1LjY4NDEgODcuMzcyMyAzOC4zMTRDODMuNDMzOCA0MC44MTIgNzkuNjQzMSA0Mi4zODk2IDc2IDQzLjA0NzRWNzIuNjMwNEM4MC41MjkyIDcxLjQ0NzMgODQuNjE1NCA2OS42NzI0IDg4LjI1ODUgNjcuMzA1N0M5MiA2NC44MDc2IDk1LjI0OTIgNjEuODQ5MSA5OC4wMDYyIDU4LjQzMDdDOTkuNDY1NSA1Ni41NTEzIDEwMC43NDUgNTQuNTk4NiAxMDEuODQ2IDUyLjU3MjNWMTYwSDM1QzE1LjY3IDE2MCAwIDE0NC4zMyAwIDEyNVYzNVoiIGZpbGw9IiNmZmZmZmYiLz48L3N2Zz4K)](https://studio1hq.com)
[![Built with Bright Data](https://img.shields.io/badge/Built_with_Bright_Data-141414?style=for-the-badge)](https://brightdata.com)

[Bright Data docs](https://docs.brightdata.com) &nbsp;·&nbsp; [Bright Data](https://brightdata.com) &nbsp;·&nbsp; [More examples](https://github.com/Studio1HQ) &nbsp;·&nbsp; [studio1hq.com](https://studio1hq.com)

</div>

<br />

## Overview

A research assistant that collects web data with Bright Data and processes it on your machine with a local Ollama model. Summaries and source text are stored in a ChromaDB knowledge base, so you can search earlier research sessions.

Bright Data is called through its Data Collection API (`https://api.brightdata.com/dca/trigger`) from `BrightDataClient` in `research_agent.py`. Ollama runs the summarization, so model inference stays local.

## Features

- **Local AI processing**: Ollama models summarize and analyze, with no cloud LLM calls.
- **Bright Data collection**: Fetches web data for the topic you enter.
- **Vector knowledge base**: ChromaDB stores research and supports similarity search.
- **Streamlit UI**: Sidebar for the API key, model choice and number of sources.
- **Multi-source research**: Summarizes each source, then produces overall insights.
- **Research history**: View past sessions from the sidebar.

## Tech stack

| Layer | Tool |
| --- | --- |
| UI | [Streamlit](https://streamlit.io) |
| Web data | [Bright Data](https://brightdata.com) Data Collection API |
| LLM | [Ollama](https://ollama.com) (`llama2` by default) |
| Vector store | [ChromaDB](https://www.trychroma.com) |

## Getting started

### Prerequisites

- Python 3.8+
- A [Bright Data](https://brightdata.com) account and API key
- [Ollama](https://ollama.com) installed with at least one model pulled
- 4 GB or more of RAM for local models

### Installation

```bash
git clone https://github.com/Studio1HQ/deep-research.git
cd deep-research
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Install Ollama and pull a model:

```bash
curl -fsSL https://ollama.ai/install.sh | sh
ollama pull llama2
```

### Environment variables

| Variable | Description |
| --- | --- |
| `BRIGHT_DATA_API_KEY` | Bright Data API key. You can also enter it in the app sidebar. |

```bash
echo "BRIGHT_DATA_API_KEY=your_actual_key_here" > .env
```

### Run

```bash
streamlit run app.py
```

Open [http://localhost:8501](http://localhost:8501), then:

1. Enter your Bright Data API key in the sidebar.
2. Choose the Ollama model and the number of sources.
3. Type a research topic, for example "Latest AI developments in 2024".
4. Click Start Research and browse the summaries and insights.

## How it works

- **`BrightDataClient`**: Fetches web data for the query.
- **`OllamaProcessor`**: Runs `ollama run <model>` to summarize each source and the overall topic.
- **`ResearchKnowledgeBase`**: Persists documents in `./research_db` and supports `search_similar`.
- **`DeepResearchAgent`**: Ties the three together in `conduct_research`.
- **`app.py`**: Streamlit interface.

## Resources

- [Bright Data docs](https://docs.brightdata.com): Web data collection products.
- [Bright Data](https://brightdata.com): Account and API key.
- [Ollama](https://ollama.com): Local model runtime.

<br />

---

<div align="center">

<a href="https://studio1hq.com">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Studio1HQ/website/main/brand/studio1-logo-on-dark.svg" />
    <img src="https://raw.githubusercontent.com/Studio1HQ/website/main/brand/studio1-logo-on-light.svg" alt="Studio1" width="160" />
  </picture>
</a>

Built by **[Studio1](https://studio1hq.com)**, the technical content and DevRel partner for devtool teams. Made with [Bright Data](https://brightdata.com).<br />
Browse more open-source examples at [github.com/Studio1HQ](https://github.com/Studio1HQ).

[![Website](https://img.shields.io/badge/studio1hq.com-0b0807?style=for-the-badge&logo=googlechrome&logoColor=white)](https://studio1hq.com)
[![Book a call](https://img.shields.io/badge/Book_a_strategy_call-f97316?style=for-the-badge&logo=googlecalendar&logoColor=white)](https://cal.com/studio1/collab)
[![X](https://img.shields.io/badge/%40Studio1HQ-141414?style=for-the-badge&logo=x&logoColor=white)](https://x.com/Studio1HQ)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0a66c2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/company/studio1hq/)

<sub><a href="https://studio1hq.com">studio1hq.com</a> · Technical content, docs, video and DevRel for devtools</sub>

</div>
