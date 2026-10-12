---
{
  "kind": "primary",
  "routes": {
    "overview": "Authenticated Overview"
  },
  "steps": [
    {
      "text": "The Web operator selects the page-performance range.",
      "kind": "actor",
      "entities": [],
      "actor": "web-operator",
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The range exceeds the raw working set.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product presents Performance measurement summaries with their population/precision distinction.",
      "kind": "product",
      "entities": [
        {
          "entity": "performance-measurement",
          "effect": "reads",
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
      "actor": "web-operator",
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

# Page performance historical

## Trigger

The page-performance range is requested.

## Outcome

The readout blends durable rollups and raw tail and explicitly marks approximation.

## Edge cases

- There is no project filter on the measurement population.
- Shift and blocking values sum visits; they are not one cumulative value for the whole range.
