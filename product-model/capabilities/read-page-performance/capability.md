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
      "target": "backend/api_web_metrics.py#web_metrics_readout"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/perf-panel.jsx#WebMetricsPanel"
    }
  ]
}
---

# Read page performance

Examine observed browser timings, shifts, blocking and guest participation, with exact or approximate population semantics.
