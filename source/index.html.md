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

> The following command returns JSON structured like this:

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

> The following command returns JSON structured like this:

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

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

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

# Feature Sets

## Get All Feature Sets for a Product

> The following command returns JSON structured like this:

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

> The following command returns JSON structured like this:

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

<aside class="success">
Remember — always include the businessUnitId as a query parameter! 
</aside>

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

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

