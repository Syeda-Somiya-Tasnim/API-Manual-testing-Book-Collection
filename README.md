# Simple Books API

## Description
This API allows users to interact with a simple book reservation system. Users can retrieve information about books, submit orders, view orders, update orders, and delete orders. 

The API is available at [Simple Books API](https://simple-books-api.glitch.me).

## Endpoints

### Status
- **GET /status**: Returns the status of the API.

### List of Books
- **GET /books**: Returns a list of books.
    - *Optional query parameters*:
        - type: fiction or non-fiction
        - limit: a number between 1 and 20.

### Get a Single Book
- **GET /books/:bookId**: Retrieve detailed information about a book.

### Submit an Order
- **POST /orders**: Allows users to submit a new order. Requires authentication.
    - *Request body (JSON)*:
        ```json
        {
          "bookId": 1,
          "customerName": "John"
        }
        ```
    - *Response*: The response body will contain the order Id.

### Get All Orders
- **GET /orders**: Allows users to view all orders. Requires authentication.

### Get an Order
- **GET /orders/:orderId**: Allows users to view an existing order. Requires authentication.

### Update an Order
- **PATCH /orders/:orderId**: Update an existing order. Requires authentication.
    - *Request body (JSON)*:
        ```json
        {
          "customerName": "John"
        }
        ```

### Delete an Order
- **DELETE /orders/:orderId**: Delete an existing order. Requires authentication.

### API Authentication
- **POST /api-clients/**: To submit or view an order, users need to register their API client.
    - *Request body (JSON)*:
        ```json
        {
           "clientName": "hostman",
           "clientEmail": "hostman@example.com"
        }
        ```
    - *Response*: The response body will contain the access token. The access token is valid for 7 days.

## Authentication
To access certain endpoints, users need to authenticate by providing a valid access token in the request header.

### Example:
Authorization: Bearer <YOUR TOKEN>

## Error Handling
- **Status code 409**: "API client already registered." This error occurs when trying to register an API client with already existing credentials. Try changing the values for clientEmail and clientName to something else.

## Installation
To run the tests, you need to have Newman installed. You can install Newman globally using npm:
```bash
npm install -g newman
newman run bookscollection.postman_collection.json -e BookCollectionEnvironment.postman_environment.json

To generate a report after running the tests, use the following command:
       **newman run bookscollection.postman_collection.json -e BookCollectionEnvironment.postman_environment.json -r cli,html**








![Screenshot_1-5-2024_14174_](https://github.com/Syeda-Somiya-Tasnim/API-Manual-testing-Book-Collection/assets/72883710/0956965c-60f0-467d-8835-dfd0b3b6e6d2)
