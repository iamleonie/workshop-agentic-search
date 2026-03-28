# Workshop: Agentic Search for Context Engineering

This workshop discusses how to ...
agentic search

![](/img/agent_search_for_context_engineering_overview.png)

## Set up


### 1. Create and activate a Python virtual environment
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 2. Install depencendies

This notebook uses `langchain` `v1.2.12` and `langchain-openai` `v1.1.11`.
```bash
pip install -r requirements.txt 
```

### 3. Data preparation

Data: https://www.ai.engineer/europe/schedule

The easiest way to run Elasticsearch locally for development and testing is using the start-local script. This script sets up Elasticsearch (and optionally Kibana) using Docker with a simple one-line command.

```bash
curl -fsSL https://elastic.co/start-local | sh
```

This creates an elastic-start-local folder containing configuration files and startup scripts. To start Elasticsearch:

```
cd elastic-start-local
./start.sh
```

### 4. API Keys

see .env.example
- Create one at https://platform.openai.com/account/api-keys if you don't have one
- Embeddings use [Jina Embeddings](https://docs.langchain.com/oss/python/integrations/embeddings/jina) (`jina-embeddings-v2-base-en`), same as the other notebooks. Add `JINA_API_KEY` in `.env` if needed ([Jina dashboard](https://jina.ai/api-dashboard/embedding)). 
- Get free Jina API key: https://jina.ai/api-dashboard/embedding

## Course Outline

TODO 


### [Vanilla Agentic Search](./notebooks/01_vanilla_agentic_search.ipynb)

- Context source: Local Elasticsearch cluster
- Context retrieval tool: Semantic search tool

### [Agentic Search with DB query tool](./notebooks/02_advanced_agentic_search.ipynb)

- Context source: Local Elasticsearch cluster
- Context retrieval tool: ES|QL Query execution tool

- ES|QL
- Elastic Agent Skills for Elasticsearch

Install [Elastic Agent Skills](https://github.com/elastic/agent-skills/tree/main)

```bash
npx skills add elastic/agent-skills
```

### [Agentic Search with Shell tool](./notebooks/03_agentic_search_with_bash_tool.ipynb)

- Context source: Local filesystem
- Context retrieval tool: Shell tool
- File search with `grep`
- Semantic file search with [`jina-grep` CLI](https://github.com/jina-ai/jina-grep-cli)

```bash
git clone https://github.com/jina-ai/jina-grep-cli.git && cd jina-grep-cli
uv pip install -e .
```

# Additional Resources
- [The shell tool is not a silver bullet for context engineering](https://www.elastic.co/search-labs/blog/search-tools-context-engineering)
- [Building effective database retrieval tools for context engineering](https://www.elastic.co/search-labs/blog/database-retrieval-tools-context-engineering)
- [Elasticsearch Quickstart](https://www.elastic.co/docs/reference/elasticsearch/clients/python/getting-started)