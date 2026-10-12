---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/.env.example"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/branding.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/project_aliases.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_state.py#purge_suppressed"
    }
  ],
  "singleton": true
}
---

# Deployment settings

The single deployment configuration consumed by source reconciliation, display and maintenance admission.

## Information kept

- **Transcript sources** — Configured buckets/object storage or local mirror.
- **Project aliases** — Externally configured project identity folds.
- **Suppressed models** — Externally configured model patterns omitted from counted request/tool information.
- **Admin credential configuration** — The configured maintenance credential requirement, without exposing its value.
- **Branding** — Configured product display identity.
- **Privacy link** — The accepted configured privacy-link destination.
- **Rate-limit display** — The deployment choice controlling rate-limit presentation.
