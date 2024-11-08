---
layout: page
---

# Get Gift Cards

The Get Gift Cards service returns a list of the gift cards in the system along with their details.

## URL

{host}/gift_cards

## HTTP method

GET

## Request headers

None

## Request parameters

None

## Request data

None

## Response data

| Name          | Type          | Mandatory? | Constraints | Notes |
| ------------- | ------------- | ---        | ---         | ---         |
| card_id       | string        | true       | -           | Unique ID of the user assigned to the task. |
| issuer        | string        | true       | -           | -           |
| balance       | float         | true       | -           | -           |
| expiry_date   | date          | true       | -           | Date the gift card expires. |

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example request and response

Request:
```shell
curl http://localhost:3000/gift_cards
```

Response:
```json
[
  {
    "card_id": "hanes-gc-001",
    "issuer": "Hanes",
    "balance": 50,
    "expiry_date": "2025-12-31"
  },
  {
    "card_id": "nike-gc-002",
    "issuer": "Nike",
    "balance": 100,
    "expiry_date": "2024-11-30"
  },
  {
    "card_id": "starbucks-gc-003",
    "issuer": "Starbucks",
    "balance": 25,
    "expiry_date": "2024-06-30"
  },
  {
    "card_id": "gap-gc-004",
    "issuer": "Gap",
    "balance": 75,
    "expiry_date": "2025-05-15"
  }
]
```