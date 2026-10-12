---
{
  "kind": "validation",
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
      "text": "Presented access is missing, invalid, expired or revoked, or the supplied selection fails validation.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::overview"
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

# Overview guest access refusal

## Trigger

The Overview selection is examined.

## Outcome

The inadmissible selection is refused without protected disclosure.
