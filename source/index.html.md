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

> To connect, use this code:

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
print(response.json())
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
    console.log(body);
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
<!-- ```shell
curl -X POST   https://api.koireader.com/v1/analyze  
  -H 'content-type: multipart/form-data'  
  -H 'X-ApiKey: APIKEY' -F 'file=@/home/user/invoice.png'
``` -->
<!-- ```javascript
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
```  -->
> The above command returns JSON structured like this:

```json
{
	"status": true,
	"data": [{
		"tables": [{
			"summary": [
				[" Summary ", " By ", "To", "No. Of Items", " Amount"],
				["Bukmizu imo tukcez uwfih ducag bipew innasi weufogo UWUiSU ud tuecika cika hubmiw wuei iewsuc. ", "Home ", "Beauty ", "4", "633.84"],
				["Piko num  te biknai nedhi tarbor efivotri atpu  cicom paio mufiuiiu otizekom  li me. ", "Automotive", "Garden ", "78", "702.56"],
				["Keyboard ", "Table ", "Clothing", "", "530.06"],
				["Gloves ", "Fish ", "Books ", "76", "335.77"],
				["Da vosom zapi naiop vabeh oronovmu tolbigu hef wa uniec bavfopem  ki nitoz por dihomre  buzci iefoben. ", "Incredible  Wooden  Chicken ", "Gorgeous Fresh  Table ", "9", "632.87"],
				["Salad ", "Chair ", "Ergonomic Frozen  Shoes ", "WV", "703.76"],
				["Mouse ", "Chips ", "Shoes ", "8", "763.79"],
				["Bacon ", "Handcrafted Wooden  Computer ", "Licensed Steel  Salad ", "77", "250.27"],
				["Li udigadew si eb fa tev naruple uwi wikelgu  mezbez vevba lasiapevu nizzicu hosui  omidocoh. ", "Hat ", "Books ", "7", "970.63"],
				["Riumuvo buflopro duvedo faiuro unoravgi  cuseei ka ofi munbutus onniis zodiuha se  wihemmi io genpu vowziwpah kug luci. ", "Gloves ", "Baby ", "", "287.87"]
			],
			"metadata": {
				"bbox": [83, 479, 698, 1063],
				"score": 0.98,
				"page": 0
			},
			"cells": [{
				"bbox": [83, 479, 411, 542],
				"score": 0.98,
				"cellPosition": [0, 0],
				"text": " Summary "
			}, {
				"bbox": [411, 479, 508, 542],
				"score": 0.98,
				"cellPosition": [0, 1],
				"text": " By "
			}, {
				"bbox": [508, 479, 590, 542],
				"score": 0.98,
				"cellPosition": [0, 2],
				"text": "To"
			}, {
				"bbox": [590, 479, 638, 542],
				"score": 0.98,
				"cellPosition": [0, 3],
				"text": "No. Of Items"
			}, {
				"bbox": [638, 479, 698, 542],
				"score": 0.98,
				"cellPosition": [0, 4],
				"text": " Amount?"
			}, {
				"bbox": [83, 542, 411, 609],
				"score": 0.98,
				"cellPosition": [1, 0],
				"text": "Bukmizu imo tukcez uwfih ducag bipew innasi weufogo UWUiSU ud tuecika cika hubmiw wuei iewsuc. "
			}, {
				"bbox": [411, 542, 508, 609],
				"score": 0.98,
				"cellPosition": [1, 1],
				"text": "Home "
			}, {
				"bbox": [508, 542, 590, 609],
				"score": 0.98,
				"cellPosition": [1, 2],
				"text": "Beauty "
			}, {
				"bbox": [590, 542, 638, 609],
				"score": 0.98,
				"cellPosition": [1, 3],
				"text": "4"
			}, {
				"bbox": [638, 542, 698, 609],
				"score": 0.98,
				"cellPosition": [1, 4],
				"text": "633.84"
			}, {
				"bbox": [83, 609, 411, 656],
				"score": 0.98,
				"cellPosition": [2, 0],
				"text": "Piko num  te biknai nedhi tarbor efivotri atpu  cicom paio mufiuiiu otizekom  li me. "
			}, {
				"bbox": [411, 609, 508, 656],
				"score": 0.98,
				"cellPosition": [2, 1],
				"text": "Automotive"
			}, {
				"bbox": [508, 609, 590, 656],
				"score": 0.98,
				"cellPosition": [2, 2],
				"text": "Garden "
			}, {
				"bbox": [590, 609, 638, 656],
				"score": 0.98,
				"cellPosition": [2, 3],
				"text": "78"
			}, {
				"bbox": [638, 609, 698, 656],
				"score": 0.98,
				"cellPosition": [2, 4],
				"text": "702.56"
			}, {
				"bbox": [83, 656, 411, 681],
				"score": 0.98,
				"cellPosition": [3, 0],
				"text": "Keyboard "
			}, {
				"bbox": [411, 656, 508, 681],
				"score": 0.98,
				"cellPosition": [3, 1],
				"text": "Table "
			}, {
				"bbox": [508, 656, 590, 681],
				"score": 0.98,
				"cellPosition": [3, 2],
				"text": "Clothing"
			}, {
				"bbox": [590, 656, 638, 681],
				"score": 0.98,
				"cellPosition": [3, 3]
			}, {
				"bbox": [638, 656, 698, 681],
				"score": 0.98,
				"cellPosition": [3, 4],
				"text": "530.06"
			}, {
				"bbox": [83, 681, 411, 708],
				"score": 0.98,
				"cellPosition": [4, 0],
				"text": "Gloves "
			}, {
				"bbox": [411, 681, 508, 708],
				"score": 0.98,
				"cellPosition": [4, 1],
				"text": "Fish "
			}, {
				"bbox": [508, 681, 590, 708],
				"score": 0.98,
				"cellPosition": [4, 2],
				"text": "Books "
			}, {
				"bbox": [590, 681, 638, 708],
				"score": 0.98,
				"cellPosition": [4, 3],
				"text": "76"
			}, {
				"bbox": [638, 681, 698, 708],
				"score": 0.98,
				"cellPosition": [4, 4],
				"text": "335.77"
			}, {
				"bbox": [83, 708, 411, 774],
				"score": 0.98,
				"cellPosition": [5, 0],
				"text": "Da vosom zapi naiop vabeh oronovmu tolbigu hef wa uniec bavfopem  ki nitoz por dihomre  buzci iefoben. "
			}, {
				"bbox": [411, 708, 508, 774],
				"score": 0.98,
				"cellPosition": [5, 1],
				"text": "Incredible  Wooden  Chicken "
			}, {
				"bbox": [508, 708, 590, 774],
				"score": 0.98,
				"cellPosition": [5, 2],
				"text": "Gorgeous Fresh  Table "
			}, {
				"bbox": [590, 708, 638, 774],
				"score": 0.98,
				"cellPosition": [5, 3],
				"text": "9"
			}, {
				"bbox": [638, 708, 698, 774],
				"score": 0.98,
				"cellPosition": [5, 4],
				"text": "632.87"
			}, {
				"bbox": [83, 774, 411, 838],
				"score": 0.98,
				"cellPosition": [6, 0],
				"text": "Salad "
			}, {
				"bbox": [411, 774, 508, 838],
				"score": 0.98,
				"cellPosition": [6, 1],
				"text": "Chair "
			}, {
				"bbox": [508, 774, 590, 838],
				"score": 0.98,
				"cellPosition": [6, 2],
				"text": "Ergonomic Frozen  Shoes "
			}, {
				"bbox": [590, 774, 638, 838],
				"score": 0.98,
				"cellPosition": [6, 3],
				"text": "WV"
			}, {
				"bbox": [638, 774, 698, 838],
				"score": 0.98,
				"cellPosition": [6, 4],
				"text": "703.76"
			}, {
				"bbox": [83, 838, 411, 862],
				"score": 0.98,
				"cellPosition": [7, 0],
				"text": "Mouse "
			}, {
				"bbox": [411, 838, 508, 862],
				"score": 0.98,
				"cellPosition": [7, 1],
				"text": "Chips "
			}, {
				"bbox": [508, 838, 590, 862],
				"score": 0.98,
				"cellPosition": [7, 2],
				"text": "Shoes "
			}, {
				"bbox": [590, 838, 638, 862],
				"score": 0.98,
				"cellPosition": [7, 3],
				"text": "8"
			}, {
				"bbox": [638, 838, 698, 862],
				"score": 0.98,
				"cellPosition": [7, 4],
				"text": "763.79"
			}, {
				"bbox": [83, 862, 411, 930],
				"score": 0.98,
				"cellPosition": [8, 0],
				"text": "Bacon "
			}, {
				"bbox": [411, 862, 508, 930],
				"score": 0.98,
				"cellPosition": [8, 1],
				"text": "Handcrafted Wooden  Computer "
			}, {
				"bbox": [508, 862, 590, 930],
				"score": 0.98,
				"cellPosition": [8, 2],
				"text": "Licensed Steel  Salad "
			}, {
				"bbox": [590, 862, 638, 930],
				"score": 0.98,
				"cellPosition": [8, 3],
				"text": "77"
			}, {
				"bbox": [638, 862, 698, 930],
				"score": 0.98,
				"cellPosition": [8, 4],
				"text": "250.27"
			}, {
				"bbox": [83, 930, 411, 995],
				"score": 0.98,
				"cellPosition": [9, 0],
				"text": "Li udigadew si eb fa tev naruple uwi wikelgu  mezbez vevba lasiapevu nizzicu hosui  omidocoh. "
			}, {
				"bbox": [411, 930, 508, 995],
				"score": 0.98,
				"cellPosition": [9, 1],
				"text": "Hat "
			}, {
				"bbox": [508, 930, 590, 995],
				"score": 0.98,
				"cellPosition": [9, 2],
				"text": "Books "
			}, {
				"bbox": [590, 930, 638, 995],
				"score": 0.98,
				"cellPosition": [9, 3],
				"text": "7"
			}, {
				"bbox": [638, 930, 698, 995],
				"score": 0.98,
				"cellPosition": [9, 4],
				"text": "970.63"
			}, {
				"bbox": [83, 995, 411, 1063],
				"score": 0.98,
				"cellPosition": [10, 0],
				"text": "Riumuvo buflopro duvedo faiuro unoravgi  cuseei ka ofi munbutus onniis zodiuha se  wihemmi io genpu vowziwpah kug luci. "
			}, {
				"bbox": [411, 995, 508, 1063],
				"score": 0.98,
				"cellPosition": [10, 1],
				"text": "Gloves "
			}, {
				"bbox": [508, 995, 590, 1063],
				"score": 0.98,
				"cellPosition": [10, 2],
				"text": "Baby "
			}, {
				"bbox": [590, 995, 638, 1063],
				"score": 0.98,
				"cellPosition": [10, 3]
			}, {
				"bbox": [638, 995, 698, 1063],
				"score": 0.98,
				"cellPosition": [10, 4],
				"text": "287.87"
			}]
		}],
		"billingAddress": [{
			"text": "Billing Edress\n2000 Logwof Place, Soto Court\nDugikfu, GA, HT\nfo.to\nPhone: (467) 348-5266, E-mail:\nOmer83@hotmail.com"
		}],
		"originAddress": [{
			"text": "Gibson - Carroll\nVersatile dynamic algorithm\n7454 Lussol Lane, Olie Center\nEcfogso, IL, SH\nfo.ci\nPhone: 7-570-089-2277, E-mail:\nLucious79@gmail.com"
		}],
		"deliveryAddress": [{
			"text": "Shipping to\n7 936 Pupta Extension, Ukida Loop\nSugalec, OK, Fl\nkagono.pf\nPhone: 7-780-736-2757, E-mail:\nJohnathon 95@hotmail.com"
		}],
		"tax": [{
			"text": null,
			"page": 0
		}],
		"detectedTotal": [{
			"text": null,
			"page": 0
		}],
		"detectedSubtotal": [{
			"text": null,
			"page": 0
		}],
		"discount": [{
			"text": null,
			"page": 0
		}],
		"dueDate": [{
			"text": "2108-02-21"
		}],
		"invoiceDate": [{
			"text": null,
			"page": 0
		}],
		"invoiceId": [{
			"text": "#24c75d2d"
		}],
		"metadata": {
			"info": "Detected Table",
			"dimensions": [1257, 1115],
			"numOfPages": 1,
			"docname": "file-2.png"
		},
		"status": true
	}],
	"statusMessage": "Processed"
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




