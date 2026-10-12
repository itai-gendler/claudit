---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Billed tokens"
      ],
      "contexts": [
        {
          "place": "claudit-web::public::cache"
        },
        {
          "place": "claudit-web::authenticated::cache"
        },
        {
          "place": "claudit-web::authenticated::inspector"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_cache.py#_session_total"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/parser.js#computeSessionStats"
    }
  ]
}
---

# Cache-hit percentage uses total billed input

The hit percentage is 100*reads/(fresh + total billed creation + reads), with zero for a zero denominator. Neutral inferred writes do not replace billed creation in this denominator.
