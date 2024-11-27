---
layout: page
---

# Update a User

The Update a User service changes the details for a given [user](index.md).

## URL

```shell
{base_url}/users/{id}
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

| Name           | Type          | Mandatory? | Constraints     | Notes |
| -------------  | ------------- | ---        | ---             | ---   |
| user_id        | string        | yes        | Must be unique. | Unique ID. |
| amazon_id      | string        | yes        | -               | The user's Amazon account ID. |
| name           | string        | yes        | -               | The user's full name.         |
| email          | string        | yes        | Must contain an '@' symbol. | The user's email address. |
| gift_cards     | string[]      | no         | -               | Array of [gift cards](../gift-cards/index.md) associated with the user. |

## Response data

A successful request returns the data you submitted plus the user's unique `id`:

| Name           | Type          | Mandatory? | Constraints | Notes |
| -------------  | ------------- | ---        | ---         | ---   |
| id             | int           | yes        | -           | Unique internal ID generated by the system. |
| user_id        | string        | yes        | -           | -     |
| amazon_id      | string        | yes        | -           | -     |
| name           | string        | yes        | -           | -     |
| email          | string        | yes        | -           | -     |
| gift_cards     | string[]      | yes        | -           | -     |

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example request and response

The following example updates the `name` and `email` for user `id` 6:

Request:

```shell
curl -XPUT -H "Content-type: application/json" -d '  {
    "user_id": "user005",
    "amazon_id": "amz09876",
    "name": "Stefan Stevens",
    "email": "stefan.stevens@example.com", 
    "gift_cards": [
        "gap-gc-005", 
        "hanes-gc-002"
    ]
  }' 'http://localhost:3000/users/6'
```

Response:

```json
{
  "user_id": "user005",
  "amazon_id": "amz09876",
  "name": "Stefan Stevens",
  "email": "stefan.stevens@example.com",
  "gift_cards": [
    "gap-gc-005",
    "hanes-gc-002"
  ],
  "id": 6
}
```

## Links

* [Documentation home](../../index.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [API reference](../../api/index.md)
* [User resource](index.md)
* [Support](mailto:support@example.com)