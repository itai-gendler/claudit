---
{
  "kind": "edge",
  "routes": {
    "overview": "Overview",
    "cache": "Cache",
    "sessions": "Sessions",
    "inspector": "Inspector"
  },
  "steps": [
    {
      "text": "The User chooses Export usage for the currently selected range and filter.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        },
        "cache": {
          "place": "claudit-web::authenticated::cache"
        },
        "sessions": {
          "place": "claudit-web::authenticated::sessions"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    },
    {
      "text": "The renderer finds no selected data.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        },
        "cache": {
          "place": "claudit-web::authenticated::cache"
        },
        "sessions": {
          "place": "claudit-web::authenticated::sessions"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    },
    {
      "text": "The Product returns HTTP 404 reports no data to render for the selected range or filter; no download is produced.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        },
        "cache": {
          "place": "claudit-web::authenticated::cache"
        },
        "sessions": {
          "place": "claudit-web::authenticated::sessions"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_export.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "scripts/plots/ccusage_plot_db.py#load_events"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#TopBar"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/branding.py"
    }
  ]
}
---

# Usage PNG no data

## Trigger

Export is requested from the current dashboard place.

## Outcome

HTTP 404 reports no data to render for the selected range or filter; no download is produced.

## Edge cases

- The renderer uses its own duplicate ordering and population; parity with Overview is not guaranteed.
- Branding and project/range selection determine the safe export filename.
