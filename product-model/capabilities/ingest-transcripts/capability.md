---
{
  "availability": [
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
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/app.py#admin_ingest"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest.py#run_ingest"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest.py#_run_ingest_locked"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_persist.py#_persist"
    }
  ]
}
---

# Ingest transcripts

Reconcile configured source transcripts, imported facts and derived populations in one initiated run. Startup and hourly runs perform the same reconciliation unattended.
