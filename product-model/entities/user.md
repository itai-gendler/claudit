---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#login_post"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#resolve_session_user_id"
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

# User

A person entering with an externally managed account and examining the shared deployment corpus.
