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
      "text": "The supplied range is invalid or presented credentialed access is missing, invalid, expired or revoked.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::overview"
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

# Overview account access refusal

## Trigger

The Overview selection is examined.

## Outcome

The inadmissible selection is refused without protected disclosure.
