---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transcript",
      "effect": "reads",
      "facts": [
        "Models",
        "Agent attribution",
        "Prompt count",
        "Context turns",
        "Rate-limit hits",
        "Main designation"
      ],
      "contexts": [
        {
          "place": "claudit-web::public"
        },
        {
          "place": "claudit-web::authenticated"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_ctx_growth.py"
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

# Admitted readers receive numeric transcript observations

Every selected disclosure requires valid presented access. Account access must resolve the current credential binding and account revocation; guest access must pass its process-bound signature and age checks. No project/session ownership filter is applied to account readers. Numeric context, model/agent grouping, prompt and rate-limit observations do not grant transcript contents or source addresses.
