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
  ],
  "entryPoints": [
    {
      "claudit-api": "/api/sessions/{session_id}/transcript"
    },
    {
      "claudit-api": "/api/sessions/{session_id}/sidecar"
    }
  ]
}
---

# Session files

Account readers retrieve a main transcript or source files within its established session scope.
