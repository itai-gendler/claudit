---
{
  "kind": "primary",
  "routes": {
    "web": "Sign in"
  },
  "steps": [
    {
      "text": "The Guest chooses guest entry.",
      "kind": "actor",
      "entities": [],
      "actor": "guest",
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "Entry without credential proof is selected.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The Product issues a Guest-audience Web session and returns to Overview.",
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
      "actor": "guest",
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

# Guest entry

## Trigger

Entry is submitted from Sign in.

## Outcome

Guest access is issued and guest Overview opens.
