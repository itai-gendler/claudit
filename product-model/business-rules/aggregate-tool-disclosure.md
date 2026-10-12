---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "tool-call",
      "effect": "reads",
      "facts": [
        "Name",
        "Model",
        "Settlement",
        "Error outcome",
        "Churn",
        "Counted status"
      ],
      "contexts": [
        {
          "place": "claudit-web::public::overview"
        },
        {
          "place": "claudit-web::authenticated::overview"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_dashboard.py"
    }
  ],
  "permits": [
    {
      "actors": [
        "guest",
        "user",
        "web-operator"
      ]
    }
  ]
}
---

# Admitted readers receive aggregate tool statistics

Every selected disclosure requires valid presented access. Account access must resolve the current credential binding and account revocation; guest access must pass its process-bound signature and age checks. No project/session ownership filter is applied to account readers. Public tool statistics include name/model, settled/error outcome counts, churn and counted status. Detailed arguments, results, failure text, dispatch details and targets are not part of this public grant.
