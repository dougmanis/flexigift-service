---
layout: page
---

# Get a Gift Card

The Get a Gift Card service returns the details for a given card.

## URL

```shell
{base_url}/gift_cards/{id}
```

## HTTP method

GET

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
curl http://localhost:3000/gift_cards/1
```

Response:

```json
{
  "id": 1,
  "card_id": "hanes-gc-001",
  "user_id": "user001",
  "issuer": "Hanes",
  "balance": 50,
  "expiry_date": "2025-12-31"
}
```

**Note**: The service always responds with HTTP status 200 even for cards that do not exist in the system. Instead of returning status 404 (Not Found), the service returns an empty data set.

For example, searching for non-existing Gift Card 999:

```bash
curl -GET "http://localhost:3000/gift_cards/999"
```

returns:

```json
{}
```

## Links

* [Documentation Home](../../index.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [REST API Reference](../index.md)
* [Gift Card Resource](index.md)
* [Support](mailto:support@example.com)