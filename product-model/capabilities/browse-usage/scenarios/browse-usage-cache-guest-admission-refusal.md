---
{
  "kind": "validation",
  "routes": {
    "web": "Cache"
  },
  "steps": [
    {
      "text": "The Guest examines Cache for the chosen range and selection.",
      "kind": "actor",
      "entities": [],
      "actor": "guest",
      "contexts": {
        "web": {
          "place": "claudit-web::public::cache"
        }
      }
    },
    {
      "text": "The selection is invalid, access validation fails, or a forbidden nonempty filter is supplied.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::cache"
        }
      }
    },
    {
      "text": "The Product returns HTTP 401 for invalid access, HTTP 400 for an invalid selection, or HTTP 403 for a forbidden filter, without revealing the refused population.",
      "kind": "product",
      "entities": [],
      "actor": "guest",
      "contexts": {
        "web": {
          "place": "claudit-web::public::cache"
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

# Cache guest admission refusal

## Trigger

The Cache selection is examined.

## Outcome

The selection is refused without protected cache information.
