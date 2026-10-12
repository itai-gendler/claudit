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
      "text": "No cache usage matches the selection.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::cache"
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

# Cache account empty

## Trigger

The Cache selection is examined.

## Outcome

The empty cache population is presented without fabricated quantities.
