---
{
  "kind": "edge",
  "routes": {
    "web": "Cache"
  },
  "steps": [
    {
      "text": "The User examines Cache for the chosen range and selection.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::cache"
        }
      }
    },
    {
      "text": "Cache or context-distribution retrieval fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::cache"
        }
      }
    },
    {
      "text": "The Product presents the failed Cache or context-distribution retrieval separately from loading and empty results; a failed region does not present its previous values as a successful new selection.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::cache"
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

# Cache account fetch failure

## Trigger

The Cache selection is examined.

## Outcome

The failure is presented distinctly from an empty population.
