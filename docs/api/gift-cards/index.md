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

| Name          | Type          | Mandatory? | Constraints | Notes |
| ------------- | ------------- | ---        | ---         | ---   |
| card_id       | string        | true       | -           | Unique ID. This value is provided by the issuer of the card. |
| user_id       | string        | true       | -           | The user associated with the payment card. |
| issuer        | string        | true       | -           | The merchant that issued the payment card. |
| balance       | float          | true       | -           | How much money is left on the card.        |
| expiry_date   | date          | true       | -           | Date the gift card expires. |

Example:

```json
{
  "card_id": "hanes-gc-001",
  "user_id": "user001",
  "issuer": "Hanes",
  "balance": 50,
  "expiry_date": "2025-12-31"
}
```

## REST APIs

The Gift Card resource offers the following REST interfaces:

* Create a Gift Card
* Get a Gift Card
* [Get Gift Cards](get-gift-cards.md)
* Update a Gift Card
* Delete a Gift Card

## Links

* [Documentation home](../../index.md)
* [API reference](../../api/index.md)
* [Support](mailto:support@example.com)