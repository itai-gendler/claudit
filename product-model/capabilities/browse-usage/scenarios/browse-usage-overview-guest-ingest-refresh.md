---
{
  "kind": "primary",
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
      "text": "A changed-ingest event arrives during browsing.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::overview"
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
            "Counted status"
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
        }
      ],
      "actor": "guest",
      "contexts": {
        "web": {
          "place": "claudit-web::public::overview"
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
            "Thinking tokens",
            "Search count",
            "Estimated cost",
            "Rate classification",
            "Meter treatment",
            "Context input",
            "Visible reply size",
            "Reply latency",
            "Counted status"
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
        }
      ],
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

# Overview guest ingest refresh

## Trigger

The Overview selection is examined.

## Outcome

Participating consumers refresh for the current selection without accepting superseded responses.

## Edge cases

- Cache/context-distribution effects and the initial model-list fetch do not all depend on the ingestion nonce.
- A superseded response does not replace the current selection.
