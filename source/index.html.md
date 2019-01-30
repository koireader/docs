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
    -H 'X-ApiKey: APIKEY' -F 'file=@/home/user/invoice.png'
```

 
```python
import requests
headers = { 
    "X-ApiKey": 'APIKEY'
}
response = requests.post('https://api.koireader.com/v1/analyze', files={'file': open('./invoice.png', 'rb')}, headers=headers)
print(response.json()['invoice.png'])
```
```javascript
const fs = require('fs');
const request = require('request');
const options = {
    method: "POST",
    url: 'https://api.koireader.com/v1/analyze',
    headers: {
        "Content-Type": "multipart/form-data",
        "X-ApiKey": 'APIKEY'
    },
    formData: {
        "file": fs.createReadStream("./invoice.png")
    }
};
request(options, function(err, res, body) {
    if (err) console.log(err);
    console.log(body['invoice.png']);
});
``` 
<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
``` -->


> Make sure to enter a valid image path and replace <code>APIKEY</code> with your API key .

Authenticate your account by including your API key in API requests. You can generate or change your API key using the <a href='https://dev.koireader.com' target='_blank'>Dashboard</a>. Your API key carries many privileges, so be sure to keep them secure! Do not share your API key in publicly accessible areas such as GitHub, client-side code, and so forth.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail. The end points expect for the API key to be included in all API requests to the server in a header that looks like the following:

<!-- `Authorization: meowmeowmeow` -->
`X-ApiKey: APIKEY`

<aside class="notice">
<p class = 'notice-para'>You must enter a valid image path and replace <code>APIKEY</code> with your personal API key.
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
  -H 'X-ApiKey: APIKEY' -F 'file=@/home/user/invoice.png'
