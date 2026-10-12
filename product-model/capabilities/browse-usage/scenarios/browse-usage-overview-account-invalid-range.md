---
{
  "kind": "validation",
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
      "text": "The supplied range is malformed or overflows supported date arithmetic.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product returns HTTP 400 for the invalid range and does not substitute another population.",
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

# Overview account invalid range

## Trigger

The Overview selection is examined.

## Outcome

The invalid range is rejected without replacing it with another population.
