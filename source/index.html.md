---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell : Shell
  - javascript : Node.js
  #- ruby
  - python : Python
  # - javascript

toc_footers:
  - <a href='https://dev.koireader.com' target="_blank">Sign Up for a Developer Key</a>
  # - <a href='https://github.com/lord/KoiReader'>Documentation Powered by KoiReader</a>

includes:
  - errors

search: true
---

# Introduction

KoiReader API is organized around REST. Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support cross-origin resource sharing, allowing you to interact securely with our API from a client-side web application (though you should never expose your API key in any public website's client-side code). JSON is returned by all API responses, including errors.

We have currently enlisted language bindings for Shell, Node.js, and Python. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

<!-- This example API documentation page was created with [KoiReader](https://github.com/lord/KoiReader). Feel free to edit it and use it as a base for your own API's documentation. -->

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request

  curl -X POST   https://api.koireader.com/v1/analyze  
    -H 'content-type: multipart/form-data' 
    -H 'X-ApiKey: APIKEY' -F 'file=@PATH'
```

 
```python
import kittn

api = kittn.authorize('meowmeowmeow')
```
```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
``` 
<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
``` -->


> Make sure to replace <code>APIKEY</code> with your API key and <code>PATH</code> with your file path.

Authenticate your account by including your API key in API requests. You can generate or change your API key using the <a href='https://dev.koireader.com' target='_blank'>Dashboard</a>. Your API key carries many privileges, so be sure to keep them secure! Do not share your API key in publicly accessible areas such as GitHub, client-side code, and so forth.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail. The end points expect for the API key to be included in all API requests to the server in a header that looks like the following:

<!-- `Authorization: meowmeowmeow` -->
`X-ApiKey: APIKEY`

<aside class="notice">
<p class = 'notice-para'>You must replace <code>APIKEY</code> with your personal API key 
  and <code>PATH</code> with your image path</p>
</aside>

# API Reference

## Get Context From Documents
<!-- 
```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.KoiReaders.get
```
-->
```shell
curl -X POST   https://api.koireader.com/v1/analyze  
  -H 'content-type: multipart/form-data'  
  -H 'X-ApiKey: APIKEY' -F 'file=@PATH'
```
```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let KoiReaders = api.KoiReaders.get();
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.KoiReaders.get()
``` 




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

This endpoint retrieves context and text from the documents .

### HTTPS Request

`POST   https://api.koireader.com/v1/analyze`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include KoiReaders that have already been adopted.

<aside class="success">
<p class = 'success-para'>Remember — to use an authenticated KoiReader API !</p>
</aside>

<!-- ## Get a Specific KoiReader

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.KoiReaders.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.KoiReaders.get(2)
```

```shell
curl "http://example.com/api/KoiReaders/2"
  -H "Authorization: meowmeowmeow"
```

 ```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.KoiReaders.get(2);
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

This endpoint retrieves a specific KoiReader.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/KoiReaders/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the KoiReader to retrieve

## Delete a Specific KoiReader

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.KoiReaders.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.KoiReaders.delete(2)
```

```shell
curl "http://example.com/api/KoiReaders/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.KoiReaders.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific KoiReader.

### HTTP Request

`DELETE http://example.com/KoiReaders/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the KoiReader to delete 
 -->
# Supported Images
<b>File Formats</b>

<p>KoiReader API supports the following file types:</p>

  * JPEG
  * PNG8
  * PNG24
  * BMP
  * WEBP
  * PDF 
  * TIFF


Note that some of these image formats are "lossy" (for example, JPEG). Reducing file sizes for such lossy formats may result in a degradation of image quality, and hence, KoiReader API accuracy.

<b>Image Sizing</b> 

<p>To enable accurate image detection within the KoiReader API, images should generally be a minimum of 640 x 480 pixels (about 300k pixels).</p>

<aside class="notice">
<p class = 'notice-para'>Generally, KoiReader API requires images to be a sufficient size so that important features within the request can be easily distinguished. Sizes smaller or larger than these recommended sizes may work. However, smaller sizes may result in lower accuracy, while larger sizes may increase processing time and bandwidth usage.</p>
</aside>

<b>File Size</b> 

<p>Image files sent to KoiReader API should not exceed 10MB. Reducing your file size can significantly improve throughput; however, be careful not to reduce image quality in the process. Note that the KoiReader API imposes a 10MB JSON request size limit.</p>