```
```javascript
const fs = require('fs');
const request = require('request');
const options = {
    method: "POST",
    url: 'https://api.koireader.com/v1/analyze',
    headers: {
        "Content-Type": "multipart/form-data",
        "X-ApiKey": 'APIKEY'
    },
    formData: {
        "file": fs.createReadStream("./invoice.png")
    }
};
request(options, function(err, res, body) {
    if (err) console.log(err);
    console.log(body['invoice.png']);
});
```

```python
import requests
headers = { 
    "X-ApiKey": 'APIKEY'
}
response = requests.post('https://api.koireader.com/v1/analyze', files={'file': open('./invoice.png', 'rb')}, headers=headers)
print(response.json()['invoice.png'])
``` 
> The above command returns JSON structured like this:

```json
{
	"delivery_address": [{"text": None,"page": "0"}, {"text": "Delivery","page": "1"}],
	"tax": [{"text": None,"page": "0"}, {"text": "1223","page": "1"}],
	"detected_total": [{"text": "$ 123987","page": "0"},{"text": "$ 56785","page": "1"}],
	"origin_address": [{"text": "Delhi","page": "0"},{"text": None,"page": "1"}],
	"processed_image_dims": None,
	"status": "true",
	"num_of_pages": "2",
	"billing_address": [{"text": "ABC","page": "0"},{"text": "Hello","page": "1"}],
	"discount": [{"text": "$109667","page": "0"},{"text": None,"page": "1"}],
	"tables": [{
		"metadata": {
			"page": 2,
			"bbox": [64, 146, 509, 383],
			"score": 0.9
		},
		"summary": [
			["", "Participation", "Attainment", "EEI", "GPI", "Overall rank"],
			["Netherlands", "3", "3=", "1", "1=", "1"],
			["Finland", "1", "8", "5", "5=", "2"],
			["UK", "5", "5=", "2", "5=", "3"],
			["US", "7=", "1", "7", "12", "4"],
			["Canada", "7=", "2", "3=", "10=", "5"],
			["Australia", "6", "3=", "6", "7", "6"],
			["Ireland", "12", "5=", "3=", "9", "7"],
			["France", "4", "9", "8=", "8", "8"],
			["Sweden", "9=", "7", "8=", "13", "9"],
			["Italy", "2", "12", "10", "10=", "10"],
			["Germany", "13", "11", "11", "1=", "11"],
			["Belgium", "9=", "10", "13", "3", "12"],
			["Austria", "9=", "13", "12", "4", "13"]
		],
		"cells": [{
			"text": "",
			"cell_position": [0, 0]
		}, {
			"text": "Participation",
			"cell_position": [0, 1]
		}, {
			"text": "Attainment",
			"cell_position": [0, 2]
		}, {
			"text": "EEI",
			"cell_position": [0, 3]
		}, {
			"text": "GPI",
			"cell_position": [0, 4]
		}, {
			"text": "Overall rank",
			"cell_position": [0, 5]
		}, {
			"text": "Netherlands",
			"cell_position": [1, 0]
		}, {
			"text": "3",
			"cell_position": [1, 1]
		}, {
			"text": "3=",
			"cell_position": [1, 2]
		}, {
			"text": "1",
			"cell_position": [1, 3]
		}, {
			"text": "1=",
			"cell_position": [1, 4]
		}, {
			"text": "1",
			"cell_position": [1, 5]
		}, {
			"text": "Finland",
			"cell_position": [2, 0]
		}, {
			"text": "1",
			"cell_position": [2, 1]
		}, {
			"text": "8",
			"cell_position": [2, 2]
		}, {
			"text": "5",
			"cell_position": [2, 3]
		}, {
			"text": "5=",
			"cell_position": [2, 4]
		}, {
			"text": "2",
			"cell_position": [2, 5]
		}, {
			"text": "UK",
			"cell_position": [3, 0]
		}, {
			"text": "5",
			"cell_position": [3, 1]
		}, {
			"text": "5=",
			"cell_position": [3, 2]
		}, {
			"text": "2",
			"cell_position": [3, 3]
		}, {
			"text": "5=",
			"cell_position": [3, 4]
		}, {
			"text": "3",
			"cell_position": [3, 5]
		}, {
			"text": "US",
			"cell_position": [4, 0]
		}, {
			"text": "7=",
			"cell_position": [4, 1]
		}, {
			"text": "1",
			"cell_position": [4, 2]
		}, {
			"text": "7",
			"cell_position": [4, 3]
		}, {
			"text": "12",
			"cell_position": [4, 4]
		}, {
			"text": "4",
			"cell_position": [4, 5]
		}, {
			"text": "Canada",
			"cell_position": [5, 0]
		}, {
			"text": "7=",
			"cell_position": [5, 1]
		}, {
			"text": "2",
			"cell_position": [5, 2]
		}, {
			"text": "3=",
			"cell_position": [5, 3]
		}, {
			"text": "10=",
			"cell_position": [5, 4]
		}, {
			"text": "5",
			"cell_position": [5, 5]
		}, {
			"text": "Australia",
			"cell_position": [6, 0]
		}, {
			"text": "6",
			"cell_position": [6, 1]
		}, {
			"text": "3=",
			"cell_position": [6, 2]
		}, {
			"text": "6",
			"cell_position": [6, 3]
		}, {
			"text": "7",
			"cell_position": [6, 4]
		}, {
			"text": "6",
			"cell_position": [6, 5]
		}, {
			"text": "Ireland",
			"cell_position": [7, 0]
		}, {
			"text": "12",
			"cell_position": [7, 1]
		}, {
			"text": "5=",
			"cell_position": [7, 2]
		}, {
			"text": "3=",
			"cell_position": [7, 3]
		}, {
			"text": "9",
			"cell_position": [7, 4]
		}, {
			"text": "7",
			"cell_position": [7, 5]
		}, {
			"text": "France",
			"cell_position": [8, 0]
		}, {
			"text": "4",
			"cell_position": [8, 1]
		}, {
			"text": "9",
			"cell_position": [8, 2]
		}, {
			"text": "8=",
			"cell_position": [8, 3]
		}, {
			"text": "8",
			"cell_position": [8, 4]
		}, {
			"text": "8",
			"cell_position": [8, 5]
		}, {
			"text": "Sweden",
			"cell_position": [9, 0]
		}, {
			"text": "9=",
			"cell_position": [9, 1]
		}, {
			"text": "7",
			"cell_position": [9, 2]
		}, {
			"text": "8=",
			"cell_position": [9, 3]
		}, {
			"text": "13",
			"cell_position": [9, 4]
		}, {
			"text": "9",
			"cell_position": [9, 5]
		}, {
			"text": "Italy",
			"cell_position": [10, 0]
		}, {
			"text": "2",
			"cell_position": [10, 1]
		}, {
			"text": "12",
			"cell_position": [10, 2]
		}, {
			"text": "10",
			"cell_position": [10, 3]
		}, {
			"text": "10=",
			"cell_position": [10, 4]
		}, {
			"text": "10",
			"cell_position": [10, 5]
		}, {
			"text": "Germany",
			"cell_position": [11, 0]
		}, {
			"text": "13",
			"cell_position": [11, 1]
		}, {
			"text": "11",
			"cell_position": [11, 2]
		}, {
			"text": "11",
			"cell_position": [11, 3]
		}, {
			"text": "1=",
			"cell_position": [11, 4]
		}, {
			"text": "11",
			"cell_position": [11, 5]
		}, {
			"text": "Belgium",
			"cell_position": [12, 0]
		}, {
			"text": "9=",
			"cell_position": [12, 1]
		}, {
			"text": "10",
			"cell_position": [12, 2]
		}, {
			"text": "13",
			"cell_position": [12, 3]
		}, {
			"text": "3",
			"cell_position": [12, 4]
		}, {
			"text": "12",
			"cell_position": [12, 5]
		}, {
			"text": "Austria",
			"cell_position": [13, 0]
		}, {
			"text": "9=",
			"cell_position": [13, 1]
		}, {
			"text": "13",
			"cell_position": [13, 2]
		}, {
			"text": "12",
			"cell_position": [13, 3]
		}, {
			"text": "4",
			"cell_position": [13, 4]
		}, {
			"text": "13",
			"cell_position": [13, 5]
		}]
	}],
	"due_date": [{"text": None,"page": "0"},{"text": "2019-10-13","page": "1"}],
	
	"invoice_id": [{"text": "#12356","page": "0"},{"text": None,"page": "1"}]
}
```

This endpoint retrieves context and text from the documents .

### HTTPS Request

`POST   https://api.koireader.com/v1/analyze`

