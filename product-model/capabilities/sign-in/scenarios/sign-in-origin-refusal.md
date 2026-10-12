---
{
  "kind": "validation",
  "routes": {
    "web": "Sign in"
  },
  "steps": [
    {
      "text": "The User submits an identifier and credential proof.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The submitted origin evidence is absent or mismatched.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The Product returns HTTP 403 reports Forbidden (cross-origin) before credential verification or access issuance.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#login_post"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#login_guest"
    }
  ]
}
---

# Credential entry origin refused

## Trigger

Entry is submitted from Sign in.

## Outcome

HTTP 403 reports Forbidden (cross-origin) before credential verification or access issuance.

## Edge cases

- The same matching-origin check also applies to guest entry.
