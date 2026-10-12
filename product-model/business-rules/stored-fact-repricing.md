---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Estimated cost",
        "Meter treatment",
        "Model",
        "Provider",
        "Time"
      ]
    },
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
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/rate_fingerprint.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_reprice.py#_record_updates"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_reprice.py#reprice_stale"
    }
  ]
}
---

# Repricing uses stored facts and pricing provenance

Changed pricing inputs/logic are fingerprinted per model/provider. Repricing recomputes stored request cost and applicable context treatment without fetching source transcripts. Effective factor pairs preserve batch provenance. Meter members recompute threshold decisions; nonmembers with stored true treatment are rechecked, while false/null treatment is retained. Newer stored pricing versions are protected from an older binary. Clean fingerprint restamping alone is not changed-data repricing and does not force the same rebuild/notification.
