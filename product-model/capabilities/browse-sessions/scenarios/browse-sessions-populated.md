---
{
  "kind": "primary",
  "routes": {
    "web": "Sessions"
  },
  "steps": [
    {
      "text": "The User examines Sessions for the current selection.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::sessions"
        }
      }
    },
    {
      "text": "The selected population has session summaries.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::sessions"
        }
      }
    },
    {
      "text": "The Product presents Coding session and Project summaries.",
      "kind": "product",
      "entities": [
        {
          "entity": "coding-session",
          "effect": "reads",
          "facts": [
            "Identity",
            "Project",
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
            "Display name"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::sessions"
        }
      }
    },
    {
      "text": "The User sorts the Coding session summaries and selects a session.",
      "kind": "actor",
      "entities": [
        {
          "entity": "coding-session",
          "effect": "reads",
          "facts": [
            "Identity",
            "Project",
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
            "Display name"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::sessions"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/sessions-list.jsx#SessionsList"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_dashboard.py#_fold_sessions"
    }
  ]
}
---

# Sessions populated

## Trigger

Sessions is examined for the current range/project.

## Outcome

The bounded summaries can be sorted and a session selected.

## Edge cases

- Dashboard summaries supply this population; at most 500 are selected upstream and the browser renders the first 80 after sorting.
- Selection starts transcript inspection; a summary can exist without a main transcript.
