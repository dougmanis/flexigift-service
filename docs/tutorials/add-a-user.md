---
layout: page
---

# Tutorial: Add a User

The Flexigift service allows users to pay for their Amazon purchases with third-party gift cards. 
This tutorial will teach you how to add a new user to Flexigift and fetch your new user's details.

Allow 30 minutes to complete this lesson.

## Prerequisites

* The Flexigift service is up and running.
* You are comfortable working with [REST interfaces](https://restfulapi.net).
* A REST client such as [cURL](https://curl.se), [Postman](https://www.postman.com), 
or [Insomnia](https://insomnia.rest). This tutorial assumes you are using cURL but use whatever REST 
client you like.

> **Note**: This tutorial assumes that the Flexigift service is running at http://localhost:3000. 
Remember to point to your own host when you adapt the code samples to your own environment.

## Overview

The following procedures will teach you how to [Create a new user](#create-a-new-user) and to 
[Fetch your new user's details](#fetch-your-new-users-details). When you've completed the procedures 
you will have a new user ready to receive gift cards.

## Create a new user

You create new users in the system with the POST method of the Create a User API.

1. Submit a Create a User request with the following details:

    * ```user_id```: The user's Flexigift account ID. This is defined by you.
    * ```amazon_id```: The user's Amazon account ID.
    * ```name```: The user's full name.
    * ```email```: The user's email address.
    * ```gift_cards```: An array of the user's gift card IDs.

    Example request:

    ```shell
    curl -POST -H "Content-type: application/json" -d '  {
        "user_id": "user005",
        "amazon_id": "amz9876",
        "name": "Steve Stevens",
        "email": "steve.stevens@example.com",
        "gift_cards": ["hanes-gc-004","gap-gc-005"]  
    }' 'http://localhost:3000/users'
    ```

    The service responds with the user details that you submitted plus a unique ```id``` that the system 
    generates automatically.

    Example response:

    ```json
    {
    "user_id": "user005",
    "amazon_id": "amz9876",
    "name": "Steve Stevens",
    "email": "steve.stevens@example.com",
    "gift_cards": [
        "hanes-gc-004",
        "gap-gc-005"
    ],
    "id": 5
    }
    ```

1. Verify that the response data matches the user details that you submitted.

    If the data matches, congratulations! Your new user is in the system and ready to be spend their 
    gift cards. Note the unique ```id```; you will need to know it if you want to fetch your user's 
    details later.

## Fetch your new user's details

You can fetch your user's details any time with the GET method of the [Users resource](../api/users/index.md) 
and the instance's unique ```id```.

Example Get a User request:

```shell
curl http://localhost:3000/users/5
```

Response:

```json
{
  "user_id": "user005",
  "amazon_id": "amz9876",
  "name": "Steve Stevens",
  "email": "steve.stevens@example.com",
  "gift_cards": [
    "hanes-gc-004",
    "gap-gc-005"
  ],
  "id": 5
}
```

## What next?

Now that you have a user in the system, try these next steps:

* [Add a Gift Card](add-a-gift-card.md) to spend.
* [Link a Gift Card to a User](link-card-to-user.md).

## Links

* [Documentation Home](../index.md)
* [Quick Start](../quickstart.md)
* [Install Flexigift](../setup.md)
* [Tutorials](../tutorials/index.md)
* [API Reference](../api/index.md)
* [Support](mailto:support@example.com)