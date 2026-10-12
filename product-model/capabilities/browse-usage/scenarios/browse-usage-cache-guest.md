---
{
  "kind": "primary",
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
      "text": "The selected population contains billed cache observations.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::cache"
        }
      }
    },
    {
      "text": "The Product loads the selected usage observations.",
      "kind": "product",
      "entities": [
        {
          "entity": "request",
          "effect": "reads",
          "facts": [
            "Identity",
            "Time",
            "Model",
            "Provider",
            "Billed tokens",
            "TTL creation",
            "Search count",
            "Estimated cost",
            "Rate classification",
            "Meter treatment",
            "Context input",
            "Source line"
          ]
        },
        {
          "entity": "transcript",
          "effect": "reads",
          "facts": [
            "Models",
            "Context turns"
          ]
        }
      ],
      "actor": "guest",
      "contexts": {
        "web": {
          "place": "claudit-web::public::cache"
        }
      }
    },
    {
      "text": "The Guest examines the selected statistics.",
      "kind": "actor",
      "entities": [
        {
          "entity": "request",
          "effect": "reads",
          "facts": [
            "Identity",
            "Time",
            "Model",
            "Provider",
            "Billed tokens",
            "TTL creation",
            "Search count",
            "Estimated cost",
            "Rate classification",
            "Meter treatment",
            "Context input",
            "Source line"
          ]
        },
        {
          "entity": "transcript",
          "effect": "reads",
          "facts": [
            "Models",
            "Context turns"
          ]
        }
      ],
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

# Cache guest population

## Trigger

The Cache selection is examined.

## Outcome

Stored totals, TTL cost components, model/provider summaries, top requests and context distributions are presented.

## Edge cases

- The displayed values omit source paths and project grouping; numeric request identifiers, source line numbers and some individual context observations remain.
