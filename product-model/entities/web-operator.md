---
{
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
  "acts": "external",
  "kind": "person",
  "relations": [
    {
      "entity": "account",
      "verb": "has",
      "cardinality": "one-to-one"
    }
  ]
}
---

# Web operator

An account role with the additional responsibility of reading page performance. The role is classified only when the caller account operator entitlement is literally true; guest access and the maintenance credential do not establish this role.
