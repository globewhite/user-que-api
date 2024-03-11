Simple Books API
This API allows you to reserve a book.

The API is available at https://que-api.aco.me

Endpoints
Status
GET /status

Returns the status of the API.

List of apis
GET /apis



Optional query parameters:

type: fiction or non-fiction
limit: a number between 1 and 5.
Get a single book
GET /api/:bookId

Retrieve detailed information about a book.

Submit an order
POST /orders

Allows you to submit a new order. Requires authentication.

The request body needs to be in JSON format and include the following properties:

bookId - Integer - Required
customerName - String - Required
Example

POST /orders/
Authorization: Bearer <YOUR TOKEN>

{
  "id": 1,
   "que": "what are the services are you looking for",
   "ans":"optical fibre cable"
}
The response body will contain the order Id.

Get all orders
GET /orders

Allows you to view all orders. Requires authentication.

Get an order
GET /orders/:orderId

Allows you to view an existing order. Requires authentication.

Update an order
PATCH /orders/:orderId

Update an existing order. Requires authentication.

The request body needs to be in JSON format and allows you to update the following properties:

customerName - String
Example

PATCH /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>

{
  "customerName": "John"
}
Delete an order
DELETE /orders/:orderId

Delete an existing order. Requires authentication.

The request body needs to be empty.

Example

DELETE /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>
API Authentication
To submit or view an order, you need to register your API client.

POST /api-clients/

The request body needs to be in JSON format and include the following properties:

clientName - String
clientEmail - String
Example

{
   "clientName": "Postman",
   "clientEmail": "abc@gmail.com"
}
The response body will contain the access token. The access token is valid for 7 days.

Possible errors

Status code 409 - "API client already registered." Try changing the values for clientEmail and clientName to something else.
