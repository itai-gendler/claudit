---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account",
      "effect": "changes",
      "facts": [
        "Web credentials"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/db.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/auth.py"
    }
  ],
  "permits": []
}
---

# External credentials are not edited

These Interfaces never change externally maintained web password verification information.
