---
layout: page
---

# Delete a User

The Delete a User service removes a given [user](index.md) from the system.

## URL

```shell
{base_url}/users/{id}
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

An empty data set.

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example request and response

Request:

```shell
curl -XDELETE http://localhost:3000/users/6
```

Response:

```json
{}
```

## Links

* [Documentation Home](../../index.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [REST API Reference](../../api/index.md)
* [User Resource](index.md)
* [Support](mailto:support@example.com)