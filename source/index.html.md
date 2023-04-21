---
title: go deploy - Order API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - json

toc_footers:
  - <a href='https://godeploy.com/'>Powered by go deploy</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for go deploy Order API
---

# Introduction

This API allows external clients create orders in our system.

# Authentication

The Orders API uses Bearer tokens to authenticate requests. Contact our support to receive a JWT token.

Your JWT token has many privileges, so keep it safe.

Use your JWT token by adding it to the Authorization header as seen in the following example:
``Authorization: Bearer JWTToken``

All API requests must have authentication header present.

<aside class="notice">
You must replace <code>JWTToken</code> with your JWT token.
</aside>

# Products

## Get All Products

> Example Response:

```json
{
  "items": [
    {
      "id": "451d2195-25ec-e811-8373-00155d016234",
      "code": "AZ-300",
      "name": "AZ-300 (Packaged Set) - (Azure Pass)",
      "courseIds": [],
      "_links": {
        "self": "/api/v2/products/451d2195-25ec-e811-8373-00155d016234"
      }
    }
  ],
  "_pageInfo": {
    "pageCount": 29,
    "totalItemCount": 287,
    "pageNumber": 1,
    "pageSize": 10,
    "hasPreviousPage": false,
    "hasNextPage": true,
    "isFirstPage": true,
    "isLastPage": false,
    "firstItemOnPage": 1,
    "lastItemOnPage": 10
  },
  "_links": {
    "next": "/api/v2/products?_page=2"
  }
}
```

This endpoint returns a paginated set of Products.

### HTTP Request

`GET api/v2/products?businessUnitId=yourBusinessUnitId`

### Query Parameters

 Parameter | Default | Description                           
-----------|---------|---------------------------------------
businessUnitId | null    | The id of the business unit to query against
 _pageSize | 10      | The number of results to get per page 
 _page     | 1       | The page to get the results for       

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

## Get a Specific Product

> Example Response:

```json
{
  "id": "451d2195-25ec-e811-8373-00155d026631",
  "code": "AZ-300",
  "name": "AZ-300 (Packaged Set) - (Azure Pass)",
  "courseIds": [],
  "_links": {
    "self": "/api/v2/products/451d2195-25ec-e811-8373-00155d026631"
  }
}
```

This endpoint retrieves a specific Product.

### HTTP Request

`GET api/v2/products/{productId}?businessUnitId=yourBusinessUnitId`

### URL Parameters

Parameter | Description
--------- | -----------
productId | The ID of the Product to retrieve

### Query Parameters

Parameter | Default | Description
-----------|---------|---------------------------------------
businessUnitId | null    | The id of the business unit to query against

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

# Feature Sets

## Get All Feature Sets for a Product

> Example Response:

```json
{
  "items": [
    {
      "id": "e903e8cf-6438-e911-8373-00155d026631",
      "productId": "451d2195-25ec-e811-8373-00155d026631",
      "name": "Standard - 180 days",
      "courseAccessPeriodDays": 180,
      "moduleSavePeriodDays": 1,
      "prices": [
        {
          "currency": "GBP",
          "value": 48.0000
        }
      ],
      "_links": {
        "self": "/api/v2/products/451d2195-25ec-e811-8373-00155d026631/feature_sets/e903e8cf-6438-e911-8373-00155d026631"
      }
    }
  ],
  "_pageInfo": {
    "pageCount": 1,
    "totalItemCount": 1,
    "pageNumber": 1,
    "pageSize": 10,
    "hasPreviousPage": false,
    "hasNextPage": false,
    "isFirstPage": true,
    "isLastPage": true,
    "firstItemOnPage": 1,
    "lastItemOnPage": 1
  },
  "_links": {}
}
```

This endpoint returns a paginated set of Feature Sets for a Product.

### HTTP Request

`GET api/v2/products/{productId}/feature_sets?businessUnitId=yourBusinessUnitId`

### Query Parameters

Parameter | Default | Description
-----------|---------|---------------------------------------
businessUnitId | null    | The id of the business unit to query against
_pageSize | 10      | The number of results to get per page
_page     | 1       | The page to get the results for

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

## Get a Specific Feature Set for a Product

> Example Response:

```json
{
  "id": "e903e8cf-6438-e911-8373-00155d026631",
  "productId": "451d2195-25ec-e811-8373-00155d026631",
  "name": "Standard - 180 days",
  "courseAccessPeriodDays": 180,
  "moduleSavePeriodDays": 1,
  "prices": [
    {
      "currency": "GBP",
      "value": 48.0000
    }
  ],
  "_links": {
    "self": "/api/v2/products/451d2195-25ec-e811-8373-00155d026631/feature_sets/e903e8cf-6438-e911-8373-00155d026631"
  }
}
```

This endpoint retrieves a specific Feature Set for a Product.

### HTTP Request

`GET api/v2/products/{productId}/feature_sets/{featureSetId}?businessUnitId=yourBusinessUnitId`

### URL Parameters

Parameter | Description
--------- | -----------
productId | The ID of the Product to get the Feature Sets for
featureSetId | The ID of the Feature Set to retrieve

### Query Parameters

Parameter | Default | Description
-----------|---------|---------------------------------------
businessUnitId | null    | The id of the business unit to query against

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

# Orders

## Get All Orders

> Example Response:

