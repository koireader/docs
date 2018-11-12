---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - Shell
  - 
  # - ruby
  # - python
  # - javascript

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  # - <a href='https://github.com/lord/KoiReader'>Documentation Powered by KoiReader</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the KoiReader API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Node.js, Python. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

<!-- This example API documentation page was created with [KoiReader](https://github.com/lord/KoiReader). Feel free to edit it and use it as a base for your own API's documentation. -->

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request

  curl -X POST   https://api.koireader.io/demo  
    -H 'content-type: multipart/form-data' 
    -H 'X-ApiKey: APIKEY' -F 'file=@PATH'
```
 
<!-- ```python
import kittn

api = kittn.authorize('meowmeowmeow')
``` -->
<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
``` -->
<!-- ```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
``` -->

> Make sure to replace `APIKEY` with your API key and `PATH` with your file path.

KoiReader uses API keys to allow access to the API. You can register a new KoiReader API key at our [developer portal](https://www.dev.koireader.com  ).

KoiReader expects for the API key to be included in all API requests to the server in a header that looks like the following:

<!-- `Authorization: meowmeowmeow` -->
`X-ApiKey: APIKEY`

<aside class="notice">
<p>You must replace <code>APIKEY</code> with your personal API key 
  and <code>PATH</code> with your image path</p>
</aside>

# KoiReader

## Get All Kittens
<!-- 
```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
``` -->

```shell
curl -X POST   https://api.koireader.io/demo  
  -H 'content-type: multipart/form-data'  
  -H 'X-ApiKey: APIKEY' -F 'file=@PATH'
```
<!-- 
```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
``` -->

> The above command returns JSON structured like this:

```json
{
      "billing_address": "IOD Azeno Drive, Fuo Extension\nDuwommo, AR, TH\ngamzob.mw\nPhone (048) 6324002, E-mail:\nCatalina-Stroman65@yahoo.com", 
      "delivery_address": null, 
      "detected_total": "1049.24", 
      "discount": " Discount 7.5m", 
      "due_date": null, 
      "invoice_number": "", 
      "origin_address": "E#mcal\n1058 AMer Drive, Wopig Turnpike\nSocgihor, NY, BZ\niwuwf\nE-mail: SydneyKulas@gmail.com,\nPhone 1-232-04&5376", 
      "table": {
        "bbox": [ 392, 645, 627, 751 ], 
        "score": 0.888
      }, 
      "table_cells": [
        {
          "bbox": [ 392, 645, 427, 664 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 427, 645, 499, 664 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 499, 645, 564, 664 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 564, 645, 627, 664 ], 
          "score": 0.888
        }
      ], 
      "tax": "", 
      "tbody_cells": [
        {
          "bbox": [ 388, 664, 427, 695 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 388, 695, 427, 723 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 388, 723, 427, 751 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 427, 664, 499, 695 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 427, 695, 499, 723 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 427, 723, 499, 751 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 499, 664, 564, 695 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 499, 695, 564, 723 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 499, 723, 564, 751 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 564, 664, 627, 695 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 564, 695, 627, 723 ], 
          "score": 0.888
        }, 
        {
          "bbox": [ 564, 723, 627, 751 ], 
          "score": 0.888
        }
      ], 
      "thead_cells": [
        {
          "bbox": [ 392, 636, 427, 664 ], 
          "score": 0.7849044354445106
        }, 
        {
          "bbox": [ 392, 664, 427, 695 ], 
          "score": 0.7771857111559676
        }, 
        {
          "bbox": [ 392, 695, 427, 723 ], 
          "score": 0.7796395169709125
        }, 
        {
          "bbox": [ 392, 723, 427, 751 ], 
          "score": 0.7818072134697397
        }, 
        {
          "bbox": [ 427, 636, 499, 664 ], 
          "score": 0.7772328922191664
        }, 
        {
          "bbox": [ 427, 664, 499, 695 ], 
          "score": 0.7782663682152343
        }, 
        {
          "bbox": [ 427, 695, 499, 723 ], 
          "score": 0.7802614661733765
        }, 
        {
          "bbox": [ 427, 723, 499, 751 ], 
          "score": 0.7828320143019636
        }, 
        {
          "bbox": [ 499, 636, 564, 664 ], 
          "score": 0.7807302831368593
        }, 
        {
          "bbox": [ 499, 664, 564, 695 ], 
          "score": 0.7784177351319097
        }, 
        {
          "bbox": [ 499, 695, 564, 723 ], 
          "score": 0.7840718764970613
        }, 
        {
          "bbox": [ 499, 723, 564, 751 ], 
          "score": 0.7784465279682596
        }, 
        {
          "bbox": [ 564,636,627,664 ], 
          "score": 0.7824219669807985
        }, 
        {
          "bbox": [564,664,627,695], 
          "score": 0.7828738934377398
        }, 
        {
          "bbox": [564,695,627,723], 
          "score": 0.7783272564477546
        }, 
        {
          "bbox": [ 564, 723, 627, 751 ], 
          "score": 0.785752982999441
        }
      ]
    }
```

This endpoint retrieves all kittens.

### HTTP Request

`POST   https://api.koireader.io/demo`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

<!-- ## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

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
curl "http://example.com/api/kittens/2"
  -X DELETE
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
ID | The ID of the kitten to delete -->

