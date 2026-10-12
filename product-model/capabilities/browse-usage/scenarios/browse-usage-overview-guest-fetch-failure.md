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
      "text": "The dashboard retrieval fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::overview"
        }
      }
    },
    {
      "text": "The Product presents the retrieval error separately from loading or empty results; Overview can retain previously loaded statistics.",
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

# Overview guest fetch failure

## Trigger

The Overview selection is examined.

## Outcome

The retrieval failure is distinguished from empty/loading; previous results can remain.