<!-- ### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include KoiReaders that have already been adopted. -->

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
# Supported Documents
<b>File Formats</b>

<p>KoiReader API supports the following file types:</p>
  
  * PDF 
  * JPEG
  * PNG8
  * PNG24
  * BMP
  * WEBP
  * TIFF


Note that some of these image formats are "lossy" (for example, JPEG). Reducing file sizes for such lossy formats may result in a degradation of image quality, and hence, KoiReader API accuracy.

<b>Image Sizing</b> 

<p>To enable accurate image detection within the KoiReader API, images should generally be a minimum of 640 x 480 pixels (about 300k pixels).</p>

<aside class="notice">
<p class = 'notice-para'>Generally, KoiReader API requires images to be a sufficient size so that important features within the request can be easily distinguished. Sizes smaller or larger than these recommended sizes may work. However, smaller sizes may result in lower accuracy, while larger sizes may increase processing time and bandwidth usage.</p>
</aside>

<b>File Size</b> 

<p>Image files sent to KoiReader API should not exceed 10MB. Reducing your file size can significantly improve throughput; however, be careful not to reduce image quality in the process. Note that the KoiReader API imposes a 10MB JSON request size limit.</p>

<b>Number of Pages</b>

<p>Maximum number of supported pages per invoice is 20. Any document with more pages than this will not be processed. You will receive error code <i>413</i> if this happens.</p>




