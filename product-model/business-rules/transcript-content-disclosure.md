---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transcript",
      "effect": "reads",
      "facts": [
        "Contents",
        "Object path"
      ],
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        },
        {
          "place": "claudit-api::session-files"
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

# Transcript contents and addresses are credentialed

Valid account access is required for contents and object addresses. Guest sessions are denied all session endpoints. Main retrieval returns one eligible main; admitted associated files are fetched within the prefix established from that main.
