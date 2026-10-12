---
{
  "kind": "edge",
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
      "text": "No sessions match the selection.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::sessions"
        }
      }
    },
    {
      "text": "The Product presents the empty selected list rather than fabricated summaries.",
      "kind": "product",
      "entities": [],
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

# Sessions empty

## Trigger

Sessions is examined for the current range/project.

## Outcome

An empty session population is presented.

## Edge cases

- Dashboard summaries supply this population; at most 500 are selected upstream and the browser renders the first 80 after sorting.
- Selection starts transcript inspection; a summary can exist without a main transcript.
