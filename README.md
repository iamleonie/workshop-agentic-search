# Workshop: Agentic Search for Context Engineering

This workshop discusses different agentic search techniques for context engineering.

![](/img/Agentic%20Search%20for%20Context%20Engineering.png)

**Learning outcomes:** By the end of this workshop you will have
- experimented with a few different ways to search for context across different context sources
- learned how you can expand the capabilities of search tools with Agent Skills and additional CLIs
- gained an intuition on the trade-offs for different search tool

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

### 3. Set up Elasticsearch

This workshop uses a local Elasticsearch instance as one of the out-of-context sources.

The easiest way to run Elasticsearch locally is using the `start-local` script, which sets up Elasticsearch (and optionally Kibana) using Docker with a simple one-line command:

```bash
curl -fsSL https://elastic.co/start-local | sh
```

This creates an *elastic-start-local* folder containing configuration files and startup scripts. To start Elasticsearch:

```bash
cd elastic-start-local
./start.sh
```

Expected output:

```bash
 ✔ Container es-local-dev          Healthy                                                                     
 ✔ Container kibana-local-dev      Healthy
```

### 4. Environment variables and API Keys

This workshop requires three categories of environment variables, which need to be added to the `.env` file (see `.env.example`)
- **LLM API key:** These notebooks use OpenAI models through LiteLLM. Alternatively, you can use any LLM of your choice that is capable of tool use. 
- **Jina API key:**  You can obtain a free Jina API key on from the [official Jina page](https://jina.ai/api-dashboard/embedding) without registration.
- **Elasticsearch credentials:** During the set up of your local Elasticsearch instance, you will find the Password (username and url stay the same).


### 5. Data preparation

The workshop's examples are based on the AI Engineer Europe Conference schedule, which is available in the `data` folder under `session.json` (Downloaded from: https://www.ai.engineer/europe/schedule).

This workshop discusses data store and filesystem as context sources. To prepare the Elasticsearch data store and the local filesystem, run the [data preparation notebook](./notebooks/00_prepare_data.ipynb).

## Course Outline

| **Topic** | **Context source** | **Retrieval tool** | **Notebook** |
| --- | --- | --- | --- |
| Vanilla Agentic Search | Local Elasticsearch cluster | Semantic search tool | [01_vanilla_agentic_search.ipynb](./notebooks/01_vanilla_agentic_search.ipynb) |
| Agentic Search with DB query tool | Local Elasticsearch cluster | ESQL Query execution tool (+ Agent Skills) | [02_advanced_agentic_search.ipynb](./notebooks/02_advanced_agentic_search.ipynb) |
| Agentic Search with Shell tool | Local Filesystem | Shell tool (+ `jina-grep-cli`) | [03_agentic_search_with_bash_tool.ipynb](./notebooks/03_agentic_search_with_bash_tool.ipynb) |

# Additional Resources
- [The shell tool is not a silver bullet for context engineering](https://www.elastic.co/search-labs/blog/search-tools-context-engineering)
- [Building effective database retrieval tools for context engineering](https://www.elastic.co/search-labs/blog/database-retrieval-tools-context-engineering)
- [Elasticsearch Quickstart](https://www.elastic.co/docs/reference/elasticsearch/clients/python/getting-started)
- [Elastic Agent Skills](https://github.com/elastic/agent-skills/tree/main)
- [`jina-grep` CLI](https://github.com/jina-ai/jina-grep-cli)