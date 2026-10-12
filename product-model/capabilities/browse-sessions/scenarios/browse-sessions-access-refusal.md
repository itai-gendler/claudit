---
{
  "kind": "validation",
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
      "text": "Presented credentialed access is missing, invalid, expired or revoked.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::authenticated::sessions"
        }
      }
    },
    {
      "text": "The Product returns HTTP 401 for invalid held access without revealing protected summaries.",
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

# Sessions access refusal

## Trigger

Sessions is examined for the current range/project.

## Outcome

Protected summaries are not disclosed.

## Edge cases

- Dashboard summaries supply this population; at most 500 are selected upstream and the browser renders the first 80 after sorting.
- Selection starts transcript inspection; a summary can exist without a main transcript.
