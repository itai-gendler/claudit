---
{
  "scope": "Browser, access, documented source-file API, ingestion, pricing, export, health and operator measurement code at source commit 26656af231809e4061fa9e4534d8bd1aa04c5e20.",
  "method": "Static tracing of entry points, handlers, parsers, SQL persistence and browser consumers, with documentation and test-source corroboration.",
  "covered": [
    {
      "description": "Browser bootstrap, shell, audience routing, dashboard request state and chart population.",
      "paths": [
        "public/",
        "src/app.jsx",
        "src/dashboard-fetch.js",
        "src/dashboard-summary.jsx",
        "src/dashboard-binning.js",
        "src/dashboard-charts.jsx",
        "src/dashboard-charts-extra.jsx",
        "src/token-breakdown.js"
      ]
    },
    {
      "description": "Cache, session table, main-transcript inspector and context-growth browser consumers.",
      "paths": [
        "src/sessions-list.jsx",
        "src/detail-pane.jsx",
        "src/event-helpers.jsx",
        "src/timeline-selection.js",
        "src/context-growth-view.jsx",
        "src/views/"
      ]
    },
    {
      "description": "Credential entry, bounded worker admission, origin checks, cookie validation and external credential reads.",
      "paths": [
        "backend/login.py",
        "backend/login_page.py",
        "backend/login_workers.py",
        "backend/auth.py",
        "backend/session.py",
        "backend/db.py"
      ]
    },
    {
      "description": "Dashboard, cache, source-file, context, latency, export and small-panel handler queries and presentation.",
      "paths": [
        "backend/api.py",
        "backend/api_common.py",
        "backend/api_dashboard.py",
        "backend/api_cache.py",
        "backend/api_sessions.py",
        "backend/api_export.py",
        "backend/api_ctx_growth.py"
      ]
    },
    {
      "description": "Server lane parsing, token partitions, prompt/context bookkeeping and canonical browser request interpretation.",
      "paths": [
        "backend/parse.py",
        "backend/parse_common.py",
        "backend/parse_projection.py",
        "backend/parse_projection_usage.py",
        "backend/parse_codex.py",
        "backend/codex_fork.py",
        "backend/parse_kimi.py",
        "backend/kimi_content.py",
        "backend/parse_lanes.py",
        "backend/prompt_gate.py",
        "backend/turn_flags.py",
        "backend/ctx_input.py",
        "backend/ctx_turns.py",
        "src/parser.js",
        "src/parser-lanes.js",
        "src/parser-codex.js",
        "src/parser-usage.js",
        "src/record-dedup.js",
        "src/ctx-input.js",
        "src/parser-cache-write.js"
      ]
    },
    {
      "description": "Shared rate data, provider/date resolution, TTL and neutral-write pricing, long-context meters and rate fingerprints.",
      "paths": [
        "src/pricing.json",
        "src/rates.js",
        "backend/pricing.py",
        "backend/pricing_load.py",
        "backend/long_context.py",
        "backend/rate_boundaries.py",
        "backend/rate_fingerprint.py",
        "backend/pricing_document.py"
      ]
    },
    {
      "description": "Source listing, lane identity, sidecar classification, fetch/parse pipelines, per-file persistence and reconciliation lifecycle.",
      "paths": [
        "backend/app.py",
        "backend/ingest.py",
        "backend/ingest_scan.py",
        "backend/ingest_walk.py",
        "backend/ingest_fetch.py",
        "backend/ingest_resolve.py",
        "backend/ingest_persist.py",
        "backend/ingest_orphans.py",
        "backend/ingest_reprice.py",
        "backend/ingest_scope.py",
        "backend/ingest_lockwatch.py",
        "backend/key_layout.py",
        "backend/lane_projects.py",
        "backend/lane_markers.py",
        "backend/project_aliases.py",
        "backend/agent_sidecar.py",
        "backend/r2.py"
      ]
    },
    {
      "description": "Canonical/suppression/teammate reconstruction, hourly and latency rollups and stored usage schema.",
      "paths": [
        "backend/ingest_rollups.py",
        "backend/ingest_rollup_state.py",
        "backend/ingest_rollup_hourly.py",
        "backend/ingest_rollup_latency.py",
        "backend/schema.sql",
        "backend/schema_files.py",
        "backend/schema_replay.sql",
        "backend/schema_cache_write.sql",
        "backend/schema_request_fee.sql",
        "backend/schema_web_search.sql"
      ]
    },
    {
      "description": "Health progress and run records, response/transcript/blob freshness, cache warming and ingest completion events.",
      "paths": [
        "backend/ingest_progress.py",
        "backend/ingest_runs.py",
        "backend/ingest_warm.py",
        "backend/cache.py",
        "backend/cache_outcomes.py",
        "backend/blob_cache.py",
        "backend/events.py"
      ]
    },
    {
      "description": "Performance beacon validation/admission, recent and rolled-up readout, retention and operator display.",
      "paths": [
        "backend/api_web_metrics.py",
        "backend/web_metrics.py",
        "backend/ingest_rollup_web_metrics.py",
        "backend/schema_web_metrics.sql",
        "src/perf.js",
        "src/perf-panel.jsx"
      ]
    },
    {
      "description": "Web-export plot query population and branding escaping.",
      "paths": [
        "scripts/plots/ccusage_plot_db.py",
        "backend/branding.py"
      ]
    }
  ],
  "exclusions": [
    {
      "description": "Fixture and automated verification code used only as static supporting evidence.",
      "paths": [
        "tests/",
        "fixtures/"
      ]
    },
    {
      "description": "Repository instructions, contribution infrastructure and service deployment examples.",
      "paths": [
        ".agents/",
        ".claude/",
        "examples/",
        "CONTRIBUTING.md"
      ]
    }
  ],
  "unmapped": [
    {
      "description": "Independent compatibility JSON contracts beyond the documented source-file routes.",
      "paths": [
        "backend/api.py",
        "backend/api_sessions.py"
      ]
    },
    {
      "description": "Standalone plotting entry and complete renderer/timeline contract beyond the web export hand-off.",
      "paths": [
        "scripts/plots/"
      ]
    },
    {
      "description": "External rate-catalog refresh, rate selection and pricing publication tooling.",
      "paths": [
        "scripts/ci/",
        ".github/workflows/refresh-pricing.yml"
      ]
    },
    {
      "description": "Exhaustive shell/ARGV churn scanners, lexical path and intake classification and granular tool-failure distinctions.",
      "paths": [
        "backend/bash_argv.py",
        "backend/bash_churn.py",
        "backend/bash_churn_errors.py",
        "backend/bash_dash_c.py",
        "backend/bash_heredocs.py",
        "backend/bash_literals.py",
        "backend/bash_loops.py",
        "backend/bash_reads.py",
        "backend/target_paths.py",
        "backend/tool_errors.py"
      ]
    },
    {
      "description": "External provisioning and SQL/privacy/backup procedures beyond settings and credential behavior consumed by the app.",
      "paths": [
        "PRIVACY.md",
        "backend/.env.example",
        "backend/db.py"
      ]
    },
    {
      "description": "Synthetic-preview data and shell branch as an independently supported workflow.",
      "paths": [
        "src/synthetic-data.js",
        "src/app.jsx"
      ]
    }
  ],
  "limitations": [
    {
      "description": "Session/file reconstruction does not settle a separately kept sidecar identity or a deterministic winner among multiple main files.",
      "paths": [
        "backend/key_layout.py",
        "backend/api_sessions.py",
        "backend/ingest_rollup_state.py"
      ]
    },
    {
      "description": "Different pricing/population projections establish observed calculations but no universal reconciliation contract across stored rollups, cache, Inspector and PNG.",
      "paths": [
        "backend/api_dashboard.py",
        "backend/api_cache.py",
        "src/parser.js",
        "scripts/plots/ccusage_plot_db.py"
      ]
    },
    {
      "description": "Transient proof, cookie possession and population admission are checked in code; schema-11 grant conditions cannot express all of them as kept-instance facts.",
      "paths": [
        "backend/login.py",
        "backend/session.py",
        "backend/app.py",
        "backend/api_web_metrics.py"
      ]
    }
  ]
}
---

# Coverage
