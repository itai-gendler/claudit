---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse.py#_tool_use_row"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse.py#_resolve_tool_errors"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_common.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/detail-pane.jsx#ToolCallDetail"
    }
  ]
}
---

# Tool call

An identified tool occurrence with its arguments, settlement and supported per-call statistics.

## Information kept

- **Identity** — Tool-use identity or source-local occurrence identity.
- **Time** — Recorded invocation time.
- **Name** — The recorded tool name.
- **Model** — Attributed model.
- **Arguments** — Recorded invocation input.
- **Result** — Available paired result content.
- **Settlement** — Whether a corresponding result settled the invocation.
- **Error outcome** — Aggregate success/failure classification, without failure text.
- **Failure details** — Detailed failure classification and result text.
- **Churn** — Supported literal per-call added/deleted line counts.
- **Dispatch attribution** — Detailed agent dispatch metadata and role/model attribution.
- **Targets** — Lexical read/write targets in the transcript namespace.
- **Counted status** — Canonical classification selecting aggregate tool statistics.
