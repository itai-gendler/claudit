---
{
  "access": "authenticated",
  "actors": [
    "user",
    "web-operator"
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#auth_middleware"
    }
  ]
}
---

# Authenticated dashboard

Account readers examine shared usage, select sessions, inspect a main transcript and export usage.
