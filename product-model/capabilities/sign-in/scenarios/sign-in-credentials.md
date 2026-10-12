---
{
  "kind": "primary",
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
      "text": "The supplied proof matches the current externally managed credentials.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The Product checks current Account credentials.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "reads",
          "facts": [
            "User identifier",
            "Web credentials"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The Product binds verified Account credentials and access revocation.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Credential binding",
            "Access revocation"
          ]
        }
      ],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The Product issues a Web session and returns to Overview.",
      "kind": "product",
      "entities": [
        {
          "entity": "web-session",
          "effect": "creates",
          "facts": [
            "Audience",
            "Holder",
            "Issued time",
            "Expiry",
            "Validity"
          ]
        }
      ],
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

# Credentialed entry

## Trigger

Entry is submitted from Sign in.

## Outcome

Account-bound access is issued and Overview opens.

## Edge cases

- Credential proof is freshly reread before binding; a changed credential follows generic rejection.
