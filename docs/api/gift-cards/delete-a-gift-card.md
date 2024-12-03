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

An empty data set.

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example request and response

Request:

```shell
curl -XDELETE "http://localhost:3000/gift_cards/6"
```

Response:

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