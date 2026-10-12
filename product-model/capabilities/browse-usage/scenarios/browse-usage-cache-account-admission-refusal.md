---
{
  "kind": "validation",
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
      "text": "The supplied range is invalid or presented credentialed access is missing, invalid, expired or revoked.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::cache"
        }
      }
    },
    {
      "text": "The Product returns HTTP 401 for invalid access or HTTP 400 for an invalid range, without returning the refused population.",
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

# Cache account admission refusal

## Trigger

The Cache selection is examined.

## Outcome

The selection is refused without protected cache information.
