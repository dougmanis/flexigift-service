---
layout: page
---

# Get Gift Cards

The Get Gift Cards service returns an array of the gift cards in the system along with their details.

## URL

```shell
{base_url}/gift_cards
```

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
| ------------- | ------------- | ---        | ---         | ---   |
| card_id       | string        | true       | -           | Unique ID. This value is provided by the issuer of the card. |
| user_id       | string        | true       | -           | The user associated with the payment card. |
| issuer        | string        | true       | -           | The merchant that issued the payment card. |
| balance       | float          | true       | -           | How much money is left on the card.        |
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
    "user_id": "user001",
    "issuer": "Hanes",
    "balance": 50,
    "expiry_date": "2025-12-31"
  },
  {
    "card_id": "nike-gc-002",
    "user_id": "user001",
    "issuer": "Nike",
    "balance": 100,
    "expiry_date": "2024-11-30"
  },
  {
    "card_id": "starbucks-gc-003",
    "user_id": "user002",
    "issuer": "Starbucks",
    "balance": 25,
    "expiry_date": "2024-06-30"
  },
  {
    "card_id": "gap-gc-004",
    "user_id": "user003",
    "issuer": "Gap",
    "balance": 75,
    "expiry_date": "2025-05-15"
  },
  {
    "card_id": "hanes-gc-001",
    "user_id": "user004",
    "issuer": "Hanes",
    "balance": 50,
    "expiry_date": "2025-12-31"
  }
]
```
## Links

* [Documentation home](../../index.md)
* [API reference](../../api/index.md)
* [Support](mailto:support@example.com)