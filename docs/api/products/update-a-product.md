---
layout: page
---

# Update a Product

The Update a Product service changes the details for a given [product](index.md).

## URL

```shell
{base_url}/products/{id}
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

| Name            | Type          | Mandatory? | Constraints | Notes |
| -------------   | ------------- | ---        | ---         | ---   |
| product_id      | string        | yes        | -           | Unique ID provided by the manufacturer. |
| name            | string        | yes        | -           | -     |
| price           | float          | yes        | -           | -     |
| eligible_issuer | string        | yes        | -           | The issuer whose gift cards can be used to pay for this product. |

## Response data

A successful request returns the data you submitted plus the product's unique `id`:

| Name            | Type          | Mandatory? | Constraints | Notes |
| -------------   | ------------- | ---        | ---         | ---   |
| id              | int           | yes        | -           | Unique internal ID generated by the system. |
| product_id      | string        | yes        | -           | Unique ID provided by the manufacturer. |
| name            | string        | yes        | -           | -     |
| price           | float          | yes        | -           | -     |
| eligible_issuer | string        | yes        | -           | The issuer whose gift cards can be used to pay for this product. |

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example request and response

The following example updates the `name` and `price` for product `id` 5:

Request:

```shell
curl -XPUT -H "Content-type: application/json" -d '  {
    "product_id": "gap-coat-001",
    "name": "Gap Winter Parka",
    "price": 60.00,
    "eligible_issuer": "Gap"
  }' 'http://localhost:3000/products/5'
```

Response:

```json
{
  "product_id": "gap-coat-001",
  "name": "Gap Winter Parka",
  "price": 60,
  "eligible_issuer": "Gap",
  "id": 5
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