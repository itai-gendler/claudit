---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_projection.py#project_records"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_codex.py#_codex_token_count"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_lanes.py#to_claudit"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_state.py#recompute_canonical"
    }
  ]
}
---

# Request

An identified usage occurrence retained from a transcript. Logical identity can recur across files; counted status selects the canonical population.

## Information kept

- **Identity** — Request or message identity, or the supported source-local fallback.
- **Time** — Recorded usage time used for selection and dated rates.
- **Model** — Recorded, adopted or format-inferred model attribution.
- **Provider** — Recorded provider when available.
- **Billed tokens** — Fresh input, total billed cache creation, reads and output under the lane policy.
- **TTL creation** — Explicit five-minute and one-hour creation counts, separate from unsplit creation.
- **Thinking tokens** — The recorded reasoning/thinking subset of output.
- **Neutral cache writes** — Provider-neutral cache-write measurement, distinct from billed creation.
- **Search count** — Explicit admissible web-search request count.
- **Estimated cost** — Stored per-request estimate, rounded to six decimals, or the explicitly surface-specific browser estimate.
- **Rate classification** — Resolved exact, family/default estimate and scheduled/banded distinctions.
- **Meter treatment** — Applicable threshold decision and effective whole-request input/output factors.
- **Context input** — The parser-selected context-input measurement, including peak iteration treatment where applicable.
- **Visible reply size** — Recorded visible response character quantity.
- **Reply latency** — Eligible prompt-to-reply latency when an anchor exists.
- **Request metadata** — Available closing reason, effort, CLI version, turn flags and tool-result count.
- **Counted status** — Canonical/replayed classification selecting counted usage.
- **Source line** — The numeric transcript line locating the usage occurrence, including guest-visible top requests.
- **Source location** — The transcript address locating the occurrence; guest payloads omit this address.
