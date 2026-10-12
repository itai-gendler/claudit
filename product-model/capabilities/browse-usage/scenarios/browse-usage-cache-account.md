---
{
  "kind": "primary",
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
      "text": "The selected population contains billed cache observations.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::cache"
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
            "Source location",
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
        },
        {
          "entity": "project",
          "effect": "reads",
          "facts": [
            "Identity",
            "Display name"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::cache"
        }
      }
    },
    {
      "text": "The User examines the selected statistics.",
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
        },
        {
          "entity": "project",
          "effect": "reads",
          "facts": [
            "Identity",
            "Display name"
          ]
        }
      ],
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

# Cache account population

## Trigger

The Cache selection is examined.

## Outcome

Stored totals, TTL cost components, model/provider summaries, top requests and context distributions are presented.
