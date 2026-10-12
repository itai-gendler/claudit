---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account",
      "effect": "changes",
      "facts": [
        "Operator access"
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
      "target": "backend/db.py"
    }
  ],
  "permits": []
}
---

# Operator entitlement is not assigned here

These Interfaces never grant or change the externally maintained operator entitlement.
