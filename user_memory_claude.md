# Claude Code Memory File

You are coding for mlziade, a backend developer and solution architect.

Here are some points to keep in mind when answering his prompts:

---

## Python Guidelines

* If there are uv files (like `uv.lock`) in the project, use uv commands.
* NEVER import or use the `typing` library in def functions signature — always use python type hints like the example below.
* Always use the logging library to create logs.
* Use Docstrings format for commenting on the code.

### Example of Type Hinting

```python
def add_numbers(a: int, b: int) -> int:
    """
    Add two integers together.

    Args:
        a: First integer
        b: Second integer

    Returns:
        The sum of the two integers.
    """
    return a + b
```

---

## JavaScript / TypeScript Guidelines

* Use JSDoc format for commenting on the code.

---

## Commit & PR Messages

* Never add "Generated with \[Claude Code]" or
  "Co-Authored-by: Claude" to the message.

---

## ZLLM API Integration

When asked to integrate with the ZLLM API or create a connector file,
use the following examples for the basic endpoints:

### Environment Variables

* `ZLLM_API_KEY`: The API key
* `ZLLM_BASE_URL`: `https://zllm.mlziade.com.br`
* `ZLLM_MODEL`: `gemma3:1b`

### Example cURL Requests

#### Auth

```bash
curl --location '{{ZLLM_BASE_URL}}/auth' \
  --header 'Content-Type: application/json' \
  --data '{"api_key": "{{ZLLM_API_KEY}}"}'
```

#### Example Response

```json
{
  "expires_at": "2025-05-11T22:17:49.1992874-03:00",
  "role": "admin",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

#### Generate

```bash
curl --location '{{ZLLM_BASE_URL}}/llm/generate' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <your_token>' \
  --data '{"prompt": "What is an LLM in 200 words?", "model": "{{ZLLM_MODEL}}"}'
```

#### Generate (Streaming)

```bash
curl --location '{{ZLLM_BASE_URL}}/llm/generate/streaming' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <your_token>' \
  --data '{"prompt": "O que são LLM em 200 palavras", "model": "{{ZLLM_MODEL}}"}'
```

---