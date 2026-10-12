---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#make_guest_session_token"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#_guest_denied"
    }
  ],
  "acts": "external",
  "kind": "person",
  "relations": [
    {
      "entity": "web-session",
      "verb": "holds",
      "cardinality": "many-to-many"
    }
  ]
}
---

# Guest

A person using presented guest dashboard access. Possession does not establish a uniquely tracked guest identity.
