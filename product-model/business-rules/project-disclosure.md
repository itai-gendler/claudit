---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "project",
      "effect": "reads",
      "facts": [
        "Identity",
        "Display name",
        "Activity span"
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
      "target": "backend/session.py#_guest_denied"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_dashboard.py#dashboard_route"
    }
  ],
  "permits": [
    {
      "actors": [
        "user",
        "web-operator"
      ]
    }
  ]
}
---

# Project information is credentialed disclosure

Every selected disclosure requires valid presented access. Account access must resolve the current credential binding and account revocation; guest access must pass its process-bound signature and age checks. No project/session ownership filter is applied to account readers. Guest requests for project endpoints or a nonempty project filter are refused; public dashboard responses omit project cost/token groups.
