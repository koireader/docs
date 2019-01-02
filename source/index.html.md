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
	'billing_address': 'Alling Mdreeg\n399 Ikeroc Park, Piszo Park\nKaunicef, WA, PT\nmac.wc\nPhone: (539) 203-2291, E-mail:\nMelyna Bogicich6$@yahoo.com',
	'delivery_address': 'Ship to\n1902 Owedov Road, Kecbe Mill\nEfujeneb, DE, Cl\nelofo.om\nPhone: 213-569-7939, E-mail:\nSophia Herman@hotmail.com',
	'detected_total': ' $ 19467',
	'discount': ' 919.6',
	'due_date': None,
	'invoice_id': '#2100a359',
	'origin_address': 'Smitham - Raynor\nSund-alone acudng méeite\n214 Dipo Glen, Dohin Boulevard\nKocizni, 0K, SR\nPhone: 1-735-920961 x51054, E-mail:\nCarlos Hintz@gmail.com',
	'tables': [{
		'cells': [{
			'bbox': [86, 495, 119, 564],
			'cell_position': [0, 0],
			'score': 0.92,
			'text': ' Item'
		}, {
			'bbox': [86, 564, 119, 593],
			'cell_position': [0, 1],
			'score': 0.91,
			'text': ' Info'
		}, {
			'bbox': [86, 593, 119, 659],
			'cell_position': [0, 2],
			'score': 0.92,
			'text': ' From'
		}, {
			'bbox': [86, 659, 119, 707],
			'cell_position': [0, 3],
			'score': 0.91,
			'text': ' For'
		}, {
			'bbox': [86, 707, 119, 755],
			'cell_position': [0, 4],
			'score': 0.91,
			'text': ' Money'
		}, {
			'bbox': [86, 755, 119, 785],
			'cell_position': [0, 5],
			'score': 0.92,
			'text': ' No . of items'
		}, {
			'bbox': [119, 495, 439, 564],
			'cell_position': [0, 6],
			'score': 0.92,
			'text': ' Unit price'
		}, {
			'bbox': [119, 564, 439, 593],
			'cell_position': [0, 7],
			'score': 0.91,
			'text': ' Total cost'
		}, {
			'bbox': [119, 593, 439, 659],
			'cell_position': [1, 0],
			'score': 0.92,
			'text': '201'
		}, {
			'bbox': [119, 659, 439, 707],
			'cell_position': [1, 1],
			'score': 0.92,
			'text': 'Shoes '
		}, {
			'bbox': [119, 707, 439, 755],
			'cell_position': [1, 2],
			'score': 0.91,
			'text': 'Shoes '
		}, {
			'bbox': [119, 755, 439, 785],
			'cell_position': [1, 3],
			'score': 0.92,
			'text': 'Bike'
		}, {
			'bbox': [439, 495, 520, 564],
			'cell_position': [1, 4],
			'score': 0.92,
			'text': '576.41'
		}, {
			'bbox': [439, 564, 520, 593],
			'cell_position': [1, 5],
			'score': 0.91,
			'text': '1'
		}, {
			'bbox': [439, 593, 520, 659],
			'cell_position': [1, 6],
			'score': 0.91,
			'text': '23.29'
		}, {
			'bbox': [439, 659, 520, 707],
			'cell_position': [1, 7],
			'score': 0.92,
			'text': '169.11'
		}, {
			'bbox': [439, 707, 520, 755],
			'cell_position': [2, 0],
			'score': 0.91,
			'text': '293'
		}, {
			'bbox': [439, 755, 520, 785],
			'cell_position': [2, 1],
			'score': 0.92,
			'text': 'Car '
		}, {
			'bbox': [520, 495, 559, 564],
			'cell_position': [2, 2],
			'score': 0.91,
			'text': 'Small  Concrete  Gloves '
		}, {
			'bbox': [520, 564, 559, 593],
			'cell_position': [2, 3],
			'score': 0.91,
			'text': 'Bike'
		}, {
			'bbox': [520, 593, 559, 659],
			'cell_position': [2, 4],
			'score': 0.92,
			'text': '57.23'
		}, {
			'bbox': [520, 659, 559, 707],
			'cell_position': [2, 5],
			'score': 0.92,
			'text': '13'
		}, {
			'bbox': [520, 707, 559, 755],
			'cell_position': [2, 6],
			'score': 0.91,
			'text': '410.31'
		}, {
			'bbox': [520, 755, 559, 785],
			'cell_position': [2, 7],
			'score': 0.91,
			'text': '439.19'
		}, {
			'bbox': [559, 495, 605, 564],
			'cell_position': [3, 0],
			'score': 0.91,
			'text': '853'
		}, {
			'bbox': [559, 564, 605, 593],
			'cell_position': [3, 1],
			'score': 0.92,
			'text': 'Ruafi moabo ufufikoh kowcugih orrohar lew mohoklo  cedlehpu 10 nefvaf ve zozaal. '
		}, {
			'bbox': [559, 593, 605, 659],
			'cell_position': [3, 2],
			'score': 0.92,
			'text': 'Bike '
		}, {
			'bbox': [559, 659, 605, 707],
			'cell_position': [3, 3],
			'score': 0.92,
			'text': 'Car '
		}, {
			'bbox': [559, 707, 605, 755],
			'cell_position': [3, 4],
			'score': 0.91,
			'text': '516.37'
		}, {
			'bbox': [559, 755, 605, 785],
			'cell_position': [3, 5],
			'score': 0.92,
			'text': '13'
		}, {
			'bbox': [605, 495, 649, 564],
			'cell_position': [3, 6],
			'score': 0.91,
			'text': '550.62'
		}, {
			'bbox': [605, 564, 649, 593],
			'cell_position': [3, 7],
			'score': 0.92,
			'text': '465.35'
		}, {
			'bbox': [605, 593, 649, 659],
			'cell_position': [4, 0],
			'score': 0.91,
			'text': '223'
		}, {
			'bbox': [605, 659, 649, 707],
			'cell_position': [4, 1],
			'score': 0.92,
			'text': 'Gag,velvi hobfu haw let cahzid co wopew tafupwur pooj  edavpi gi girjottug dija nitfano numvavuha. '
		}, {
			'bbox': [605, 707, 649, 755],
			'cell_position': [4, 2],
			'score': 0.92,
			'text': 'Small Cotton Fish '
		}, {
			'bbox': [605, 755, 649, 785],
			'cell_position': [4, 3],
			'score': 0.92,
			'text': 'Chair'
		}, {
			'bbox': [649, 495, 691, 564],
			'cell_position': [4, 4],
			'score': 0.92,
			'text': '860.04'
		}, {
			'bbox': [649, 564, 691, 593],
			'cell_position': [4, 5],
			'score': 0.91,
			'text': '11'
		}, {
			'bbox': [649, 593, 691, 659],
			'cell_position': [4, 6],
			'score': 0.92,
			'text': '249.93'
		}, {
			'bbox': [649, 659, 691, 707],
			'cell_position': [4, 7],
			'score': 0.92,
			'text': '299.03'
		}, {
			'bbox': [649, 707, 691, 755],
			'cell_position': [5, 0],
			'score': 0.91,
			'text': '125'
		}, {
			'bbox': [649, 755, 691, 785],
			'cell_position': [5, 1],
			'score': 0.92,
			'text': 'Gloves '
		}, {
			'bbox': [691, 495, 733, 564],
			'cell_position': [5, 2],
			'score': 0.91,
			'text': 'Garden '
		}, {
			'bbox': [691, 564, 733, 593],
			'cell_position': [5, 3],
			'score': 0.92,
			'text': 'Fish'
		}, {
			'bbox': [691, 593, 733, 659],
			'cell_position': [5, 4],
			'score': 0.92,
			'text': ''
		}, {
			'bbox': [691, 659, 733, 707],
			'cell_position': [5, 5],
			'score': 0.91,
			'text': '17'
		}, {
			'bbox': [691, 707, 733, 755],
			'cell_position': [5, 6],
			'score': 0.92,
			'text': '676.33'
		}, {
			'bbox': [691, 755, 733, 785],
			'cell_position': [5, 7],
			'score': 0.91,
			'text': '836.77'
		}],
		'metadata': {
			'bbox': [86, 493, 733, 785],
			'page': 0,
			'score': 0.98
		},
		'summary': [
			[' Item', ' Info', ' From', ' For', ' Money', ' No . of items', ' Unit price', ' Total cost'],
			['201', 'Shoes ', 'Shoes ', 'Bike', '576.41', '1', '23.29', '169.11'],
			['293', 'Car ', 'Small  Concrete  Gloves ', 'Bike', '57.23', '13', '410.31', '439.19'],
			['853', 'Ruafi moabo ufufikoh kowcugih orrohar lew mohoklo  cedlehpu 10 nefvaf ve zozaal. ', 'Bike ', 'Car ', '516.37', '13', '550.62', '465.35'],
			['223', 'Gag,velvi hobfu haw let cahzid co wopew tafupwur pooj  edavpi gi girjottug dija nitfano numvavuha. ', 'Small Cotton Fish ', 'Chair', '860.04', '11', '249.93', '299.03'],
			['125', 'Gloves ', 'Garden ', 'Fish', '', '17', '676.33', '836.77']
		]
	}],
	'tax': ''
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

