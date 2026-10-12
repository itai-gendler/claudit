---
{
  "appliesTo": [
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
      "id": "inspect-transcript",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "capability",
      "id": "export-usage",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Estimated cost",
        "Counted status"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#backendDashToShape"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/token-breakdown.js"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/parser.js#computeSessionStats"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "scripts/plots/ccusage_plot_db.py#load_events"
    }
  ]
}
---

# Cost surfaces use source-specific populations and inputs

Overview hourly/browser reconstruction lacks full unsplit creation and search counts and does not preserve Cache complete rate-epoch/stored-factor grouping. Inspector prices only the fetched main transcript and does not inherit complete ingest-level cross-file canonicalization/model adoption or all subagents. PNG queries use different DISTINCT ON duplicate ordering and filter population. These computations remain distinct estimates without universal cost reconciliation.
