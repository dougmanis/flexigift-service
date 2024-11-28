---
layout: page
---

# Get a Transaction

The Get a Transaction service returns the details for a given [transaction](index.md).

## URL

```shell
{base_url}/transactions/{id}
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

## Example request and response

Request:

```shell
curl http://localhost:3000/transactions/1
```

Response:

```json
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
}
```

> **Note**: The service always responds with HTTP status 200 even for transactions that do not exist in the system. Instead of returning status 404 (Not Found), the service returns an empty data set.
>
> For example, searching for non-existing transaction 999:
>
> ```bash
> curl -GET "http://localhost:3000/transactions/999"
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
* [Transactions resource](index.md)
* [Support](mailto:support@example.com)