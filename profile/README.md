<div align="center">

# ⚡ SentioGate

### The Intelligent, Zero-Markup AI LLM Router & Unified Gateway

[![Website](https://img.shields.io/badge/Website-sentiogate.app-2563eb?style=for-the-badge&logo=google-chrome&logoColor=white)](https://sentiogate.app)
[![Documentation](https://img.shields.io/badge/Docs-sentiogate.app%2Fdocs-059669?style=for-the-badge&logo=googledocs&logoColor=white)](https://sentiogate.app/docs)
[![Live Benchmarks](https://img.shields.io/badge/Benchmarks-Live_TTFT-7c3aed?style=for-the-badge&logo=speedtest&logoColor=white)](https://sentiogate.app/benchmarks)
[![Developer Hub](https://img.shields.io/badge/Dev_Hub-sentiogate.github.io-0ea5e9?style=for-the-badge&logo=githubpages&logoColor=white)](https://sentiogate.github.io)
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg?style=for-the-badge)](https://opensource.org/licenses/Apache-2.0)

<p align="center">
  <b>One OpenAI-compatible endpoint for every frontier model.</b><br/>
  Intelligent latency routing, automatic multi-provider failover, and strict Bring-Your-Own-Key (BYOK) privacy — with <b>0% token markup</b>.
</p>

```
Client App / SDK ───▶ [ SentioGate Intelligent Router ] ──┬──▶ OpenAI (GPT-4o)
                              │                          ├──▶ Anthropic (Claude 3.5 Sonnet)
                       ⚡ Latency & Cost Optimization    ├──▶ DeepSeek (V3 / R1)
                       🛡️ Automatic Instant Failover      ├──▶ Google Gemini (Flash / Pro)
                       🔒 BYOK (Keys Never Stored)       └──▶ Groq / Bedrock / Mistral
```

</div>

---

### 🚀 Why Developers Choose SentioGate

1. **0% Token Markup**: Unlike conventional resale proxies that inflate model token rates, SentioGate operates on a pure Bring-Your-Own-Key (BYOK) infrastructure. You pay standard raw provider rates directly.
2. **Sub-20ms Routing Overhead**: Ultra-fast heuristic and statistical health-based routing that selects the fastest available model replica or failover host.
3. **Drop-in OpenAI Compatibility**: Works instantly with your existing code, LangChain, LlamaIndex, Vercel AI SDK, or Open-WebUI by switching just two lines (`baseURL` and `apiKey`).
4. **Resilient Circuit Breaking**: Never let provider outages or HTTP 429 rate limits break your production applications. When OpenAI or Anthropic degrades, requests seamlessly cascade to alternate providers or fallback models in milliseconds.

---

### 📦 Client SDKs & Tools

Explore our open-source developer libraries and resources:

* **[sentiogate-js](https://github.com/SentioGate/sentiogate-js)** — Lightweight, zero-dependency TypeScript & Node.js client SDK. Supports streaming, retries, and token-budget constraints.
* **[sentiogate-python](https://github.com/SentioGate/sentiogate-python)** — Pure standard-library Python SDK with synchronous and asynchronous streaming support.
* **[llm-routing-benchmarks](https://github.com/SentioGate/llm-routing-benchmarks)** — Open benchmark suite measuring Time-To-First-Token (TTFT), failover latency, and throughput across 20+ models and inference providers.
* **[Developer Hub & Playground](https://sentiogate.github.io)** — Interactive visualizer showing dynamic routing in action.

---

### ⚡ Quickstart

#### Python
```python
import os
from sentiogate import SentioGate

client = SentioGate(
    api_key=os.environ["SENTIOGATE_API_KEY"],
    # Optionally pass your provider keys directly (BYOK)
    provider_keys={"openai": os.environ["OPENAI_API_KEY"]}
)

response = client.chat.completions.create(
    model="auto:fastest",  # Automatically routes to lowest-latency model
    messages=[{"role": "user", "content": "Explain quantum computing in 10 words."}],
)
print(response.choices[0].message.content)
```

#### TypeScript / JavaScript
```typescript
import { SentioGate } from "@sentiogate/sdk";

const gate = new SentioGate({
  apiKey: process.env.SENTIOGATE_API_KEY!,
});

const completion = await gate.chat.completions.create({
  model: "auto:cost-efficient", // Routes for optimal token efficiency
  messages: [{ role: "user", content: "Optimize this SQL query..." }],
  stream: true,
});

for await (const chunk of completion) {
  process.stdout.write(chunk.choices[0]?.delta?.content || "");
}
```

#### Drop-in OpenAI SDK Replacement
```python
from openai import OpenAI

# Zero code refactoring: just update base_url
client = OpenAI(
    base_url="https://api.sentiogate.app/v1",
    api_key=os.environ["SENTIOGATE_API_KEY"]
)
```

---

### 📊 Transparent Benchmarks & Data

We believe in open metrics. View real-time provider latency, historical uptime, and comparative benchmarks:
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
