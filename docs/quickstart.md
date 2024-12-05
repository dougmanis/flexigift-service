---
layout: page
---

# Quick Start

Welcome to Flexigift, the service that lets you spend your gift cards at Amazon.com. This quick start 
will walk you through:

1. Adding a new [user](api/users/index.md) named Jack Johnson.
1. Registering Jack's Kohl's [gift card](api/gift-cards/index.md) with Flexigift.
1. Linking Jack's card to his Flexigift account.
1. Registering a Kohl's [product](api/products/index.md) for Jack to purchase with his card.

## 1) [Install Flexigift](setup.md)

Do this first!

## 2) Add a user

Customers who want to spend their third-party gift cards at Amazon.com must first register with Flexigift. 
Flexigift supports multiple users, but in this walkthrough we will add only one.

To register a user with Flexigift:

1. In a console, submit a Create User request with the following data:
    * ```user_id```: A unique user ID of your choosing.
    * ```amazon_id```: The user's Amazon account ID.
    * ```name```: Full name. **Jack Johnson** in this example.
    * ```email```: A valid email address.

    Ex:

    ```shell
    curl -POST -H "Content-type: application/json" -d '  {
        "user_id": "user006",
        "amazon_id": "amz3456",
        "name": "Jack Johnson",
        "email": "jack.johnson@example.com",
    }' 'http://localhost:3000/users'
    ```

1. Note the unique `id` in the system's response (**7** in our example). You will need it to link a 
gift card to this user later.

    Ex:

    ```json
    {
        "user_id": "user006",
        "amazon_id": "amz3456",
        "name": "Jack Johnson",
        "email": "jack.johnson@example.com",
        "id": 7
    }
    ```

## 3) Add a gift card

Jack has a gift card from Kohl's that he would like to spend at Amazon.com. Let's register his card 
with Flexigift:

1. Submit a Create a Gift Card request with the following data:
    * `card_id`: Unique identifier provided by the issuer of the card.
    * `user_id`: The user associated with the payment card. Jack's ID is **user006**.
    * `issuer`: The merchant that issued the payment card. **Kohls** in this case.
    * `balance`: How much money is left on the card.
    * `expiry_date`: Date the gift card expires.

    Ex:

    ```shell
    curl -XPOST -H "Content-type: application/json" -d '  {
        "card_id": "kohls-gc-001",
        "user_id": "user006",
        "issuer": "Kohls",
        "balance": 250,
        "expiry_date": "2025-12-31"
    }' 'http://localhost:3000/gift_cards'
    ```

2. Note the unique `id` in the system's response (**6** in our example):

    ```json
    {
        "card_id": "kohls-gc-001",
        "user_id": "user006",
        "issuer": "Kohls",
        "balance": 250,
        "expiry_date": "2025-12-31",
        "id": 6
    }
    ```

## 4) Link a gift card to a user

Now that Jack and his Kohl's gift card are registerd with Flexigift, link the card to Jack's Flexigift 
account. Do this by adding the ```card_id``` of Jack's Kohl's gift card to his account:

> IMPORTANT!: The Update User request overwrites _all_ of the exiting user's data. You _must_ re-submit  
> _all_ of your user's existing data or it will be cleared.

1. Submit an Update User request with the following data:
    * ```user_id```: **user006**
    * ```amazon_id```: **amz3456**
    * ```name```: **Jack Johnson**
    * ```email```: **jack.johnson@example.com**
    * ```gift_cards```: **kohls-gc-001**

    Ex:

    ```shell
    curl -XPUT -H "Content-type: application/json" -d '  {
        "user_id": "user006",
        "amazon_id": "amz3456",
        "name": "Jack Johnson",
        "email": "jack.johnson@example.com",
        "gift_cards": ["kohls-gc-001"]  
    }' 'http://localhost:3000/users/6'
    ```

2. Note that the system response shows that Jack's user account is now linked to his Kohl's card via 
the ```gift_cards``` property:

    ```json
    {
        "user_id": "user006",
        "amazon_id": "amz3456",
        "name": "Jack Johnson",
        "email": "jack.johnson@example.com",
        "gift_cards": [
            "kohls-gc-001"
        ],
        "id": 6
    }
    ```

## 5) Register a product with Flexigift

The gift card issuers (Kohl's in our example) decide which of their products are eligible to be purchased 
through Flexigift. Jack now has a Kohl's card linked to his account and ready to spend, but there are 
no eligible products for him to buy. Let's change that!

To register an eligible product:

1. Submit a Create a Product request with the following data:
    * ```product_id```: Part number provided by the issuer.
    * ```name```: Product name provided by the issuer.
    * ```price```: Price provided by the issuer.
    * ```eligible_issuer```: The company that issued the card.

    Ex:

    ```shell
    curl -XPOST -H "Content-type: application/json" -d '  {
        "product_id": "kohls-dogbed-001",
        "name": "Deluxe Round Dog Bed",
        "price": "50.00",
        "eligible_issuer": "Kohls"
    }' 'http://localhost:3000/products
    ```
1. Note in the system response that the system has assigned a unique internal `id` property:

    ```json
    {
        "product_id": "kohls-dogbed-001",
        "name": "Deluxe Round Dog Bed",
        "price": "50.00",
        "eligible_issuer": "Kohls",
        "id": 5
    }
    ```

## Next steps

Now that Jack Johnson's Kohl's gift card is linked to his Flexigift account, and an eligible Kohl's 
catalog item is registered with Flexigift, when Jack adds the Kohl's Deluxe Round Dog Bed to his 
Amazon.com shopping cart, Amazon will offer him the option to pay with his Kohl's gift card.

## Links

* [Documentation Home](index.md)
* [Quick Start](quickstart.md)
* [Install Flexigift](setup.md)
* [Tutorials](tutorials/index.md)
* [API Reference](api/index.md)
* [Support](mailto:support@example.com)