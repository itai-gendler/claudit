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
      "text": "The population spans scheduled or banded rates.",
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

# Cache account variable rates

## Trigger

The Cache selection is examined.

## Outcome

Estimate distinctions and derived components are presented while the stored total remains the total.

## Edge cases

- Scheduled token decomposition can be rescaled toward persisted token cost; this is not exact per-component attribution.
- Search cost is additive and neutral cache writes are not a billing input.
