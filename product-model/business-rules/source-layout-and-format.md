---
{
  "appliesTo": [
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
    },
    {
      "type": "capability",
      "id": "retrieve-session-files",
      "contexts": [
        {
          "place": "claudit-api::session-files"
        }
      ]
    },
    {
      "type": "entity",
      "id": "project",
      "facts": [
        "Identity"
      ]
    },
    {
      "type": "entity",
      "id": "coding-session",
      "facts": [
        "Identity",
        "Session file scope"
      ]
    },
    {
      "type": "entity",
      "id": "transcript",
      "facts": [
        "Object path",
        "Main designation"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/key_layout.py#classify"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_lanes.py#sniff_format"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/r2.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_sidecar"
    }
  ]
}
---

# Imported identity follows configured layouts and content-selected formats

Configured buckets or the local mirror supply Claude project/session transcript layouts and lane sessions/project/session wire layouts, including agent files and compressed sources. Bucket-qualified identities avoid cross-bucket collisions. Content sniffing selects Claude, Codex, kimi-code or legacy Kimi parsing. Malformed JSON and nonobject lines are skipped under parser policy; they do not alone establish a fatal whole-file failure. File-mode realpath joining refuses traversal outside its source root. Session-associated retrieval establishes its prefix from a main and rejects leading separators, dot/dot-dot components and NUL before fetching; an empty required relative address is parameter validation.
