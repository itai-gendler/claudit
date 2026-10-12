---
{
  "kind": "validation",
  "routes": {
    "overview": "Operator Overview observation"
  },
  "steps": [
    {
      "text": "Presented access or matching-origin evidence fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        }
      },
      "unattended": true
    },
    {
      "text": "The Product reports missing/invalid access receives HTTP 401 or cross-origin submission HTTP 403; no measurements are stored.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
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

# Automatic measurement admission-refusal

## Trigger

Browser instrumentation automatically submits its observations.

## Outcome

Missing/invalid access receives HTTP 401 or cross-origin submission HTTP 403; no measurements are stored.

## Edge cases

- Guest and account browser observations contribute; guest browsers share one source audience.
- Admission checks existing retained counts before the batch; insertion can overshoot 20,000 for a user ID or 2,000 for shared guest ID.
- Numeric values are clamped after supported vocabulary and shape validation; raw retention is processed by ingestion, not a wall-clock deletion guarantee.
