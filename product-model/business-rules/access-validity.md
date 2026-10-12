---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "web-session",
      "facts": [
        "Expiry",
        "Validity"
      ]
    },
    {
      "type": "entity",
      "id": "account",
      "facts": [
        "Credential binding",
        "Access revocation",
        "Operator access"
      ]
    }
  ],
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#is_operator"
    }
  ]
}
---

# Access expires and remains credential and revocation bound

Issued access lasts seven days and rejects invalid signatures, malformed/obsolete tokens and timestamps more than sixty seconds ahead. Account access requires the current revocation and accepted credential binding. The external account must still exist and match its last-login credentials through the at-most-sixty-second configuration cache. Guest signatures use a process secret, so guest access dies on restart. Web operator classification uses only literal boolean true on the caller account. Cookies are HttpOnly, SameSite strict, and Secure under the configured cookie mode.
