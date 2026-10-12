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
      "text": "The renderer fails for another reason.",
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
      "text": "The Product reports other nonzero rendering exits produce HTTP 500 with export render failed; no PNG is returned.",
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

# Usage PNG failure

## Trigger

Export is requested from the current dashboard place.

## Outcome

Other nonzero rendering exits produce HTTP 500 with export render failed; no PNG is returned.

## Edge cases

- The renderer uses its own duplicate ordering and population; parity with Overview is not guaranteed.
- Branding and project/range selection determine the safe export filename.
