---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "coding-session",
      "effect": "reads",
      "contexts": [
        {
          "place": "claudit-api::session-files"
        },
        {
          "place": "claudit-web::authenticated::sessions"
        },
        {
          "place": "claudit-web::authenticated::inspector"
        }
      ]
    },
    {
      "type": "entity",
      "id": "coding-session",
      "effect": "reads",
      "facts": [
        "Project",
        "Transcript membership",
        "Session file scope"
      ],
      "contexts": [
        {
          "place": "claudit-web::authenticated::overview"
        },
        {
          "place": "claudit-web::authenticated::cache"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#_guest_denied"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_transcript"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_sidecar"
    }
  ],
  "permits": [
    {
      "actors": [
        "user",
        "web-operator"
      ]
    }
  ]
}
---

# Detailed session and file scope is credentialed

Session endpoints and source-file scope require valid non-guest account access. Detailed project/membership/file-scope disclosures are for account readers; publicly readable numeric summaries do not grant access to these endpoints.
