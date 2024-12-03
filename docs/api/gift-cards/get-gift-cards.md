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

You can optionally filter your results by one or more of the following query parameters:

| Name          | Type          | Mandatory? | Constraints | Notes |
| ------------- | ------------- | ---        | ---         | ---   |
| card_id       | string        | no         | -           | -     |
| user_id       | string        | no         | -           | -     |
| issuer        | string        | no         | -           | -     |
| balance       | float          | no         | -           | -     |
| expiry_date   | date          | no         | -           | -     |

If you submit no query parameters, the system will return the full array of Gift Cards.

## Request data

None

## Response data

| Name          | Type          | Mandatory? | Constraints     | Notes |
| ------------- | ------------- | ---        | ---             | ---   |
| id            | int           | yes        | Must be unique. | Internal unique ID assigned by the system. |
| card_id       | string        | no         | -               | Unique ID provided by the issuer of the card. |
| user_id       | string        | no         | -               | The user associated with the payment card. |
| issuer        | string        | no         | -               | The merchant that issued the payment card. |
| balance       | float          | no         | -               | How much money is left on the card.        |
| expiry_date   | date          | no         | -               | Date the gift card expires. |

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example requests and responses

### Get all Gift Cards

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

### Filter Gift Cards by their issuer

Request:

```shell
curl -GET "http://localhost:3000/gift_cards?issuer=Hanes"
```

Response:

```json
[
  {
    "card_id": "hanes-gc-003",
    "user_id": "user004",
    "issuer": "Hanes",
    "balance": 10,
    "expiry_date": "2026-12-31",
    "id": 1
  },
  {
    "id": 5,
    "card_id": "hanes-gc-002",
    "user_id": "user004",
    "issuer": "Hanes",
    "balance": 50,
    "expiry_date": "2025-12-31"
  }
]
```

### Filter Gift Cards by their issuer and balance

Request:

```shell
curl -GET "http://localhost:3000/gift_cards?issuer=Hanes&balance=50"
```

Response:

```json
[
  {
    "card_id": "hanes-gc-003",
    "user_id": "user004",
    "issuer": "Hanes",
    "balance": 50,
    "expiry_date": "2026-12-31",
    "id": 1
  },
  {
    "id": 5,
    "card_id": "hanes-gc-002",
    "user_id": "user004",
    "issuer": "Hanes",
    "balance": 50,
    "expiry_date": "2025-12-31"
  }
]
```

## Links

* [Documentation Home](../../index.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [REST API Reference](../index.md)
* [Gift Card Resource](index.md)
* [Support](mailto:support@example.com)