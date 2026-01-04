# Configuration

For basic configuration instructions, see [this documentation](https://developers.openai.com/codex/config-basic).

For advanced configuration instructions, see [this documentation](https://developers.openai.com/codex/config-advanced).

For a full configuration reference, see [this documentation](https://developers.openai.com/codex/config-reference).

## Built-in Model Providers

Codex includes several built-in model providers that you can use out of the box:

### OpenAI

The default provider for Codex. Uses OpenAI's API with the Responses API.

```toml
model_provider = "openai"
model = "gpt-5.1-codex-max"
```

Requires authentication via `OPENAI_API_KEY` environment variable or ChatGPT login.

### OpenRouter

A unified API gateway that provides access to 200+ models from various providers. Built-in support for Codex.

```toml
model_provider = "openrouter"
model = "minimax/minimax-m2.1"
```

**Recommended coding models:**

- `minimax/minimax-m2.1` - Fast, capable coding model
- `x-ai/grok-code-fast-1` - Grok's fast coding model
- `mistralai/devstral-2512:free` - Free Mistral dev model

**Setup:**

1. Get your API key from https://openrouter.ai/settings
2. Set the environment variable:
   ```bash
   export OPENROUTER_API_KEY="sk-or-..."
   ```
3. Configure in `~/.codex/config.toml`:
   ```toml
   model_provider = "openrouter"
   model = "minimax/minimax-m2.1"
   ```

### Local Models (Ollama / LM Studio)

Codex supports local models via Ollama and LM Studio:

```toml
# For Ollama
model_provider = "ollama"
model = "llama3.1"

# For LM Studio
model_provider = "lmstudio"
model = "llama3.1-8b"
```

## Custom Model Providers

You can define additional model providers in your config:

```toml
[model_providers.my-provider]
name = "My Provider"
base_url = "https://api.myprovider.com/v1"
env_key = "MY_PROVIDER_API_KEY"
wire_api = "responses"
request_max_retries = 4
```

## Connecting to MCP servers

Codex can connect to MCP servers configured in `~/.codex/config.toml`. See the configuration reference for the latest MCP server options:

- https://developers.openai.com/codex/config-reference

## Notify

Codex can run a notification hook when the agent finishes a turn. See the configuration reference for the latest notification settings:

- https://developers.openai.com/codex/config-reference
