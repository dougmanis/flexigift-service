---
layout: page
---

# Gift Card resource

The Gift Card resource contains information about customers' third-party payment cards.

## Base endpoint

```shell
{base_url}/gift-cards
```

## Data structure

| Name          | Type          | Mandatory? | Constraints     | Notes |
| ------------- | ------------- | ---        | ---             | ---   |
| id            | int           | yes        | Must be unique. | Internal unique ID assigned by the system. |
| card_id       | string        | no         | -               | Unique ID provided by the issuer of the card. |
| user_id       | string        | no         | -               | The user associated with the payment card. |
| issuer        | string        | no         | -               | The merchant that issued the payment card. |
| balance       | float          | no         | -               | How much money is left on the card.        |
| expiry_date   | date          | no         | -               | Date the gift card expires. |

Example:

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

## REST APIs

The Gift Card resource offers the following REST interfaces:

* [Create a Gift Card](create-a-gift-card.md)
* [Get a Gift Card](get-a-gift-card.md)
* [Get Gift Cards](get-gift-cards.md)
* [Update a Gift Card](update-a-gift-card.md)
* [Delete a Gift Card](delete-a-gift-card.md)

## Links

* [Documentation home](../../index.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [API reference](../../api/index.md)
* [Support](mailto:support@example.com)