---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "coding-session",
      "effect": "reads",
      "facts": [
        "Identity",
        "Activity span",
        "Usage summary"
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
      "target": "backend/api_dashboard.py#dashboard_route"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_ctx_growth.py#context_growth_session"
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

# Admitted readers receive numeric session usage

Every selected disclosure requires valid presented access. Account access must resolve the current credential binding and account revocation; guest access must pass its process-bound signature and age checks. No project/session ownership filter is applied to account readers. Numeric identifiers and individual context observations can remain in guest-accessible data; public access is not a guarantee that all session identifiers are hidden.
