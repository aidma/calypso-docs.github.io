---
title: Calypso API Documentation

# language_tabs: # must be one of https://git.io/vQNgJ
#   - shell
#   # - ruby
#   # - python
#   # - javascript

toc_footers:
  - <a href='https://calypso.finance'>Calypso Finance</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to Calypso API! You can use this API to access Calypso API endpoints, which can give you access to invoice information or invoice creation.

The base URL with access to the Calypso Invoice API looks like this: <a href="https://invoice.calypso.finance/">https://invoice.calypso.finance/</a>

<aside class="notice">
If you detect an error in API, need help or have an idea on how to improve it, please contact the <a href="#">Technical Support</a>. 
</aside>


# Authentication

### Create API key

Calypso uses API keys to allow access to the API. You can contact Technical Support to generate a new API key for you.
### Use API key

Calypso expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Api-Key: < your_api_key >`

<aside class="notice">
You must replace <code>< your_api_key ></code> with your personal API key.
</aside>

# Invoices


State | Description
--------- | -------
PENDING_PAYMENT | * Created a new invoice that is awaiting invoice payment. * The client has transferred funds, but they are not received on the wallet. 
PAID | The invoice has been paid in full. 
PENDING_INTERVENTION | * The invoice is awaiting intervention from the merchant in the process. * The client has transferred insufficient funds. * The client has transferred an amount exceeding 


## Get All Invoices

<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
``` -->

> Request:

```shell
curl "https://invoice.calypso.finance/api/v1/invoices" \
  -H "Api-Key: < your_api_key >"
```

<!-- ```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
``` -->

> Response:

```json
[
  {
    "amount": 0,
    "cartItems": [
      {
        "currency": "BTC",
        "price": 0,
        "product": "string",
        "quantity": 0
      }
    ],
    "createdDate": "2021-05-25T11:14:55.165Z",
    "currency": "BTC",
    "description": "string",
    "fee": 0,
    "fiat": {
      "additionalProp1": 0,
      "additionalProp2": 0,
      "additionalProp3": 0
    },
    "id": 0,
    "invoiceAddress": "string",
    "payAmount": 0,
    "state": "PENDING_PAYMENT"
  }
]
```

This endpoint retrieves all invoices.

### HTTP Request

`GET https://invoice.calypso.finance/api/v1/invoices`

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ------- | ------- | -----------
Api-Key | STRING | YES | < your_api_key >


<!-- <aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside> -->

## Get a Specific Invoice

<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
``` -->

> Request:

```shell
curl "https://invoice.calypso.finance/api/v1/invoices/0" \
  -H "Api-Key: < your_api_key >"
```

<!-- ```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
``` -->

> Response:

```json
{
  "amount": 0,
  "cartItems": [
    {
      "currency": "BTC",
      "price": 0,
      "product": "string",
      "quantity": 0
    }
  ],
  "createdDate": "2021-05-25T12:37:28.054Z",
  "currency": "BTC",
  "description": "string",
  "fee": 0,
  "fiat": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "id": 0,
  "invoiceAddress": "string",
  "payAmount": 0,
  "state": "PENDING_PAYMENT"
}
```

This endpoint retrieves a specific invoice.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://invoice.calypso.finance/api/v1/invoices/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the invoice to retrieve

## New Invoice

> Request:

```shell
curl "https://invoice.calypso.finance/api/v1/invoices" \
  -H "Api-Key: < your_api_key >"
```

> Response:

```json
{
  "amount": 0,
  "cartItems": [
    {
      "currency": "BTC",
      "price": 0,
      "product": "string",
      "quantity": 0
    }
  ],
  "createdDate": "2021-05-25T12:37:28.054Z",
  "currency": "BTC",
  "description": "string",
  "fee": 0,
  "fiat": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "id": 0,
  "invoiceAddress": "string",
  "payAmount": 0,
  "state": "PENDING_PAYMENT"
}
```

This endpoint creates a new invoice.

### HTTP Request

`POST https://invoice.calypso.finance/api/v1/invoices`

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ------- | ------- | -----------
Api-Key | STRING | YES | < your_api_key >


### Query Body

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
amount | NUMBER | YES | The total amount of the invoice.
currency | ENUM | YES | Received currency name. [BTC, ETH, USDT, FAU, USD, EUR, RUB]
description | STRING | YES | A short description of the invoice.
cartItems | OBJECT | YES | Shopping cart.

## New Invoice (Button)

> Request:

```shell
curl "https://invoice.calypso.finance/api/v1/invoices/by/template/0" \
  -H "Api-Key: < your_api_key >"
```

> Response:

```json
{
  "amount": 0,
  "cartItems": [
    {
      "currency": "BTC",
      "price": 0,
      "product": "string",
      "quantity": 0
    }
  ],
  "createdDate": "2021-05-25T12:37:28.054Z",
  "currency": "BTC",
  "description": "string",
  "fee": 0,
  "fiat": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "id": 0,
  "invoiceAddress": "string",
  "payAmount": 0,
  "state": "PENDING_PAYMENT"
}
```

This endpoint creates a new invoice.

### HTTP Request

`POST https://invoice.calypso.finance/api/v1/invoices/by/template/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | ID of the button that creates the invoice.


### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ------- | ------- | -----------
Api-Key | STRING | YES | < your_api_key >


## Cancel a Specific Invoice
<!-- 
```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
``` -->

> Request:

```shell
curl "https://invoice.calypso.finance/api/v1/invoices/0/chargeback" \
  -H "Api-Key: < your_api_key >"
```

<!-- ```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
``` -->

<!-- > The above command returns JSON structured like this: -->

> Response:

```json
{
  "amount": 0,
  "cartItems": [
    {
      "currency": "BTC",
      "price": 0,
      "product": "string",
      "quantity": 0
    }
  ],
  "createdDate": "2021-05-25T12:37:28.054Z",
  "currency": "BTC",
  "description": "string",
  "fee": 0,
  "fiat": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "id": 0,
  "invoiceAddress": "string",
  "payAmount": 0,
  "state": "CANCEL"
}
```

This endpoint cancels a specific invoice.

### HTTP Request

`POST https://invoice.calypso.finance/api/v1/invoices/<ID>/chargeback`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the invoice to retrieve
