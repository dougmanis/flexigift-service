---
layout: page
---

# Get a User

The Get a User service returns the details for a given [user](index.md).

## URL

```shell
{base_url}/users/{id}
```

## HTTP method

GET

## Request headers

None

## Request parameters

Path parameters:

| Name          | Type          | Mandatory? | Constraints | Notes |
| ------------- | ------------- | ---        | ---         | ---   |
| id            | int           | yes        |             | Internal unique ID assigned by the system. |

## Request data

None

## Response data

| Name           | Type          | Mandatory? | Constraints     | Notes |
| -------------  | ------------- | ---        | ---             | ---   |
| id             | int           | yes        | Must be unique. | Internal unique ID generated by the system. |
| user_id        | string        | yes        | Must be unique. | Unique ID.                      |
| amazon_id      | string        | yes        | -               | The user's Amazon account ID.   |
| name           | string        | yes        | -               | The user's full name.           |
| email          | string        | yes        | Must contain an '@' symbol. | The user's email address. |
| gift_cards     | string[]      | yes        | -               | Array of [gift cards](../gift-cards/index.md) associated with the user. |

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example request and response

Request:

```shell
http://localhost:3000/users/1
```

Response:

```json
{
  "id": 1,
  "user_id": "user001",
  "amazon_id": "amz12345",
  "name": "John Doe",
  "email": "john.doe@example.com",
  "gift_cards": [
    "hanes-gc-001",
    "nike-gc-002"
  ]
}
```

> **Note**: The service always responds with HTTP status 200 even for users that do not exist in the system. Instead of returning status 404 (Not Found), the service returns an empty data set.
>
> For example, searching for non-existing user 999:
>
> ```bash
> curl -GET "http://localhost:3000/gift_cards/999"
> ```
>
> returns:
>
> ```json
> {}
> ```

## Links

* [Documentation home](../../index.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [API reference](../../api/index.md)
* [User resource](index.md)
* [Support](mailto:support@example.com)