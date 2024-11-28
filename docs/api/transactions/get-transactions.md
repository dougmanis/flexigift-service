---
layout: page
---

# Get Transactions

The Get Transactions service returns an array of the [transactions](index.md) in the system along with their details.

## URL

```shell
{base_url}/transactions
```

## HTTP method

GET

## Request headers

None

## Request parameters

None

## Request data

None

## Response data

| Name           | Type          | Mandatory? | Constraints | Notes |
| -------------  | ------------- | ---        | ---         | ---   |
| id             | int           | yes        | -           | Unique internal ID generated by the system. |
| transaction_id | string        | yes        | -           | Unique ID. |
| user_id        | string        | yes        | -           | The user who made the purchase.    |
| amazon_id      | string        | yes        | -           | The user's Amazon account ID.      |
| product_id     | string        | yes        | -           | Product catalog number provided by the manufacturer. |
| card_id        | string        | yes        | -           | Unique ID of the payment card used for the purchase. |
| amount         | float          | yes        | -           | - |
| status         | string        | yes        | Must be one of: {COMPLETED, REJECTED} | - |
| balance_check  | boolean       | yes        | Must be one of: {TRUE, FALSE} | Did the card have enough money to pay for the purchase? |
| message        | string        | no         | -           | - |

## HTTP response codes

| Code          | Description   | Notes |
| ------------- | ------------- | ---   |
| 200           | OK            | -     |

## Example requests and responses

### Get all Transactions

Request:

```shell
curl http://localhost:3000/transactions
```

Response:

```json
[
  {
    "id": 1,
    "transaction_id": "txn001",
    "user_id": "user001",
    "amazon_id": "amz12345",
    "product_id": "hanes-underwear-001",
    "card_id": "hanes-gc-001",
    "amount": 15.99,
    "status": "Completed",
    "balance_check": true,
    "message": "Balance confirmed before transaction."
  },
  {
    "id": 2,
    "transaction_id": "txn002",
    "user_id": "user002",
    "amazon_id": "amz67890",
    "product_id": "starbucks-coffee-003",
    "card_id": "starbucks-gc-003",
    "amount": 12.99,
    "status": "Completed",
    "balance_check": true,
    "message": "Balance confirmed before transaction."
  },
  {
    "id": 3,
    "transaction_id": "txn003",
    "user_id": "user003",
    "amazon_id": "amz54321",
    "product_id": "gap-jacket-004",
    "card_id": "gap-gc-004",
    "amount": 65,
    "status": "Completed",
    "balance_check": true,
    "message": "Balance confirmed before transaction."
  },
  {
    "id": 4,
    "transaction_id": "txn004",
    "user_id": "user004",
    "amazon_id": "amz98765",
    "product_id": "hanes-underwear-001",
    "card_id": "hanes-gc-001",
    "amount": 15.99,
    "status": "Completed",
    "balance_check": true,
    "message": "Balance confirmed before transaction."
  }
]
```

## Links

* [Documentation home](../../index.md)
* [Install Flexigift](../../setup.md)
* [Tutorials](../../tutorials/index.md)
* [API reference](../../api/index.md)
* [Transactions resource](index.md)
* [Support](mailto:support@example.com)