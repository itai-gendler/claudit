---
{
  "availability": [
    {
      "place": "claudit-web::authenticated"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/perf.js"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_web_metrics.py#post_metrics"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/web_metrics.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_web_metrics.py"
    }
  ]
}
---

# Record page performance

Collect admitted browser observations automatically for the operator readout and durable performance summaries.
