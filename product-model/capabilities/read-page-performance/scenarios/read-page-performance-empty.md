---
{
  "kind": "edge",
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
      "text": "No measurements are available for the range.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product reports the readout does not fabricate zero timings.",
      "kind": "product",
      "entities": [],
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

# Page performance empty

## Trigger

The page-performance range is requested.

## Outcome

The readout does not fabricate zero timings.

## Edge cases

- There is no project filter on the measurement population.
- Shift and blocking values sum visits; they are not one cumulative value for the whole range.
