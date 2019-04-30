---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell : Shell
  - javascript : Node.js
  #- ruby
  - python : Python
  # - javascript

toc_footers:
  - <a href='https://dev.koireader.com/signupLogin?action=signup' target="_blank">Sign Up for a Developer Key</a>
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
				["Item ", " W Product Dells", " To ", " Charges", " W quantity", "Grand  Total"],
				["631", "Generic Fresh Pizza Sleek Frozen Tuna ", "Computers", "368.57", "5", "872.88"],
				["704", "Generic Frozen Bike,  Handmade Granite Mouse", "Sleek son  Table ", "237.37", "20", "268.38"],
				["88", "Unbranded Granite Hat,  Small Plastic Cheese ", "Unbranded Fresh Car ", "586.62", "9", "723.25"],
				["548", "Practical Metal Car, Generic  Soap ", "Gloves ", "475.25", "1", "838.03"],
				["902", "Practical Wooden PA  Unbranded  Bike ", "Small  Wooden  Char ", "367.49", "10", "446.08"],
				["569", "Ergonomic Rubber Shoes, Unbranded Wooden  Computer ", "Computers", "18.08", "13", "759.29"],
				["776", "Tasy Frozen Cheese,  Rustic Concrete Tuna ", "Games", "75.72", "14", "619.96"],
				["597", "Ergonomic Frozen Fish,  TasW Plastic Mouse ", "Practical  Rubber  Shoes ", "548.62", "13", "665.91"]
			],
			"metadata": {
				"bbox": [72, 564, 574, 1007],
				"score": 0.98,
				"page": 0
			},
			"cells": [{
				"bbox": [72, 564, 106, 608],
				"score": 0.98,
				"cellPosition": [0, 0],
				"text": "Item "
			}, {
				"bbox": [106, 564, 297, 608],
				"score": 0.98,
				"cellPosition": [0, 1],
				"text": " W Product Dells"
			}, {
				"bbox": [297, 564, 391, 608],
				"score": 0.98,
				"cellPosition": [0, 2],
				"text": " To "
			}, {
				"bbox": [391, 564, 458, 608],
				"score": 0.98,
				"cellPosition": [0, 3],
				"text": " Charges"
			}, {
				"bbox": [458, 564, 522, 608],
				"score": 0.98,
				"cellPosition": [0, 4],
				"text": " W quantity"
			}, {
				"bbox": [522, 564, 574, 608],
				"score": 0.98,
				"cellPosition": [0, 5],
				"text": "Grand  Total"
			}, {
				"bbox": [72, 608, 106, 652],
				"score": 0.98,
				"cellPosition": [1, 0],
				"text": "631"
			}, {
				"bbox": [106, 608, 297, 652],
				"score": 0.98,
				"cellPosition": [1, 1],
				"text": "Generic Fresh Pizza Sleek Frozen Tuna "
			}, {
				"bbox": [297, 608, 391, 652],
				"score": 0.98,
				"cellPosition": [1, 2],
				"text": "Computers"
			}, {
				"bbox": [391, 608, 458, 652],
				"score": 0.98,
				"cellPosition": [1, 3],
				"text": "368.57"
			}, {
				"bbox": [458, 608, 522, 652],
				"score": 0.98,
				"cellPosition": [1, 4],
				"text": "5"
			}, {
				"bbox": [522, 608, 574, 652],
				"score": 0.98,
				"cellPosition": [1, 5],
				"text": "872.88"
			}, {
				"bbox": [72, 652, 106, 696],
				"score": 0.98,
				"cellPosition": [2, 0],
				"text": "704"
			}, {
				"bbox": [106, 652, 297, 696],
				"score": 0.98,
				"cellPosition": [2, 1],
				"text": "Generic Frozen Bike,  Handmade Granite Mouse"
			}, {
				"bbox": [297, 652, 391, 696],
				"score": 0.98,
				"cellPosition": [2, 2],
				"text": "Sleek son  Table "
			}, {
				"bbox": [391, 652, 458, 696],
				"score": 0.98,
				"cellPosition": [2, 3],
				"text": "237.37"
			}, {
				"bbox": [458, 652, 522, 696],
				"score": 0.98,
				"cellPosition": [2, 4],
				"text": "20"
			}, {
				"bbox": [522, 652, 574, 696],
				"score": 0.98,
				"cellPosition": [2, 5],
				"text": "268.38"
			}, {
				"bbox": [72, 696, 106, 738],
				"score": 0.98,
				"cellPosition": [3, 0],
				"text": "88"
			}, {
				"bbox": [106, 696, 297, 738],
				"score": 0.98,
				"cellPosition": [3, 1],
				"text": "Unbranded Granite Hat,  Small Plastic Cheese "
			}, {
				"bbox": [297, 696, 391, 738],
				"score": 0.98,
				"cellPosition": [3, 2],
				"text": "Unbranded Fresh Car "
			}, {
				"bbox": [391, 696, 458, 738],
				"score": 0.98,
				"cellPosition": [3, 3],
				"text": "586.62"
			}, {
				"bbox": [458, 696, 522, 738],
				"score": 0.98,
				"cellPosition": [3, 4],
				"text": "9"
			}, {
				"bbox": [522, 696, 574, 738],
				"score": 0.98,
				"cellPosition": [3, 5],
				"text": "723.25"
			}, {
				"bbox": [72, 738, 106, 781],
				"score": 0.98,
				"cellPosition": [4, 0],
				"text": "548"
			}, {
				"bbox": [106, 738, 297, 781],
				"score": 0.98,
				"cellPosition": [4, 1],
				"text": "Practical Metal Car, Generic  Soap "
			}, {
				"bbox": [297, 738, 391, 781],
				"score": 0.98,
				"cellPosition": [4, 2],
				"text": "Gloves "
			}, {
				"bbox": [391, 738, 458, 781],
				"score": 0.98,
				"cellPosition": [4, 3],
				"text": "475.25"
			}, {
				"bbox": [458, 738, 522, 781],
				"score": 0.98,
				"cellPosition": [4, 4],
				"text": "1"
			}, {
				"bbox": [522, 738, 574, 781],
				"score": 0.98,
				"cellPosition": [4, 5],
				"text": "838.03"
			}, {
				"bbox": [72, 781, 106, 844],
				"score": 0.98,
				"cellPosition": [5, 0],
				"text": "902"
			}, {
				"bbox": [106, 781, 297, 844],
				"score": 0.98,
				"cellPosition": [5, 1],
				"text": "Practical Wooden PA  Unbranded  Bike "
			}, {
				"bbox": [297, 781, 391, 844],
				"score": 0.98,
				"cellPosition": [5, 2],
				"text": "Small  Wooden  Char "
			}, {
				"bbox": [391, 781, 458, 844],
				"score": 0.98,
				"cellPosition": [5, 3],
				"text": "367.49"
			}, {
				"bbox": [458, 781, 522, 844],
				"score": 0.98,
				"cellPosition": [5, 4],
				"text": "10"
			}, {
				"bbox": [522, 781, 574, 844],
				"score": 0.98,
				"cellPosition": [5, 5],
				"text": "446.08"
			}, {
				"bbox": [72, 844, 106, 902],
				"score": 0.98,
				"cellPosition": [6, 0],
				"text": "569"
			}, {
				"bbox": [106, 844, 297, 902],
				"score": 0.98,
				"cellPosition": [6, 1],
				"text": "Ergonomic Rubber Shoes, Unbranded Wooden  Computer "
			}, {
				"bbox": [297, 844, 391, 902],
				"score": 0.98,
				"cellPosition": [6, 2],
				"text": "Computers"
			}, {
				"bbox": [391, 844, 458, 902],
				"score": 0.98,
				"cellPosition": [6, 3],
				"text": "18.08"
			}, {
				"bbox": [458, 844, 522, 902],
				"score": 0.98,
				"cellPosition": [6, 4],
				"text": "13"
			}, {
				"bbox": [522, 844, 574, 902],
				"score": 0.98,
				"cellPosition": [6, 5],
				"text": "759.29"
			}, {
				"bbox": [72, 902, 106, 951],
				"score": 0.98,
				"cellPosition": [7, 0],
				"text": "776"
			}, {
				"bbox": [106, 902, 297, 951],
				"score": 0.98,
				"cellPosition": [7, 1],
				"text": "Tasy Frozen Cheese,  Rustic Concrete Tuna "
			}, {
				"bbox": [297, 902, 391, 951],
				"score": 0.98,
				"cellPosition": [7, 2],
				"text": "Games"
			}, {
				"bbox": [391, 902, 458, 951],
				"score": 0.98,
				"cellPosition": [7, 3],
				"text": "75.72"
			}, {
				"bbox": [458, 902, 522, 951],
				"score": 0.98,
				"cellPosition": [7, 4],
				"text": "14"
			}, {
				"bbox": [522, 902, 574, 951],
				"score": 0.98,
				"cellPosition": [7, 5],
				"text": "619.96"
			}, {
				"bbox": [72, 951, 106, 1007],
				"score": 0.98,
				"cellPosition": [8, 0],
				"text": "597"
			}, {
				"bbox": [106, 951, 297, 1007],
				"score": 0.98,
				"cellPosition": [8, 1],
				"text": "Ergonomic Frozen Fish,  TasW Plastic Mouse "
			}, {
				"bbox": [297, 951, 391, 1007],
				"score": 0.98,
				"cellPosition": [8, 2],
				"text": "Practical  Rubber  Shoes "
			}, {
				"bbox": [391, 951, 458, 1007],
				"score": 0.98,
				"cellPosition": [8, 3],
				"text": "548.62"
			}, {
				"bbox": [458, 951, 522, 1007],
				"score": 0.98,
				"cellPosition": [8, 4],
				"text": "13"
			}, {
				"bbox": [522, 951, 574, 1007],
				"score": 0.98,
				"cellPosition": [8, 5],
				"text": "665.91"
			}]
		}],
		"billingAddress": [{
			"text": "Bill Mdress\n1231 Zeol Point, Voeke Helghb\nHolnme, WI, CF\nfefruugi.ar\nPhone: 065498-1594 '(3103, E.nall:\nAlison.Grady90@gmaII.com",
			"page": 0
		}],
		"originAddress": [{
			"text": "Hansen, Gottlieb and Johns\nImpactful\n1521 VevhuJ Steet, Honln Extension\nEkezodo, CT, JM\ncud.nl\nEqnan: Asa.wunsch@gmallcom, Phone: 1-718485-6225",
			"page": 0
		}],
		"deliveryAddress": [{
			"text": "Ship to Address\n414 FWb Road, GegJat Road\nTeJawtf, WI, AO\nogesetoj.uy\nEqnall: Doyle64@yahoo.com,\nPhone: 999-731-2964 x8653",
			"page": 0
		}],
		"tax": [{
			"text": " 16.36%",
			"page": 0
		}],
		"detectedTotal": [{
			"text": "Ft 1715.86",
			"page": 0
		}],
		"detectedSubtotal": [{
			"text": null,
			"page": 0
		}],
		"discount": [{
			"text": " 1588.1",
			"page": 0
		}],
		"dueDate": [{
			"text": null,
			"page": 0
		}],
		"invoiceDate": [{
			"text": null,
			"page": 0
		}],
		"invoiceId": [{
			"text": "k4840206",
			"page": 0
		}],
		"metadata": {
			"info": "Detected Table",
			"dimensions": [1200, 919],
			"numOfPages": 1,
			"docname": "file-1.png",
			"text": "(c) Hartmann - Gorczany Invoice\nHansen, Gottlleb and Johns\nAssimilated Impactful Intranet\n1621 Vevhu| Street, Honin Extension\nEkezodo, CT, JM\nzud.nl\n=-mall: Asa. Wunsch@gmall.com, Phone: 1-718-685-6225\nBill to Address 'Ship to Address\n1231 Zeol Point, Voeke Heights 414 Figeb Road, Gegjat Road\nHoinme, WI, CF Tejawif, WI, AO\nfefruugiar ogesetoj.uy\nPhone: 065-498-1594 x3103, E-mall: E-mall: Doyle64@yahoo.com,\nAlison.Grady30@gmail.com Phone: 999-731-2964 x8653\nInvoice No #4840206\ncalculating optimizing vertical,\ncomposite.\nSignature\nDue Datesi14:2094 vat: 16.36%\nDisc.: 1588.1\nPay Total: Ftt715.26"
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




