---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Estimated cost"
      ],
      "contexts": [
        {
          "place": "claudit-web::public::overview"
        },
        {
          "place": "claudit-web::authenticated::overview"
        }
      ]
    },
    {
      "type": "entity",
      "id": "deployment-settings",
      "facts": [
        "Rate-limit display"
      ]
    },
    {
      "type": "capability",
      "id": "browse-usage",
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
      "target": "src/app.jsx#Dashboard"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/.env.example"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_dashboard.py"
    }
  ]
}
---

# Zero-cost and rate-limit display do not change imported population

Zero-cost usage remains available; applicable Overview cost-only panels are omitted rather than hiding token usage. This is not a universal omission of every zero-cost value on Cache. The configured rate-limit display switch changes presentation while imported rate-limit information remains retained.
