---
layout: page
---

# Get a Product

The Get a Product service returns the details for a given [product](index.md).

## URL

```shell
{base_url}/products/{id}
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

Request:

```shell
curl http://localhost:3000/products/1
```

Response:

```json
{
  "id": 1,
  "product_id": "hanes-underwear-001",
  "name": "Hanes Men's Underwear Pack",
  "price": 15.99,
  "eligible_issuer": "Hanes"
}
```

> **Note**: The service always responds with HTTP status 200 even for products that do not exist in the system. Instead of returning status 404 (Not Found), the service returns an empty data set.
>
> For example, searching for non-existing product 999:
>
> ```bash
> curl -GET "http://localhost:3000/products/999"
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
* [Products resource](index.md)
* [Support](mailto:support@example.com)