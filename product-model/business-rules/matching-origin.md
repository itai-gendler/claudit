---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "web-session",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "performance-measurement",
      "effect": "creates"
    },
    {
      "type": "capability",
      "id": "ingest-transcripts",
      "contexts": [
        {
          "place": "claudit-api::maintenance"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#check_origin"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#auth_middleware"
    }
  ]
}
---

# Mutating entry requires matching-origin evidence

Mutating requests require Host and matching Origin, or matching Referer when Origin is absent. Missing/mismatched evidence is refused before the selected operation. Credential/guest entry, maintenance ingestion and measurement storage share this requirement. Safe reads are exempt; GET logout relies on SameSite strict and clears only the presented cookie.
