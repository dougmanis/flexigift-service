---
layout: page
---

# Delete a Gift Card

The Delete a Gift Card service removes a given card from the system.

## URL

```shell
{base_url}/gift_cards/{id}
```

## HTTP method

DELETE

## Request headers

None

## Request parameters

Path parameters:

| Name          | Type          | Mandatory? | Constraints     | Notes |
| ------------- | ------------- | ---        | ---             | ---   |
| id            | int           | yes        |                 | Internal unique ID assigned by the system. |

## Request data

None

## Response data

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
curl -DELETE "http://localhost:3000/gift_cards/6"
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
* [API reference](../index.md)
* [Gift Card resource](index.md)
* [Support](mailto:support@example.com)