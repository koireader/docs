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
	'billing_address': 'Bill to A oss\nMathis\nAddress : 241 Zekim\nPi-ore',
	'delivery_address': None,
	'detected_total': '',
	'discount': '',
	'due_date': None,
	'invoice_id': '',
	'origin_address': 'nvüe from\nyone Corp\nebsite : pogulecu.com\n033 Gohasi Place. Ofiam Averu. SM\nj@coideby',
	'table': {
		'bbox': [133, 613, 626, 1005],
		'score': 0.98
	},
	'table_cells': [{
		'bbox': [133, 607, 162, 644],
		'cell_position': [0, 0],
		'score': 0.9016333447638814,
		'text': 'Item '
	}, {
		'bbox': [133, 644, 162, 679],
		'cell_position': [0, 1],
		'score': 0.9014802991361961,
		'text': ' Descrt)tion '
	}, {
		'bbox': [133, 679, 162, 717],
		'cell_position': [0, 2],
		'score': 0.9033820447416433,
		'text': ' By '
	}, {
		'bbox': [133, 717, 162, 753],
		'cell_position': [0, 3],
		'score': 0.9087951191402877,
		'text': ' For '
	}, {
		'bbox': [133, 753, 162, 788],
		'cell_position': [0, 4],
		'score': 0.9032689335279892,
		'text': 'Cost '
	}, {
		'bbox': [133, 788, 162, 825],
		'cell_position': [0, 5],
		'score': 0.9045185896904288,
		'text': 'Qty '
	}, {
		'bbox': [133, 825, 162, 861],
		'cell_position': [0, 6],
		'score': 0.903257023595601,
		'text': 'Grand Total'
	}, {
		'bbox': [133, 861, 162, 897],
		'cell_position': [1, 0],
		'score': 0.9052301832231363,
		'text': '487'
	}, {
		'bbox': [133, 897, 162, 932],
		'cell_position': [1, 1],
		'score': 0.9033436277589102,
		'text': 'Practical Phstic Hat, Handcrafted Wooden Keyboard '
	}, {
		'bbox': [133, 932, 162, 968],
		'cell_position': [1, 2],
		'score': 0.9017499888419732,
		'text': 'Clothing'
	}, {
		'bbox': [133, 968, 162, 1005],
		'cell_position': [1, 3],
		'score': 0.9015291907898787,
		'text': 'Ball '
	}, {
		'bbox': [162, 607, 332, 644],
		'cell_position': [1, 4],
		'score': 0.9031414688478592,
		'text': '240.69'
	}, {
		'bbox': [162, 644, 332, 679],
		'cell_position': [1, 5],
		'score': 0.9020637305748863,
		'text': '7'
	}, {
		'bbox': [162, 679, 332, 717],
		'cell_position': [1, 6],
		'score': 0.9021476499095469,
		'text': '563.46'
	}, {
		'bbox': [162, 717, 332, 753],
		'cell_position': [2, 0],
		'score': 0.9080973718317236,
		'text': '609'
	}, {
		'bbox': [162, 753, 332, 788],
		'cell_position': [2, 1],
		'score': 0.9040677284582916,
		'text': 'Fantastic Granite Salad, Awesome Metal Pizza '
	}, {
		'bbox': [162, 788, 332, 825],
		'cell_position': [2, 2],
		'score': 0.909732131169216,
		'text': 'Incredib Soft CtBese '
	}, {
		'bbox': [162, 825, 332, 861],
		'cell_position': [2, 3],
		'score': 0.9061200868877263,
		'text': ' Rustic Wooden  Keyboard '
	}, {
		'bbox': [162, 861, 332, 897],
		'cell_position': [2, 4],
		'score': 0.9020907990696718,
		'text': '98817'
	}, {
		'bbox': [162, 897, 332, 932],
		'cell_position': [2, 5],
		'score': 0.9067260584128559,
		'text': '4'
	}, {
		'bbox': [162, 932, 332, 968],
		'cell_position': [2, 6],
		'score': 0.9042947742660494,
		'text': '57021'
	}, {
		'bbox': [162, 968, 332, 1005],
		'cell_position': [3, 0],
		'score': 0.9099320316074148,
		'text': '907'
	}, {
		'bbox': [332, 607, 415, 644],
		'cell_position': [3, 1],
		'score': 0.9060101549847918,
		'text': 'Tasty Fresh Pants Refined Plaü Bke '
	}, {
		'bbox': [332, 644, 415, 679],
		'cell_position': [3, 2],
		'score': 0.9022033794733543,
		'text': 'Car '
	}, {
		'bbox': [332, 679, 415, 717],
		'cell_position': [3, 3],
		'score': 0.9074161511179316,
		'text': 'Indtstriel '
	}, {
		'bbox': [332, 717, 415, 753],
		'cell_position': [3, 4],
		'score': 0.9013495924913214,
		'text': '5715'
	}, {
		'bbox': [332, 753, 415, 788],
		'cell_position': [3, 5],
		'score': 0.9027088728741736,
		'text': '11'
	}, {
		'bbox': [332, 788, 415, 825],
		'cell_position': [3, 6],
		'score': 0.907360011325008,
		'text': '492.79'
	}, {
		'bbox': [332, 825, 415, 861],
		'cell_position': [4, 0],
		'score': 0.9026163954757003,
		'text': '699'
	}, {
		'bbox': [332, 861, 415, 897],
		'cell_position': [4, 1],
		'score': 0.9096354960908608,
		'text': 'Prantinal Rt±ber Stüt, I-Jrårarxied Cotton fish '
	}, {
		'bbox': [332, 897, 415, 932],
		'cell_position': [4, 2],
		'score': 0.9021407232632179,
		'text': 'Electrorics '
	}, {
		'bbox': [332, 932, 415, 968],
		'cell_position': [4, 3],
		'score': 0.9016806704159959,
		'text': 'Outdoors '
	}, {
		'bbox': [332, 968, 415, 1005],
		'cell_position': [4, 4],
		'score': 0.9091387741888399,
		'text': '44.42'
	}, {
		'bbox': [415, 607, 513, 644],
		'cell_position': [4, 5],
		'score': 0.9057133406825375,
		'text': '18'
	}, {
		'bbox': [415, 644, 513, 679],
		'cell_position': [4, 6],
		'score': 0.903116282798108,
		'text': '48064'
	}, {
		'bbox': [415, 679, 513, 717],
		'cell_position': [5, 0],
		'score': 0.9037619708067474,
		'text': '441'
	}, {
		'bbox': [415, 717, 513, 753],
		'cell_position': [5, 1],
		'score': 0.9055211158147589,
		'text': 'Tasty &arite Cticken, Incredible Metal Chair '
	}, {
		'bbox': [415, 753, 513, 788],
		'cell_position': [5, 2],
		'score': 0.9041984136043236,
		'text': 'Shek Wooden Shoes '
	}, {
		'bbox': [415, 788, 513, 825],
		'cell_position': [5, 3],
		'score': 0.90333956147091,
		'text': 'Cticken '
	}, {
		'bbox': [415, 825, 513, 861],
		'cell_position': [5, 4],
		'score': 0.9075689687879865,
		'text': '98883'
	}, {
		'bbox': [415, 861, 513, 897],
		'cell_position': [5, 5],
		'score': 0.904044655869242,
		'text': '11'
	}, {
		'bbox': [415, 897, 513, 932],
		'cell_position': [5, 6],
		'score': 0.9026780621432977,
		'text': '92857'
	}, {
		'bbox': [415, 932, 513, 968],
		'cell_position': [6, 0],
		'score': 0.9013227237230417,
		'text': '268'
	}, {
		'bbox': [415, 968, 513, 1005],
		'cell_position': [6, 1],
		'score': 0.9073014293886017,
		'text': 'Awesome Rubber Shit Gorgeous Corcrete Mouse '
	}, {
		'bbox': [513, 607, 555, 644],
		'cell_position': [6, 2],
		'score': 0.9013420035427901,
		'text': 'Bike '
	}, {
		'bbox': [513, 644, 555, 679],
		'cell_position': [6, 3],
		'score': 0.9019610861927053,
		'text': 'Kids '
	}, {
		'bbox': [513, 679, 555, 717],
		'cell_position': [6, 4],
		'score': 0.904483708346285,
		'text': '774568'
	}, {
		'bbox': [513, 717, 555, 753],
		'cell_position': [6, 5],
		'score': 0.907986667865889,
		'text': ''
	}, {
		'bbox': [513, 753, 555, 788],
		'cell_position': [6, 6],
		'score': 0.9055977292481531,
		'text': '24483'
	}, {
		'bbox': [513, 788, 555, 825],
		'cell_position': [7, 0],
		'score': 0.9035588274164639,
		'text': '541'
	}, {
		'bbox': [513, 825, 555, 861],
		'cell_position': [7, 1],
		'score': 0.9077998987899181,
		'text': 'Tasty Steel Gbves, Handmade  PhsticSboes '
	}, {
		'bbox': [513, 861, 555, 897],
		'cell_position': [7, 2],
		'score': 0.9030879652428568,
		'text': 'Books '
	}, {
		'bbox': [513, 897, 555, 932],
		'cell_position': [7, 3],
		'score': 0.9034771919330983,
		'text': 'Computers '
	}, {
		'bbox': [513, 932, 555, 968],
		'cell_position': [7, 4],
		'score': 0.9023415807846799,
		'text': '685.71'
	}, {
		'bbox': [513, 968, 555, 1005],
		'cell_position': [7, 5],
		'score': 0.901057183688312,
		'text': '20'
	}, {
		'bbox': [555, 607, 580, 644],
		'cell_position': [7, 6],
		'score': 0.9033743313290797,
		'text': '25119'
	}, {
		'bbox': [555, 644, 580, 679],
		'cell_position': [8, 0],
		'score': 0.9050455830126205,
		'text': '799'
	}, {
		'bbox': [555, 679, 580, 717],
		'cell_position': [8, 1],
		'score': 0.9019558557885914,
		'text': 'Practical Phstic Gloves, Tasty  Frozen '
	}, {
		'bbox': [555, 717, 580, 753],
		'cell_position': [8, 2],
		'score': 0.9051022575849903,
		'text': 'Sitt '
	}, {
		'bbox': [555, 753, 580, 788],
		'cell_position': [8, 3],
		'score': 0.9036459312908528,
		'text': 'Shoes '
	}, {
		'bbox': [555, 788, 580, 825],
		'cell_position': [8, 4],
		'score': 0.9096108186229148,
		'text': '66627'
	}, {
		'bbox': [555, 825, 580, 861],
		'cell_position': [8, 5],
		'score': 0.9029651789675168,
		'text': '18'
	}, {
		'bbox': [555, 861, 580, 897],
		'cell_position': [8, 6],
		'score': 0.9046370948562583,
		'text': '43092'
	}, {
		'bbox': [555, 897, 580, 932],
		'cell_position': [9, 0],
		'score': 0.9074656735241808,
		'text': '401'
	}, {
		'bbox': [555, 932, 580, 968],
		'cell_position': [9, 1],
		'score': 0.9019837912900545,
		'text': 'Fantastic Wooden Ball. Refirbd  Grafte Ct#s '
	}, {
		'bbox': [555, 968, 580, 1005],
		'cell_position': [9, 2],
		'score': 0.9092869832063457,
		'text': 'Kids '
	}, {
		'bbox': [580, 607, 626, 644],
		'cell_position': [9, 3],
		'score': 0.9058211871666494,
		'text': 'Sausages '
	}, {
		'bbox': [580, 644, 626, 679],
		'cell_position': [9, 4],
		'score': 0.9080215087042515,
		'text': '49666'
	}, {
		'bbox': [580, 679, 626, 717],
		'cell_position': [9, 5],
		'score': 0.9038703728192272,
		'text': '19'
	}, {
		'bbox': [580, 717, 626, 753],
		'cell_position': [9, 6],
		'score': 0.9020357868589233,
		'text': '26.03'
	}, {
		'bbox': [580, 753, 626, 788],
		'cell_position': [10, 0],
		'score': 0.9080484944035109,
		'text': '321'
	}, {
		'bbox': [580, 788, 626, 825],
		'cell_position': [10, 1],
		'score': 0.9084564573910465,
		'text': 'Generic Frozen Fish. Skek Soft Shoes '
	}, {
		'bbox': [580, 825, 626, 861],
		'cell_position': [10, 2],
		'score': 0.9050550884088834,
		'text': 'Cheese '
	}, {
		'bbox': [580, 861, 626, 897],
		'cell_position': [10, 3],
		'score': 0.9081235068790537,
		'text': 'RefitBd Concrete Keyboard '
	}, {
		'bbox': [580, 897, 626, 932],
		'cell_position': [10, 4],
		'score': 0.9057418908551711,
		'text': '209.79'
	}, {
		'bbox': [580, 932, 626, 968],
		'cell_position': [10, 5],
		'score': 0.904858757966236,
		'text': '10'
	}, {
		'bbox': [580, 968, 626, 1005],
		'cell_position': [10, 6],
		'score': 0.9066883303217321,
		'text': '91.76'
	}],
	'table_summary': [
		['Item ', ' Descrt)tion ', ' By ', ' For ', 'Cost ', 'Qty ', 'Grand Total'],
		['487', 'Practical Phstic Hat, Handcrafted Wooden Keyboard ', 'Clothing', 'Ball ', '240.69', '7', '563.46'],
		['609', 'Fantastic Granite Salad, Awesome Metal Pizza ', 'Incredib Soft CtBese ', ' Rustic Wooden  Keyboard ', '98817', '4', '57021'],
		['907', 'Tasty Fresh Pants Refined Plaü Bke ', 'Car ', 'Indtstriel ', '5715', '11', '492.79'],
		['699', 'Prantinal Rt±ber Stüt, I-Jrårarxied Cotton fish ', 'Electrorics ', 'Outdoors ', '44.42', '18', '48064'],
		['441', 'Tasty &arite Cticken, Incredible Metal Chair ', 'Shek Wooden Shoes ', 'Cticken ', '98883', '11', '92857'],
		['268', 'Awesome Rubber Shit Gorgeous Corcrete Mouse ', 'Bike ', 'Kids ', '774568', '', '24483'],
		['541', 'Tasty Steel Gbves, Handmade  PhsticSboes ', 'Books ', 'Computers ', '685.71', '20', '25119'],
		['799', 'Practical Phstic Gloves, Tasty  Frozen ', 'Sitt ', 'Shoes ', '66627', '18', '43092'],
		['401', 'Fantastic Wooden Ball. Refirbd  Grafte Ct#s ', 'Kids ', 'Sausages ', '49666', '19', '26.03'],
		['321', 'Generic Frozen Fish. Skek Soft Shoes ', 'Cheese ', 'RefitBd Concrete Keyboard ', '209.79', '10', '91.76']
	],
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

