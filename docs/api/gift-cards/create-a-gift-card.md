---
layout: page
---

# Create a Gift Card

The Create a Gift Card service injects a new card into the system.

## URL

```shell
{base_url}/gift_cards
```

## HTTP method

POST

## Request headers

None

## Request parameters

None

## Request data

| Name          | Type          | Mandatory? | Constraints    | Notes |
| ------------- | ------------- | ---        | ---            | ---   |
| card_id       | string        | no         | -              | Unique identifier provided by the issuer of the card. |
| user_id       | string        | no         | -              | The user associated with the payment card. |
| issuer        | string        | no         | -              | The merchant that issued the payment card. |
| balance       | float          | no         | -              | How much money is left on the card.        |
| expiry_date   | date          | no         | -              | Date the gift card expires. |

## Response data

A successful request returns the data you submitted plus a unique ID:

| Name          | Type          | Mandatory? | Constraints     | Notes |
| ------------- | ------------- | ---        | ---             | ---   |
| id            | int           | yes        | Must be unique. | Internal unique ID assigned by the system. |
| card_id       | string        | no         | -               | - |
| user_id       | string        | no         | -               | - |
| issuer        | string        | no         | -               | - |
| balance       | float          | no         | -               | - |
| expiry_date   | date          | no         | -               | - |

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 201           | Created       | -     |

## Example request and response

Request:

```shell
curl -XPOST -H "Content-type: application/json" -d '  {
    "card_id": "hanes-gc-003",
    "user_id": "user004",
    "issuer": "Hanes",
    "balance": 200,
    "expiry_date": "2026-12-31"
  }' 'http://localhost:3000/gift_cards'
```

Response:

```json
{
  "card_id": "hanes-gc-003",
  "user_id": "user004",
  "issuer": "Hanes",
  "balance": 200,
  "expiry_date": "2026-12-31",
  "id": 6
}
```

## Links

* [Documentation home](../../index.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [API reference](../index.md)
* [Gift Card resource](index.md)
* [Support](mailto:support@example.com)