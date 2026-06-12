# local-pyrag

A local RAG CLI that chats with documents using a locally-running LLM via [Ollama](https://ollama.com).

## Requirements

- [Ollama](https://ollama.com) running locally
- Python 3.11+
- [uv](https://docs.astral.sh/uv/)

## Setup

```bash
uv sync
```

Create a `.env` file in the project root:

```env
# Point at your Ollama instance (default: http://localhost:11434/v1)
OPENAI_BASE_URL=http://localhost:11434/v1

# Not required for Ollama, but must be non-empty for the OpenAI client
OPENAI_API_KEY=unused-local

# Model to use (default: gemma3:latest)
CHAT_MODEL=gemma3:latest
```

## Usage

```bash
uv run pyrag --help
```

## Development

```bash
# Install deps
uv sync

# Run directly
uv run pyrag
```
