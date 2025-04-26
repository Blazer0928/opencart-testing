# Open-Cart REST API Collection - Postman

This repository contains a Postman collection for interacting with the OpenCart REST API. The collection includes various endpoints related to cart, currency, and coupon management.
Table of Contents
-    Pre-requisites
-    Collection Overview
-    How to Set Up
-    API Endpoints
-    Cart
-    Currency
-    Coupon
-    Testing and Validation
-    Environment Variables

## Pre-requisites

Before using this collection, ensure you have the following:

-    Postman installed on your machine. You can download it here.

 -   An OpenCart API endpoint with proper configurations. You must replace {{BaseUrl}} in the collection with your OpenCart API base URL.

 -   An API Token for authentication.

# Collection Overview

The OpenCart API collection contains the following sections:

-    Cart: Endpoints for adding, viewing, editing, and removing products in the shopping cart.

-    Currency: Endpoint for changing the session currency.

-    Coupon: Endpoint for applying coupons to the cart.

# How to Set Up

-    Import the Postman Collection:

-    Download the collection JSON file.

 -   Open Postman and import the collection using the "Import" button.

  -  Set Up Environment Variables:

-    Ensure you have set up the following environment variables in Postman:
-
 -   {{BaseUrl}}: Your OpenCart API base URL (e.g., http://your-opencart-site.com/).
-
 -   {{api_token_val}}: The API token required for authentication.
-
     {{product_id}}: The ID of a product to be used in the cart (can be dynamically set as shown in the collection).
-
 -   {{quantity}}: The quantity of the product (can be dynamically set).
-
 -   {{currency}}: The currency for the session (e.g., USD).
-
 -   {{coupon}}: The coupon code to apply.
-
## API Endpoints
1. Cart

    Adding Product to Cart

        Method: POST

        URL: {{BaseUrl}}api/cart/add

        Body Parameters:

            product_id: The ID of the product to add.

            quantity: The number of products to add.

    View Cart Content

        Method: GET

        URL: {{BaseUrl}}api/cart/products

        Description: Fetches the current content of the cart.

    Edit Product Quantity in Cart

        Method: POST

        URL: {{BaseUrl}}api/cart/edit

        Body Parameters:

            cart_id: The cart ID of the product to modify.

            quantity: The new quantity to set.

    Remove Product from Cart

        Method: POST

        URL: {{BaseUrl}}api/cart/remove

        Body Parameters:

            cart_id: The cart ID of the product to remove.

2. Currency

    Change Session Currency

        Method: POST

        URL: {{BaseUrl}}api/currency

        Body Parameters:

            currency: The currency to switch to (e.g., USD).

3. Coupon

    Apply Existing Coupon

        Method: POST

        URL: {{BaseUrl}}api/coupon

        Body Parameters:

            coupon: The coupon code to apply.

Testing and Validation

Each request in the collection has built-in tests to ensure:

    The API returns a 200 OK status code.

    The response body matches expected values (e.g., successful messages or data).

Example tests include:

    Checking that the cart's content is updated after adding products.

    Validating that the correct currency is set after switching.

    Confirming that the coupon application is successful.

Environment Variables

You need to set the following variables in your Postman environment for proper functioning of the collection:

    BaseUrl: Your OpenCart API base URL (e.g., http://your-opencart-site.com/).

    api_token_val: The API token required for authentication.

    product_id: Product ID to use in cart operations.

    quantity: Quantity for the product to be added to the cart.

    currency: Currency to be set for the session (e.g., USD).

    coupon: The coupon code for the cart.
