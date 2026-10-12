---
{
  "kind": "edge",
  "routes": {
    "status": "Status"
  },
  "steps": [
    {
      "text": "Scheduled listing/derived work fails fatally or the ingest lock is lost.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        }
      },
      "unattended": true
    },
    {
      "text": "The Product reports scheduled failure closes with error information and partial counts; ordinary completion, cache warming and changed-data notification are skipped.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        }
      }
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

# Scheduled ingestion fatal

## Trigger

The Product-owned startup/hourly schedule is due.

## Outcome

Scheduled failure closes with error information and partial counts; ordinary completion, cache warming and changed-data notification are skipped.

## Edge cases

- Per-file committed work is not rolled back as one whole-run transaction.
- A concurrent skip can leave the previous status visible.
- Success notification requires actual changed data and no fatal/abort; it does not refresh every browser consumer.
