---
{
  "kind": "edge",
  "routes": {
    "web": "Overview"
  },
  "steps": [
    {
      "text": "The User examines Overview for the chosen range and selection.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "No usage matches the selection.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product displays the selected empty population distinctly from loading and retrieval error.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#Dashboard"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/views/cache-view.jsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_dashboard.py#dashboard_route"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_cache.py#cache_view_route"
    }
  ]
}
---

# Overview account empty

## Trigger

The Overview selection is examined.

## Outcome

The selected empty population is distinguished from loading and failure.
