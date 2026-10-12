---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account",
      "effect": "changes",
      "facts": [
        "Credential binding"
      ],
      "contexts": [
        {
          "place": "claudit-web::public::sign-in"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#_bind_verified_credentials"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "has",
          "entity": "user"
        }
      ]
    },
    {
      "related": [
        {
          "verb": "has",
          "entity": "web-operator"
        }
      ]
    }
  ]
}
---

# Verified entry binds account credentials

Binding changes only for the account whose current externally maintained credential proof was verified. The credential is freshly reread and compared before binding; stale proof receives generic rejection rather than a new binding.
