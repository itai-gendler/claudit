---
{
  "kind": "edge",
  "routes": {
    "web": "Overview"
  },
  "steps": [
    {
      "text": "The Guest examines Overview for the chosen range and selection.",
      "kind": "actor",
      "entities": [],
      "actor": "guest",
      "contexts": {
        "web": {
          "place": "claudit-web::public::overview"
        }
      }
    },
    {
      "text": "No usage matches the selection.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::overview"
        }
      }
    },
    {
      "text": "The Product displays the selected empty population distinctly from loading and retrieval error.",
      "kind": "product",
      "entities": [],
      "actor": "guest",
      "contexts": {
        "web": {
          "place": "claudit-web::public::overview"
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

# Overview guest empty

## Trigger

The Overview selection is examined.

## Outcome

The selected empty population is distinguished from loading and failure.
