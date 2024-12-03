---
layout: page
---

# Tutorial: Link a Gift Card to a User

The Flexigift service allows users to pay for their Amazon purchases with third-party gift cards. 
This tutorial will teach you how to add link a gift card to a user.

Allow 30 minutes to complete this lesson.

## Prerequisites

* The Flexigift service is up and running.
* You are comfortable working with [REST interfaces](https://restfulapi.net).
* A REST client such as [cURL](https://curl.se), [Postman](https://www.postman.com), 
or [Insomnia](https://insomnia.rest). This tutorial assumes you are using cURL but use whatever REST client you like.
* At least one user and gift card already exist in the system. If they do not, first follow the 
[Add a User](add-a-user.md) and [Create a Gift Card](add-a-gift-card.md) tutorials.

> **Note**: This tutorial assumes that the Flexigift service is running at http://localhost:3000. 
Remember to point to your own host when you adapt the code samples to your own environment.

## Overview

The following procedures will teach you how to link a gift card to a user. When you've completed the 
tutorial, the user will be able to use their card for their Amazon.com purchases.

## Find your user and gift card IDs

Users and gift cards are associated with each other by their ```user_id``` and ```card_id``` respectively. 
The linking of users and gift cards is one to many; that is, a user may have many gift cards, but 
a gift card may be linked to only one user.

To find your user ID:

1. Fetch all of the users in the system:

    ``` shell
    curl http://localhost:3000/users/
    ```

1. Find your user and note their ```id``` and ```user_id``` values.
1. Also note _all_ of your user's details. You will need to submit them again when you update your user.

To find your card IDs: 

1. Fetch all of the gift cards in the system: 

    ```shell
    curl http://localhost:3000/gift_cards
    ```

1. Note the ```id``` and ```card_id``` for the card you want to link to your user.
1. Also note _all_ of your card's details. You will need to submit them again when you update your card.

## Link your user to their card

Link your user to their gift card with the PUT method of the User resource:

Submit an Update a User request with the the ```gift_card``` ID(s) of the card(s) you want to link to.

    > **Important!**: Remember to also include _all_ of your user's existing details in this request. 
    If you do not include those details, the system will clear them out.

The following example request links gift card ```gap-gc-005``` to user ```5```:

```shell
curl -XPUT -H "Content-type: application/json" -d '  {
    "user_id": "user005",
    "amazon_id": "amz9876",
    "name": "Steve Stevens",
    "email": "steve.stevens@example.com",
    "gift_cards": ["gap-gc-005"]  
  }' 'http://localhost:3000/users/5'
```

Example response:

```json
{
  "user_id": "user005",
  "amazon_id": "amz9876",
  "name": "Steve Stevens",
  "email": "steve.stevens@example.com",
  "gift_cards": [
    "gap-gc-005"
  ],
  "id": 5
}
```

## Link the gift card to your user

Link the gift card to your user with the PUT method of the Gift Card resource:

Submit an Update Gift Card request with your user's ```user_id```.

The following example request links user ```user005``` to gift card ```8```:

```shell
curl -XPUT -H "Content-type: application/json" -d '  {
    "card_id": "gap-gc-005",
    "user_id": "user005",
    "issuer": "Hanes",
    "balance": 200,
    "expiry_date": "2026-12-31"
  }' 'http://localhost:3000/gift_cards/8'
```

Example response:

```json
{
  "card_id": "gap-gc-005",
  "user_id": "user005",
  "issuer": "Hanes",
  "balance": 200,
  "expiry_date": "2026-12-31",
  "id": 8
}
```

## What next?

Now that your user has gift cards associated, they can start redeeming them in their Amazon.com shopping cart.

## Links

* [Documentation Home](../index.md)
* [Install Flexigift](../setup.md)
* [Tutorials](../tutorials/index.md)
* [REST API Reference](../api/index.md)
* [Support](mailto:support@example.com)