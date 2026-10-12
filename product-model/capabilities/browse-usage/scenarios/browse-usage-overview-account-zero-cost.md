---
{
  "kind": "edge",
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
      "text": "Selected usage has zero estimated cost.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::overview"
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
            "Thinking tokens",
            "Search count",
            "Estimated cost",
            "Rate classification",
            "Meter treatment",
            "Context input",
            "Visible reply size",
            "Reply latency",
            "Counted status",
            "Request metadata",
            "Source location"
          ]
        },
        {
          "entity": "tool-call",
          "effect": "reads",
          "facts": [
            "Name",
            "Model",
            "Settlement",
            "Error outcome",
            "Churn",
            "Counted status"
          ]
        },
        {
          "entity": "transcript",
          "effect": "reads",
          "facts": [
            "Models",
            "Agent attribution",
            "Prompt count",
            "Context turns",
            "Rate-limit hits",
            "Main designation"
          ]
        },
        {
          "entity": "coding-session",
          "effect": "reads",
          "facts": [
            "Identity",
            "Activity span",
            "Usage summary",
            "Main transcript availability"
          ]
        },
        {
          "entity": "project",
          "effect": "reads",
          "facts": [
            "Identity",
            "Display name",
            "Activity span"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::overview"
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
            "Thinking tokens",
            "Search count",
            "Estimated cost",
            "Rate classification",
            "Meter treatment",
            "Context input",
            "Visible reply size",
            "Reply latency",
            "Counted status",
            "Request metadata",
            "Source location"
          ]
        },
        {
          "entity": "tool-call",
          "effect": "reads",
          "facts": [
            "Name",
            "Model",
            "Settlement",
            "Error outcome",
            "Churn",
            "Counted status"
          ]
        },
        {
          "entity": "transcript",
          "effect": "reads",
          "facts": [
            "Models",
            "Agent attribution",
            "Prompt count",
            "Context turns",
            "Rate-limit hits",
            "Main designation"
          ]
        },
        {
          "entity": "coding-session",
          "effect": "reads",
          "facts": [
            "Identity",
            "Activity span",
            "Usage summary",
            "Main transcript availability"
          ]
        },
        {
          "entity": "project",
          "effect": "reads",
          "facts": [
            "Identity",
            "Display name",
            "Activity span"
          ]
        }
      ],
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

# Overview account zero cost

## Trigger

The Overview selection is examined.

## Outcome

Usage remains visible while applicable cost-only panels are omitted.
