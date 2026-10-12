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
      "text": "Another rendering operation holds the slot.",
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
      "text": "The Product returns HTTP 503 reports that an export is already in progress; no overlapping render starts.",
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

# Usage PNG busy

## Trigger

Export is requested from the current dashboard place.

## Outcome

HTTP 503 reports that an export is already in progress; no overlapping render starts.

## Edge cases

- The renderer uses its own duplicate ordering and population; parity with Overview is not guaranteed.
- Branding and project/range selection determine the safe export filename.
