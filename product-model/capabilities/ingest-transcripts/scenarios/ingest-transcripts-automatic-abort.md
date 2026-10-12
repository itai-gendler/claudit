---
{
  "kind": "edge",
  "routes": {
    "status": "Status"
  },
  "steps": [
    {
      "text": "Shutdown interrupts scheduled reconciliation.",
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
      "text": "The Product reports the scheduled run closes aborted, retaining committed partial work without ordinary derived completion, warming or changed-data notification.",
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

# Scheduled ingestion abort

## Trigger

The Product-owned startup/hourly schedule is due.

## Outcome

The scheduled run closes aborted, retaining committed partial work without ordinary derived completion, warming or changed-data notification.

## Edge cases

- Per-file committed work is not rolled back as one whole-run transaction.
- A concurrent skip can leave the previous status visible.
- Success notification requires actual changed data and no fatal/abort; it does not refresh every browser consumer.
