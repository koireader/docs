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
	"origin_address": [
		{
		"page": 0,
		"text": null
		}
	],
	"tax": [
		{
		"page": 1,
		"text": null
		}
	],
	"discount": [
		{
		"page": 0,
		"text": null
		}
	],
	"tables": [
		{
		"metadata": {
			"score": 0.98,
			"bbox": [
				134,
				711,
				384,
				928
			],
			"page": 0
		},
		"cells": [
			{
				"score": 0.98,
				"text": " Item #",
				"cell_position": [
					0,
					0
				],
				"bbox": [
					134,
					711,
					186,
					740
				]
			},
			{
				"score": 0.98,
				"text": " Charges",
				"cell_position": [
					0,
					1
				],
				"bbox": [
					186,
					711,
					249,
					740
				]
			},
			{
				"score": 0.98,
				"text": " Quantity",
				"cell_position": [
					0,
					2
				],
				"bbox": [
					249,
					711,
					314,
					740
				]
			},
			{
				"score": 0.98,
				"text": " Pay Total",
				"cell_position": [
					0,
					3
				],
				"bbox": [
					314,
					711,
					384,
					740
				]
			},
			{
				"score": 0.98,
				"text": "512",
				"cell_position": [
					1,
					0
				],
				"bbox": [
					134,
					740,
					186,
					773
				]
			},
			{
				"score": 0.98,
				"text": "215.58",
				"cell_position": [
					1,
					1
				],
				"bbox": [
					186,
					740,
					249,
					773
				]
			},
			{
				"score": 0.98,
				"text": "10",
				"cell_position": [
					1,
					2
				],
				"bbox": [
					249,
					740,
					314,
					773
				]
			},
			{
				"score": 0.98,
				"text": "726.02",
				"cell_position": [
					1,
					3
				],
				"bbox": [
					314,
					740,
					384,
					773
				]
			},
			{
				"score": 0.98,
				"text": "150",
				"cell_position": [
					2,
					0
				],
				"bbox": [
					134,
					773,
					186,
					804
				]
			},
			{
				"score": 0.98,
				"text": "108.76",
				"cell_position": [
					2,
					1
				],
				"bbox": [
					186,
					773,
					249,
					804
				]
			},
			{
				"score": 0.98,
				"text": "3",
				"cell_position": [
					2,
					2
				],
				"bbox": [
					249,
					773,
					314,
					804
				]
			},
			{
				"score": 0.98,
				"text": "48.62",
				"cell_position": [
					2,
					3
				],
				"bbox": [
					314,
					773,
					384,
					804
				]
			},
			{
				"score": 0.98,
				"text": "590",
				"cell_position": [
					3,
					0
				],
				"bbox": [
					134,
					804,
					186,
					834
				]
			},
			{
				"score": 0.98,
				"text": "335.52",
				"cell_position": [
					3,
					1
				],
				"bbox": [
					186,
					804,
					249,
					834
				]
			},
			{
				"score": 0.98,
				"text": "19",
				"cell_position": [
					3,
					2
				],
				"bbox": [
					249,
					804,
					314,
					834
				]
			},
			{
				"score": 0.98,
				"text": "908.4",
				"cell_position": [
					3,
					3
				],
				"bbox": [
					314,
					804,
					384,
					834
				]
			},
			{
				"score": 0.98,
				"text": "300",
				"cell_position": [
					4,
					0
				],
				"bbox": [
					134,
					834,
					186,
					864
				]
			},
			{
				"score": 0.98,
				"text": "667.53",
				"cell_position": [
					4,
					1
				],
				"bbox": [
					186,
					834,
					249,
					864
				]
			},
			{
				"score": 0.98,
				"text": "9",
				"cell_position": [
					4,
					2
				],
				"bbox": [
					249,
					834,
					314,
					864
				]
			},
			{
				"score": 0.98,
				"text": "555,.14",
				"cell_position": [
					4,
					3
				],
				"bbox": [
					314,
					834,
					384,
					864
				]
			},
			{
				"score": 0.98,
				"text": "849",
				"cell_position": [
					5,
					0
				],
				"bbox": [
					134,
					864,
					186,
					896
				]
			},
			{
				"score": 0.98,
				"text": "507.47",
				"cell_position": [
					5,
					1
				],
				"bbox": [
					186,
					864,
					249,
					896
				]
			},
			{
				"score": 0.98,
				"text": "",
				"cell_position": [
					5,
					2
				],
				"bbox": [
					249,
					864,
					314,
					896
				]
			},
			{
				"score": 0.98,
				"text": "468.66",
				"cell_position": [
					5,
					3
				],
				"bbox": [
					314,
					864,
					384,
					896
				]
			},
			{
				"score": 0.98,
				"text": "126",
				"cell_position": [
					6,
					0
				],
				"bbox": [
					134,
					896,
					186,
					928
				]
			},
			{
				"score": 0.98,
				"text": "397.01",
				"cell_position": [
					6,
					1
				],
				"bbox": [
					186,
					896,
					249,
					928
				]
			},
			{
				"score": 0.98,
				"text": "8",
				"cell_position": [
					6,
					2
				],
				"bbox": [
					249,
					896,
					314,
					928
				]
			},
			{
				"score": 0.98,
				"text": "468.21",
				"cell_position": [
					6,
					3
				],
				"bbox": [
					314,
					896,
					384,
					928
				]
			}
		],
		"summary": [
				[" Item #"," Charges"," Quantity"," Pay Total"],
				["512","215.58","10","726.02"],
				["150","108.76","3","48.62"],
				["590","335.52","19","908.4"],
				["300","667.53","9","555,.14"],
				["849","507.47","","468.66"],
				["126","397.01","8","468.21"]
			]
		}
	],
	"metadata": {
		"num_of_pages": 1,
		"dimensions": [
		1209,
		1059,
		3
		],
		"info": "Detected Table"
	},
	"billing_address": [
		{
		"page": 0,
		"text": "Bill to\n199 Nukle Key, Darof Glen\nOgefuve, NV, BY\nhovfop.im\nPhone: 716.222.5777, E-mail: Herminio_Reynolds44@hotmail.com"
		}
	],
	"detected_total": [
		{
		"page": 0,
		"text": "$ 751.82"
		}
	],
	"invoice_id": [
		{
		"page": 0,
		"text": "#7ece1e20"
		}
	],
	"delivery_address": [
		{
		"page": 0,
		"text": "o Ship:\n998 Fojgi Manor, Botpu Square\nLesabem, FL, JP\nri.mn\nE-mail: Barbara_Becker78@gmail.com, Phone:\n(012) 653-3315 x4427"
		}
	],
	"due_date": [
		{
		"page": 0,
		"text": null
		}
	],
	"detected_subtotal": [
		{
		"page": 0,
		"text": null
		}
	],
	"status": true
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




