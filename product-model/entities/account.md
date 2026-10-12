---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#get_or_create_session_row"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#bump_session_generation"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/auth.py"
    }
  ],
  "relations": [
    {
      "entity": "web-session",
      "verb": "holds",
      "cardinality": "one-to-many"
    }
  ]
}
---

# Account

The externally managed identity whose credentials and entitlement determine issued dashboard access.

## Information kept

- **User identifier** — The externally assigned positive account identifier.
- **Web credentials** — Externally maintained password verification information; plaintext submissions are not kept.
- **Operator access** — The external boolean entitlement used to classify Web operator.
- **Credential binding** — The accepted credential identity to which issued access remains bound.
- **Access revocation** — The account-wide revocation of previously issued access; successful logout advances revocation.
