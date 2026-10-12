---
{
  "kind": "primary",
  "routes": {
    "overview": "Operator Overview observation"
  },
  "steps": [
    {
      "text": "Automatic browser observations satisfy admission and measurement validation.",
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
      "text": "The Product stores admitted Performance measurement observations with server time and source audience.",
      "kind": "product",
      "entities": [
        {
          "entity": "performance-measurement",
          "effect": "creates",
          "facts": [
            "Time",
            "Category",
            "Part",
            "Region",
            "Phase",
            "Value",
            "Source audience"
          ]
        }
      ],
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product processes durable summaries before pruning raw Performance measurement information.",
      "kind": "product",
      "entities": [
        {
          "entity": "performance-measurement",
          "effect": "removes"
        }
      ],
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

# Automatic measurement accepted

## Trigger

Browser instrumentation automatically submits its observations.

## Outcome

HTTP 202 reports the admitted stored count. Durable rollup processing precedes later raw retention cleanup; this acknowledgement is not a completed readout rebuild.

## Edge cases

- Guest and account browser observations contribute; guest browsers share one source audience.
- Admission checks existing retained counts before the batch; insertion can overshoot 20,000 for a user ID or 2,000 for shared guest ID.
- Numeric values are clamped after supported vocabulary and shape validation; raw retention is processed by ingestion, not a wall-clock deletion guarantee.
