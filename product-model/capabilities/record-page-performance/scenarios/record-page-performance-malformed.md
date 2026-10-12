---
{
  "kind": "validation",
  "routes": {
    "overview": "Operator Overview observation"
  },
  "steps": [
    {
      "text": "The automatic batch is invalid JSON, has unknown/invalid terms, invalid shape or more than 50 items.",
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
      "text": "The Product returns HTTP 400 identifies invalid JSON or the invalid batch field; no measurements are created.",
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

# Automatic measurement malformed

## Trigger

Browser instrumentation automatically submits its observations.

## Outcome

HTTP 400 identifies invalid JSON or the invalid batch field; no measurements are created.

## Edge cases

- Guest and account browser observations contribute; guest browsers share one source audience.
- Admission checks existing retained counts before the batch; insertion can overshoot 20,000 for a user ID or 2,000 for shared guest ID.
- Numeric values are clamped after supported vocabulary and shape validation; raw retention is processed by ingestion, not a wall-clock deletion guarantee.