```json
{
  "items": [
    {
      "id": 1,
      "businessUnitId": "4f48f74f-1738-e911-8373-00155d026631",
      "businessUnit": {
        "name": "UK"
      },
      "createdByUserId": "DF66878B-8787-4D40-9A17-7E705B734833",
      "createdByUser": {
        "forename": "John",
        "surname": "Smith",
        "name": "John Smith",
        "userName": "johnsmith@example.com"
      },
      "orderSourceId": "67a6b9b1-8a96-4b64-8165-0207e132dd0a",
      "orderSource": {
        "name": "go deploy",
        "invoiceable": true
      },
      "purchasingOrderReference": "423432432",
      "contactForename": "John",
      "contactSurname": "Smith",
      "contactEmail": "johnsmith@example.com",
      "orderStatus": "Cancelled",
      "created": "2019-02-24T20:04:30.473",
      "editable": false,
      "cancellable": false,
      "_links": {
        "self": "/api/v2/orders/1"
      }
    }
  ],
  "_pageInfo": {
    "pageCount": 415,
    "totalItemCount": 4150,
    "pageNumber": 1,
    "pageSize": 10,
    "hasPreviousPage": false,
    "hasNextPage": true,
    "isFirstPage": true,
    "isLastPage": false,
    "firstItemOnPage": 1,
    "lastItemOnPage": 10
  },
  "_links": {
    "next": "/api/v2/orders?_page=2"
  }
}
```

This endpoint returns a paginated set of Orders.

### HTTP Request

`GET api/v2/orders?businessUnitId=yourBusinessUnitId`

### Query Parameters

Parameter | Default | Description
-----------|---------|---------------------------------------
businessUnitId | null    | The id of the business unit to query against
_pageSize | 10      | The number of results to get per page
_page     | 1       | The page to get the results for

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

## Get a Specific Order

> Example Response:

```json
{
  "id": 1,
  "businessUnitId": "4f48f74f-1738-e911-8373-00155d026631",
  "createdByUserId": "DF66878B-8787-4D40-9A17-7E705B734833",
  "orderSourceId": "67a6b9b1-8a96-4b64-8165-0207e132dd0a",
  "purchasingOrderReference": "423432432",
  "contactForename": "John",
  "contactSurname": "Smith",
  "contactEmail": "johnsmith@example.com",
  "orderStatus": "Cancelled",
  "created": "2019-02-24T20:04:30.473",
  "editable": false,
  "cancellable": false
}
```

This endpoint retrieves a specific Order.

### HTTP Request

`GET api/v2/orders/{orderId}?businessUnitId=yourBusinessUnitId`

### URL Parameters

Parameter | Description
--------- | -----------
orderId | The ID of the Order to retrieve

### Query Parameters

Parameter | Default | Description
-----------|---------|---------------------------------------
businessUnitId | null    | The id of the business unit to query against

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

## Create an Order

> Example Request:

```json
{
  "purchaseOrderReference": "your Order Reference",
  "contactEmail": "contact email address",
  "emailKeys": true,
  "orderItems": [
    {
      "featureSetId": "feature set id",
      "quantity": 1,
      "sourceReference": "Your source reference",
      "feedbackLinkUri": "Your feedback link uri",
      "feedbackLinkText": "Submit feedback",
      "enableFeedbackLink": true,
      "achievementCode": ""
    }
  ]
}
```

> Example Response:

```json
{
  "id": 35044,
  "businessUnitId": "4f48f74f-1738-e911-8373-00155d026631",
  "businessUnit": {
    "name": "UK"
  },
  "createdByUserId": "133g13e5-5cf3-4692-afa7-3b7548f00d44",
  "createdByUser": {
    "forename": "John",
    "surname": "Smith",
    "name": "John Smith",
    "userName": "johnsmith@example.com"
  },
  "orderSourceId": "67a6b9b1-8a96-4b64-8165-0207e132dd0a",
  "purchasingOrderReference": "123456",
  "contactForename": "John",
  "contactSurname": "Smith",
  "contactEmail": "johnsmith@example.com",
  "orderStatus": "New",
  "created": "2023-04-21T12:49:24.7613405Z",
  "editable": false,
  "cancellable": false,
  "_links": {
    "self": "/api/v2/orders/35044"
  }
}
```

This endpoint creates an Order.

### HTTP Request

`POST api/v2/orders?businessUnitId=yourBusinessUnitId`

### Query Parameters

Parameter | Default | Description
-----------|---------|---------------------------------------
businessUnitId | null    | The id of the business unit to query against

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

# Order Items

## Get All Order Items for an Order

> Example Response:

```json
{
  "items": [
    {
      "orderId": 1,
      "id": 1,
      "featureSetId": "94771bf7-6b38-e911-8373-00155d026631",
      "quantity": 1,
      "enableFeedbackLink": false,
      "description": "M10999A - SQL Server on Linux (Standard - 180 days)",
      "_links": {
        "self": "/api/v2/orders/1/items"
      }
    }
  ],
  "_pageInfo": {
    "pageCount": 1,
    "totalItemCount": 1,
    "pageNumber": 1,
    "pageSize": 10,
    "hasPreviousPage": false,
    "hasNextPage": false,
    "isFirstPage": true,
    "isLastPage": true,
    "firstItemOnPage": 1,
    "lastItemOnPage": 1
  },
  "_links": {}
}
```

This endpoint returns a paginated set of Order Items for an Order.

### HTTP Request

`GET api/v2/orders/{orderId}/items?businessUnitId=yourBusinessUnitId`

### URL Parameters

Parameter | Description
--------- | -----------
orderId | The ID of the Order to retrieve

### Query Parameters

Parameter | Default | Description
-----------|---------|---------------------------------------
businessUnitId | null    | The id of the business unit to query against
_pageSize | 10      | The number of results to get per page
_page     | 1       | The page to get the results for

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>
