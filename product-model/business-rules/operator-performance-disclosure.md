---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "performance-measurement",
      "effect": "reads",
      "contexts": [
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
      "target": "backend/session.py#is_operator"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_web_metrics.py#web_metrics_route"
    }
  ],
  "permits": [
    {
      "actors": [
        "web-operator"
      ]
    }
  ]
}
---

# Only Web operator reads page performance

The caller must resolve a valid account session and be classified as Web operator from its own Account Operator access literal boolean true. Guests, absent flags, strings and other truthy values do not classify the caller. Admin bearer proof does not establish this web role. The entitlement belongs to the caller, not to a globally readable measurement.
