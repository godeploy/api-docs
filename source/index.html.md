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
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
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

