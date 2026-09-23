# 🧠 Perplexity AI Model Guide & Mapping (2026 Frontier Models)

This guide covers model comparisons, benchmarks, parameter mappings, and collection support for Perplexity AI (Pro & Max tiers).

---

## 🏆 Model Rankings & Recommendations

Based on empirical performance and coding benchmarks:

### 1. 🥇 Best Overall (Coding, Software Engineering & System Design)
* **`Claude Sonnet 5`** (Anthropic) — *Available on: Pro & Max*
  * **Parameter:** `mode="pro"`, `model="claude sonnet 5"` (Backend: `claude45sonnet` / `claude45sonnetthinking`)
  * **Why it's #1:** World-class in-repository coding, high technical follow-through, low hallucination rate, and adaptive multi-tier thinking support.

### 2. 🥈 Best for Terminal, CLI & High Efficiency Workflows
* **`GPT-5.6 Terra`** (OpenAI) — *Available on: Pro & Max*
  * **Parameter:** `mode="pro"`, `model="gpt-5.2"` / `"gpt5"` (Backend: `gpt52` / `gpt52_thinking`)
  * **Why:** Optimized for fast, multi-step problem solving, CLI workflows, and low-latency structured output.

### 3. 🥉 Best for Massive Context (1M+ Tokens) & Deep Reasoning
* **`Gemini 3.1 Pro`** (Google) — *Available on: Pro & Max*
  * **Parameter:** `mode="pro"`, `model="gemini-3.0-pro"` (Backend: `gemini30pro`)
  * **Why:** Excels on abstract reasoning benchmarks (ARC-AGI-2), large context retention, and multi-file repository analysis in a single pass.

### 4. 🚀 Specialized Models (STEM & Multi-Step Agentic)
* **`Grok 4.5`** (xAI): MoE architecture tailored for STEM, math, and code synthesis.
* **`Kimi K3`** (Moonshot AI): 2.8T parameter model with Kimi Delta Attention for persistent, long-turn reasoning tasks.
* **`Nemotron 3 Ultra`** (NVIDIA): Hybrid Transformer-Mamba architecture designed for autonomous agent reasoning.

### 5. 💎 Max Tier Exclusive Models
* **`Claude Opus 5`** (Anthropic) & **`GPT-5.6 Sol`** (OpenAI):
  * *Available exclusively to Perplexity Max subscribers.*
  * Reserved for frontier scientific, mathematical, and complex architectural problem solving.

---

## 📊 Model Comparison Matrix (Pro vs Max)

| Model | Provider | Pro Tier | Max Tier | Reasoning Support | Parameter Mapping |
| :--- | :--- | :---: | :---: | :--- | :--- |
| **Claude Sonnet 5** | Anthropic | **Yes** | **Yes** | Optional (`mode="reasoning"`) | `model="claude sonnet 5"` |
| **GPT-5.6 Terra** | OpenAI | **Yes** | **Yes** | Optional (`mode="reasoning"`) | `model="gpt-5.2"` / `"gpt-4.5"` |
| **Gemini 3.1 Pro** | Google | **Yes** | **Yes** | Always active | `model="gemini-3.0-pro"` |
| **Grok 4.5** | xAI | **Yes** | **Yes** | Optional (`mode="reasoning"`) | `model="grok-4.1"` |
| **Kimi K3** | Moonshot AI | **Yes** | **Yes** | Always active | `model="kimi k3"` |
| **GLM 5.2** | Z.ai | **Yes** | **Yes** | Always active | `model="glm 5.2"` |
| **Nemotron 3 Ultra** | NVIDIA | **Yes** | **Yes** | Always active | `model="nemotron"` |
| **Sonar 2** | Perplexity | **Yes** | **Yes** | Not applicable | `model="sonar"` |
| **Claude Opus 5** | Anthropic | ❌ No | **Yes** | Optional | `model="claude opus 5"` (Max only) |
| **GPT-5.6 Sol** | OpenAI | ❌ No | **Yes** | Optional | `model="gpt-5.6 sol"` (Max only) |

---

## ⚡ Reasoning Workflows & Complex Problem Solving

For complex architectural tasks, code generation, or technical research, leverage the `reasoning` mode with **Claude Sonnet 5** or **Gemini 3.1 Pro**:

```python
import os
import json
import perplexity

# Load cookies from environment variable (or config dict)
raw_cookies = os.getenv("PERPLEXITY_COOKIES")
cookies = json.loads(raw_cookies) if raw_cookies else None

client = perplexity.Client(cookies=cookies)

# Query with extended reasoning enabled
response = client.search(
    query="Design a resilient event-driven microservices architecture with Kafka and PostgreSQL CDC",
    mode="reasoning",
    model="claude sonnet 5"
)

print(response["answer"])
```

---

## 📁 Perplexity Projects / Spaces / Collections Support

You can target searches within a specific **Perplexity Space / Project / Collection** by passing the `collection_uuid` parameter.

Queries routed through a collection inherit custom instructions and gain direct access to uploaded files and knowledge sources within that space.

### Finding your `collection_uuid`:
1. Navigate to your Space/Project on [perplexity.ai](https://www.perplexity.ai).
2. Look at the browser URL: `https://www.perplexity.ai/spaces/<UUID>` or `https://www.perplexity.ai/collections/<UUID>`.
3. Copy the UUID string.

### Example:
```python
import os
import json
import perplexity

raw_cookies = os.getenv("PERPLEXITY_COOKIES")
cookies = json.loads(raw_cookies) if raw_cookies else None

client = perplexity.Client(cookies=cookies)

response = client.search(
    query="Summarize the core findings and action items across this project's documentation",
    mode="pro",
    model="claude sonnet 5",
    collection_uuid="12345678-abcd-1234-abcd-1234567890ab"
)

print(response["answer"])
```
