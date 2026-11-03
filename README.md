<div align="center">

# ⚡ SentioGate

### The Zero-Markup, OpenAI-Compatible LLM Router

[![Website](https://img.shields.io/badge/Website-sentiogate.app-2563eb?style=for-the-badge&logo=google-chrome&logoColor=white)](https://sentiogate.app)
[![Documentation](https://img.shields.io/badge/Docs-sentiogate.app%2Fdocs-059669?style=for-the-badge&logo=googledocs&logoColor=white)](https://sentiogate.app/docs)
[![Live Benchmarks](https://img.shields.io/badge/Benchmarks-Live_TTFT-7c3aed?style=for-the-badge&logo=speedtest&logoColor=white)](https://sentiogate.app/benchmarks)
[![Developer Hub](https://img.shields.io/badge/Dev_Hub-sentiogate.github.io-0ea5e9?style=for-the-badge&logo=githubpages&logoColor=white)](https://sentiogate.github.io)
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg?style=for-the-badge)](https://opensource.org/licenses/Apache-2.0)

<p align="center">
  <b>One OpenAI-compatible endpoint for the models you already pay for.</b><br/>
  Routing by cost, quality or latency with Bring-Your-Own-Key (BYOK) and <b>0% token markup</b>. SentioGate automatically falls back to another model if one fails.
</p>

```
Client App / SDK ───▶ [ SentioGate Router ] ──┬──▶ OpenAI
                              │               ├──▶ Anthropic
                   ⚡ Cost / quality / latency ├──▶ Google Gemini
                   🛡️ Automatic fallback       ├──▶ DeepSeek
                   🔒 Encrypted key Vault      └──▶ Groq / Mistral / xAI / ...
```

</div>

---

### 🚀 Why Developers Choose SentioGate

1. **0% Token Markup**: SentioGate is Bring-Your-Own-Key (BYOK). You pay your providers' standard rates directly; SentioGate adds no fee per token.
2. **Routing you control**: send `model: "auto"` and choose `route_preference` `cost` (default), `quality` or `latency`, or pin a specific `provider/model`.
3. **Drop-in OpenAI Compatibility**: works with the OpenAI SDK, LangChain and other OpenAI-compatible tools by changing the base URL and API key.
4. **Automatic fallback**: SentioGate automatically falls back to another model if one fails, so a single provider outage or rate limit doesn't have to break your app.
5. **Your keys stay yours**: provider keys are stored encrypted in your Vault, decrypted only in memory to call the provider, and shown back masked.

---

### 📦 Client SDKs & Tools

Explore our open-source developer libraries and resources:

* **[sentiogate-js](https://github.com/SentioGate/sentiogate-js)** — Lightweight, zero-dependency TypeScript & Node.js client SDK (`@sentiogate/sdk`). Supports streaming and opt-in retries.
* **[sentiogate-python](https://github.com/SentioGate/sentiogate-python)** — Pure standard-library Python SDK (`sentiogate-python`) with streaming support.
* **[llm-routing-benchmarks](https://github.com/SentioGate/llm-routing-benchmarks)** — Open benchmark scripts for measuring Time-To-First-Token (TTFT) and latency across providers.
* **[Developer Hub & Playground](https://sentiogate.github.io)** — Interactive visualizer showing routing in action.

---

### ⚡ Quickstart

#### Python
```python
import os
from sentiogate import AutoRouterClient

client = AutoRouterClient(api_key=os.environ["SENTIOGATE_API_KEY"])

response = client.chat(
    model="auto",  # SentioGate picks the model
    messages=[{"role": "user", "content": "Explain quantum computing in 10 words."}],
    extra_body={"route_preference": "latency"},  # "cost" (default), "quality" or "latency"
)
print(response["choices"][0]["message"]["content"])
```

#### TypeScript / JavaScript
```typescript
import { AutoRouter } from "@sentiogate/sdk";

const router = new AutoRouter({
  baseUrl: "https://api.sentiogate.dev",
  apiKey: process.env.SENTIOGATE_API_KEY,
});

for await (const chunk of router.streamChat({
  model: "auto",
  messages: [{ role: "user", content: "Optimize this SQL query..." }],
  extraBody: { route_preference: "cost" },
})) {
  process.stdout.write(chunk.choices?.[0]?.delta?.content || "");
}
```

#### Drop-in OpenAI SDK Replacement
```python
import os
from openai import OpenAI

# Just update base_url and api_key
client = OpenAI(
    base_url="https://api.sentiogate.dev/v1",
    api_key=os.environ["SENTIOGATE_API_KEY"],
)
```

---

### 📊 Transparent Benchmarks & Data

We believe in open metrics. View provider latency and comparative benchmarks:
* 🌐 **Live Web Benchmarks:** [sentiogate.app/benchmarks](https://sentiogate.app/benchmarks)
* 📈 **Benchmark Methodology & Code:** [SentioGate/llm-routing-benchmarks](https://github.com/SentioGate/llm-routing-benchmarks)
* ⚖️ **Comparison Guide (SentioGate vs OpenRouter & LiteLLM):** [sentiogate.app/compare](https://sentiogate.app/compare)

---

### 🌐 Official Links & Community

* **Web Application & Dashboard:** [https://sentiogate.app](https://sentiogate.app)
* **Interactive Documentation:** [https://sentiogate.app/docs](https://sentiogate.app/docs)
* **Free Chatbot & Gateway Tools:** [https://sentiogate.app/free-ai-tools](https://sentiogate.app/free-ai-tools)
* **GitHub Pages Developer Hub:** [https://sentiogate.github.io](https://sentiogate.github.io)
* **Developer Inquiries:** [support@sentiogate.app](mailto:support@sentiogate.app)
