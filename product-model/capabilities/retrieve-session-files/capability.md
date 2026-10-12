---
{
  "availability": [
    {
      "place": "claudit-api::session-files"
    }
  ],
  "references": [
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
  ]
}
---

# Retrieve session files

Retrieve the selected main transcript or source bytes within the session-relative scope established from a main transcript.
