---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#verify_session_token"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#resolve_session_user_id"
    }
  ]
}
---

# Web session

Issued dashboard access presented by its holder. The product distinguishes account-bound and guest access without exposing internal secret or fingerprint records.

## Information kept

- **Audience** — Guest or Account access.
- **Holder** — The account or possession-based guest audience presenting the access.
- **Issued time** — When access was issued.
- **Expiry** — The seven-day lifetime of issued access.
- **Validity** — Whether signature, age, applicable credential binding and revocation checks accept the presented access.
