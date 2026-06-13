# local-pyrag

A local RAG CLI for chatting with a locally-running LLM via [Ollama](https://ollama.com).

## Requirements

- Python 3.11+
- [uv](https://docs.astral.sh/uv/)
- [Ollama](https://ollama.com) running locally

## Setup

```bash
uv sync
```

Create a `.env` file in the project root:

```env
# Ollama API endpoint (default: http://localhost:11434/v1)
OPENAI_BASE_URL=http://localhost:11434/v1

# Any non-empty value works for Ollama
OPENAI_API_KEY=unused-local

# Model to use (default: gemma3:latest)
CHAT_MODEL=gemma3:latest
```

## Usage

Start a chat session:

```bash
pyrag
```

In-session commands:

| Command            | Action                     |
| ------------------ | -------------------------- |
| `/reset`           | Clear conversation history |
| `/exit` or `/quit` | Quit                       |

## Development

To install all the dependencies in the pyproject.toml file run:

```bash
uv sync
```

---

## Database

Once you have the database created, you can create the tables.

```bash
PGPASSWORD=yourpassword psql -U username -d pyrag -f db/init.sql
```
