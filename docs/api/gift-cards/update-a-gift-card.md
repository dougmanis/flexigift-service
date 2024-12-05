---
layout: page
---

# Update a Gift Card

The Update a Gift Card service changes the details for a given card.

## URL

```shell
{base_url}/gift_cards/{id}
```

## HTTP method

PUT

## Request headers

None

## Request parameters

Path parameters:

| Name          | Type          | Mandatory? | Constraints     | Notes |
| ------------- | ------------- | ---        | ---             | ---   |
| id            | int           | yes        |                 | Internal unique ID assigned by the system. |

## Request data

| Name          | Type          | Mandatory? | Constraints    | Notes |
| ------------- | ------------- | ---        | ---            | ---   |
| card_id       | string        | no         | -              | Unique identifier provided by the issuer of the card. |
| user_id       | string        | no         | -              | The user associated with the payment card. |
| issuer        | string        | no         | -              | The merchant that issued the payment card. |
| balance       | float          | no         | -              | How much money is left on the card.        |
| expiry_date   | date          | no         | -              | Date the gift card expires. |

## Response data

A successful request returns the data you submitted plus the card's unique {id}:

| Name          | Type          | Mandatory? | Constraints     | Notes |
| ------------- | ------------- | ---        | ---             | ---   |
| id            | int           | yes        | -               | -     |
| card_id       | string        | no         | -               | -     |
| user_id       | string        | no         | -               | -     |
| issuer        | string        | no         | -               | -     |
| balance       | float          | no         | -               | -     |
| expiry_date   | date          | no         | -               | -     |

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example request and response

Request:

```shell
curl -XPUT -H "Content-type: application/json" -d '  {
    "card_id": "hanes-gc-003",
    "user_id": "user004",
    "issuer": "Hanes",
    "balance": 10,
    "expiry_date": "2026-12-31"
  }' 'http://localhost:3000/gift_cards/1'
```

Response:

```json
{
  "card_id": "hanes-gc-003",
  "user_id": "user004",
  "issuer": "Hanes",
  "balance": 10,
  "expiry_date": "2026-12-31",
  "id": 1
}
```

## Links

* [Documentation Home](../../index.md)
* [Quick Start](../../quickstart.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [API Reference](../../api/index.md)
* [Transactions Resource](index.md)
* [Support](mailto:support@example.com)