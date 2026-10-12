---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "ingest-transcripts",
      "contexts": [
        {
          "place": "claudit-api::maintenance"
        },
        {
          "place": "claudit-api::status"
        },
        {
          "place": "claudit-web::public"
        },
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "entity",
      "id": "project"
    },
    {
      "type": "entity",
      "id": "coding-session"
    },
    {
      "type": "entity",
      "id": "transcript"
    },
    {
      "type": "entity",
      "id": "request"
    },
    {
      "type": "entity",
      "id": "tool-call"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest.py#_walk_and_persist"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_persist.py#_persist"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_orphans.py"
    }
  ]
}
---

# Replacement is atomic per source file

Each parsed file persists in one transaction, replacing its request/tool facts together. The run is not one corpus-wide transaction: partial failures, fatal errors and aborts can preserve committed earlier files. Complete listing evidence precedes ordinary orphan removal; incomplete/fatal scans do not justify ordinary disappearance cleanup. Successful disappearance cleanup removes derived occurrences and evicts raw cached bytes after commit. Source objects remain untouched.
