---
{
  "kind": "validation",
  "routes": {
    "overview": "Authenticated Overview"
  },
  "steps": [
    {
      "text": "The User selects the page-performance range.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The caller’s Account has Operator access other than literal true.",
      "kind": "condition",
      "entities": [
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "Operator access"
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
      "text": "The Product returns HTTP 403 reports operator only without returning performance readings.",
      "kind": "product",
      "entities": [],
      "actor": "user",
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

# Page performance access-refusal

## Trigger

The page-performance range is requested.

## Outcome

HTTP 403 reports operator only without returning performance readings.

## Edge cases

- There is no project filter on the measurement population.
- Shift and blocking values sum visits; they are not one cumulative value for the whole range.
