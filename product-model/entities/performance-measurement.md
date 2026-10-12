---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/web_metrics.py#normalise"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/web_metrics.py#store"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_web_metrics.py#web_metrics_readout"
    }
  ]
}
---

# Performance measurement

An admitted browser observation contributing to the operator readout and its durable summaries.

## Information kept

- **Time** — Server-side recording time.
- **Category** — Supported page-operation, layout-shift or blocking category.
- **Part** — The measured fetch, client, total, shift or blocking part.
- **Region** — A supported page region.
- **Phase** — A supported operation phase.
- **Value** — A finite measured value clamped to the applicable part bounds.
- **Source audience** — The non-guest user identifier or the shared guest audience; guest browsers are not individually identified.
