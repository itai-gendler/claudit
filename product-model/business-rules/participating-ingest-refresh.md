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
      "type": "capability",
      "id": "browse-usage",
      "contexts": [
        {
          "place": "claudit-web::public"
        },
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "capability",
      "id": "browse-sessions",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "capability",
      "id": "inspect-transcript",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest.py#_run_ingest_locked"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/events.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#App"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/views/cache-view.jsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/views/context-growth-view-v2.jsx"
    }
  ]
}
---

# Changed ingestion refreshes participating consumers

Successful changed ingestion invalidates aggregate response entries and broadcasts ingest_done after derived reconciliation; fatal/aborted runs do not perform ordinary successful notification. Fingerprint-only restamping does not itself imply changed data. The web shell refreshes Overview and participating nonce-dependent consumers; Cache, context distributions, an already loaded Inspector and the initial model-list fetch do not all depend on that nonce. Superseded requests do not replace the current selection.
