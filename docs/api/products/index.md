---
layout: page
---

# Products resource

Flexigift stores a list of products that are eligible to be purchased with a customer's gift card. 
The Products service contains information about these items.

## Base endpoint

```shell
{base_url}/products
```

## Data structure

| Name            | Type          | Mandatory? | Constraints | Notes |
| -------------   | ------------- | ---        | ---         | ---   |
| product_id      | string        | true       | -           | Unique ID provided by the manufacturer. |
| name            | string        | true       | -           | -     |
| price           | float          | true       | -           | -     |
| eligible_issuer | string        | true       | -           | The issuer whose gift cards can be used to pay for this product. |

Example:

```json
{
  "product_id": "hanes-underwear-001",
  "name": "Hanes Men's Underwear Pack",
  "price": 15.99,
  "eligible_issuer": "Hanes"
}
```

## REST APIs

The Products resource offers the following REST interfaces:

* Create a Product
* Get a Product
* Get Products
* Update a Product
* Delete a Product

## Links

* [Documentation home](../../index.md)
* [API reference](../../api/index.md)
* [Support](mailto:support@example.com)