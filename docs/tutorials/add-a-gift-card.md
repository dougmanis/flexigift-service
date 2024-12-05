---
layout: page
---

# Tutorial: Add a Gift Card

The Flexigift service allows users to pay for their Amazon purchases with third-party gift cards. 
This tutorial will teach you how to add a new gift card to Flexigift and fetch your new card's details.

Allow 30 minutes to complete this lesson.

## Prerequisites

* The Flexigift service is up and running.
* You are comfortable working with [REST interfaces](https://restfulapi.net).
* A REST client such as [cURL](https://curl.se), [Postman](https://www.postman.com), 
or [Insomnia](https://insomnia.rest). This tutorial assumes you are using cURL but use whatever REST client you like.
* There is a user in the system to associate with the new gift card. Follow the [Add a User](add-a-user.md) 
tutorial to create one if there is not one already.

> **Note**: This tutorial assumes that the Flexigift service is running at http://localhost:3000. Remember to 
point to your own host when you adapt the code samples to your own environment.

## Overview

The following procedures will teach you how to [Create a new gift card](#create-a-new-gift-card) and to 
[Fetch your new card's details](#fetch-your-new-cards-details). When you've completed the procedures 
you will have a new gift card ready to spend.

## Create a new gift card

You create new cards in the system with the POST method of the 
[Create a Gift Card](../api/gift-cards/create-a-gift-card.md) API.

1. Submit a Create a Gift Card request with the following details:

    * ```card_id```: Unique identifier provided by the issuer of the card.
    * ```user_id```: The user associated with the payment card.
    * ```issuer```: The merchant that issued the payment card.
    * ```balance```: How much money is left on the card.
    * ```expiry_date```: Date the gift card expires.

    Example request:

    ```shell
    curl -POST -H "Content-type: application/json" -d '  {
        "card_id": "hanes-gc-003",
        "user_id": "user001",
        "issuer": "Hanes",
        "balance": 200,
        "expiry_date": "2026-12-31"
    }' 'http://localhost:3000/gift_cards'
    ```

    The service responds with the gift card details that you submitted plus a unique ID that the system 
    generates automatically.

    Example response:

    ```json
    {
    "card_id": "hanes-gc-003",
    "user_id": "user001",
    "issuer": "Hanes",
    "balance": 200,
    "expiry_date": "2026-12-31",
    "id": 6
    }
    ```

1. Verify that the response data matches the card details that you submitted.

    If the data matches, congratulations! Your new gift card is in the system and ready to be spent. 
    Note the unique ```id```; you will need to know it if you want to fetch your card's details later.

## Fetch your new card's details

You can fetch your gift card's details any time with the GET method of the [Gift Card Resource](../api/gift-cards/index.md) and the 
instance's unique ```id```.

Example [Get a Gift Card](../api/gift-cards/get-a-gift-card.md) request:

```shell
curl "http://localhost:3000/gift_cards/6"
```

Response:

```json
{
  "card_id": "hanes-gc-003",
  "user_id": "user001",
  "issuer": "Hanes",
  "balance": 200,
  "expiry_date": "2026-12-31",
  "id": 6
}
```

## What next?

Now that you have a gift card in the system, link it to a user as described in the [Add a User](add-a-user.md) tutorial.

## Links

* [Documentation Home](../index.md)
* [Quick Start](../quickstart.md)
* [Install Flexigift](../setup.md)
* [Tutorials](../tutorials/index.md)
* [API Reference](../api/index.md)
* [Support](mailto:support@example.com)