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
  "invoice.png": {
    tables: [
      {
        summary: [
          [" Item", " description", " By", " For", " Cost", " Qty", " Grand Total"],
          ["47", "Practical Phstic Hat, Handcrafted Wooden Keyboard ", "Clothing", "Ball ", "240.69", "7", "563.46"],
          ["609", "Fantastic Granite Salad, Awesome Metal Pizza ", "Incredib Soft CtBese ", " Rustic Wooden  Keyboard ", "98817", "4", "57021"],
          ["907", "Tasty Fresh Pants  Refined Pla\\u00fc Bke ", "Car ", "Indtstriel ", "5715", "11", "492.79"],
          ["699", "Prantinal Rt\\u00b1ber St\\u00fct, I-Jr\\u00e5rarxied Cotton fish ", "Electrorics ", "Outdoors ", "44.42", "18", "48064"],
          ["441", "Tasty &arite Cticken, Incredible Metal Chair ", "Shek Wooden Shoes ", "Cticken ", "98883", "11", "92857"],
          ["268", "Awesome Rubber Shit Gorgeous Corcrete Mouse ", "Bike ", "Kids ", "774568", "", "24483"],
          ["541", "Tasty Steel Gbves, Handmade  PhsticSboes ", "Books ", "Computers ", "685.71", "20", "25119"],
          ["799", "Practical Phstic Gloves, Tasty  Frozen ", "Sitt ", "Shoes ", "66627", "18", "43092"],
          ["401", "Fantastic Wooden Ball. Refirbd  Grafte Ct#s ", "Kids ", "Sausages ", "49666", "19", "26.03"],
          ["321", "Generic Frozen Fish. Skek Soft  Shoes ", "Cheese ", "RefitBd Concrete Keyboard ", "209.79", "10", "91.76"]
        ],
        metadata: {
          bbox: [ 133, 608, 626, 1005 ],
          score: 0.98,
          page: 0
        },
        cells: [
          {
            bbox: [ 133, 608, 162, 645 ],
            score: 0.98,
            cell_position: [ 0, 0 ],
            text: " Item"
          },
          {
            bbox: [ 162, 608, 334, 645 ],
            score: 0.98,
            cell_position: [ 0, 1 ],
            text: " description"
          },
          {
            bbox: [ 334, 608, 417, 645 ],
            score: 0.98,
            cell_position: [ 0, 2 ],
            text: " By"
          },
          {
            bbox: [ 417, 608, 514, 645 ],
            score: 0.98,
            cell_position: [ 0, 3 ],
            text: " For"
          },
          {
            bbox: [ 514, 608, 557, 645 ],
            score: 0.98,
            cell_position: [ 0, 4 ],
            text: " Cost"
          },
          {
            bbox: [ 557, 608, 582, 645 ],
            score: 0.98,
            cell_position: [ 0, 5 ],
            text: " Qty"
          },
          {
            bbox: [ 582, 608, 626, 645 ],
            score: 0.98,
            cell_position: [ 0, 6 ],
            text: " Grand Total"
          },
          {
            bbox: [ 133, 645, 162, 680 ],
            score: 0.98,
            cell_position: [ 1, 0 ],
            text: "47"
          },
          {
            bbox: [ 162, 645, 334, 680 ],
            score: 0.98,
            cell_position: [ 1, 1 ],
            text: "Practical Phstic Hat, Handcrafted Wooden Keyboard "
          },
          {
            bbox: [ 334, 645, 417, 680 ],
            score: 0.98,
            cell_position: [ 1, 2 ],
            text: "Clothing"
          },
          {
            bbox: [ 417, 645, 514, 680 ],
            score: 0.98,
            cell_position: [ 1, 3 ],
            text: "Ball "
          },
          {
            bbox: [ 514, 645, 557, 680 ],
            score: 0.98,
            cell_position: [ 1, 4 ],
            text: "240.69"
          },
          {
            bbox: [ 557, 645, 582, 680 ],
            score: 0.98,
            cell_position: [ 1, 5 ],
            text: "7"
          },
          {
            bbox: [ 582, 645, 626, 680 ],
            score: 0.98,
            cell_position: [ 1, 6 ],
            text: "563.46"
          },
          {
            bbox: [ 133, 680, 162, 718 ],
            score: 0.98,
            cell_position: [ 2, 0 ],
            text: "609"
          },
          {
            bbox: [ 162, 680, 334, 718 ],
            score: 0.98,
            cell_position: [ 2, 1 ],
            text: "Fantastic Granite Salad, Awesome Metal Pizza "
          },
          {
            bbox: [ 334, 680, 417, 718 ],
            score: 0.98,
            cell_position: [ 2, 2 ],
            text: "Incredib Soft CtBese "
          },
          {
            bbox: [ 417, 680, 514, 718 ],
            score: 0.98,
            cell_position: [ 2, 3 ],
            text: " Rustic Wooden  Keyboard "
          },
          {
            bbox: [ 514, 680, 557, 718 ],
            score: 0.98,
            cell_position: [ 2, 4 ],
            text: "98817"
          },
          {
            bbox: [ 557, 680, 582, 718 ],
            score: 0.98,
            cell_position: [ 2, 5 ],
            text: "4"
          },
          {
            bbox: [ 582, 680, 626, 718 ],
            score: 0.98,
            cell_position: [ 2, 6 ],
            text: "57021"
          },
          {
            bbox: [ 133, 718, 162, 753 ],
            score: 0.98,
            cell_position: [ 3, 0 ],
            text: "907"
          },
          {
            bbox: [ 162, 718, 334, 753 ],
            score: 0.98,
            cell_position: [ 3, 1 ],
            text: "Tasty Fresh Pants  Refined Pla\\u00fc Bke "
          },
          {
            bbox: [ 334, 718, 417, 753 ],
            score: 0.98,
            cell_position: [ 3, 2 ],
            text: "Car "
          },
          {
            bbox: [ 417, 718, 514, 753 ],
            score: 0.98,
            cell_position: [ 3, 3 ],
            text: "Indtstriel "
          },
          {
            bbox: [ 514, 718, 557, 753 ],
            score: 0.98,
            cell_position: [ 3, 4 ],
            text: "5715"
          },
          {
            bbox: [ 557, 718, 582, 753 ],
            score: 0.98,
            cell_position: [ 3, 5 ],
            text: "11"
          },
          {
            bbox: [ 582, 718, 626, 753 ],
            score: 0.98,
            cell_position: [ 3, 6 ],
            text: "492.79"
          },
          {
            bbox: [ 133, 753, 162, 789 ],
            score: 0.98,
            cell_position: [ 4, 0 ],
            text: "699"
          },
          {
            bbox: [ 162, 753, 334, 789 ],
            score: 0.98,
            cell_position: [ 4, 1 ],
            text: "Prantinal Rt\\u00b1ber St\\u00fct, I-Jr\\u00e5rarxied Cotton fish "
          },
          {
            bbox: [ 334, 753, 417, 789 ],
            score: 0.98,
            cell_position: [ 4, 2 ],
            text: "Electrorics "
          },
          {
            bbox: [ 417, 753, 514, 789 ],
            score: 0.98,
            cell_position: [ 4, 3 ],
            text: "Outdoors "
          },
          {
            bbox: [ 514, 753, 557, 789 ],
            score: 0.98,
            cell_position: [ 4, 4 ],
            text: "44.42"
          },
          {
            bbox: [ 557, 753, 582, 789 ],
            score: 0.98,
            cell_position: [ 4, 5 ],
            text: "18"
          },
          {
            bbox: [ 582, 753, 626, 789 ],
            score: 0.98,
            cell_position: [ 4, 6 ],
            text: "48064"
          },
          {
            bbox: [ 133, 789, 162, 825 ],
            score: 0.98,
            cell_position: [ 5, 0 ],
            text: "441"
          },
          {
            bbox: [ 162, 789, 334, 825 ],
            score: 0.98,
            cell_position: [ 5, 1 ],
            text: "Tasty &arite Cticken, Incredible Metal Chair "
          },
          {
            bbox: [ 334, 789, 417, 825 ],
            score: 0.98,
            cell_position: [ 5, 2 ],
            text: "Shek Wooden Shoes "
          },
          {
            bbox: [ 417, 789, 514, 825 ],
            score: 0.98,
            cell_position: [ 5, 3 ],
            text: "Cticken "
          },
          {
            bbox: [ 514, 789, 557, 825 ],
            score: 0.98,
            cell_position: [ 5, 4 ],
            text: "98883"
          },
          {
            bbox: [ 557, 789, 582, 825 ],
            score: 0.98,
            cell_position: [ 5, 5 ],
            text: "11"
          },
          {
            bbox: [ 582, 789, 626, 825 ],
            score: 0.98,
            cell_position: [ 5, 6 ],
            text: "92857"
          },
          {
            bbox: [ 133, 825, 162, 861 ],
            score: 0.98,
            cell_position: [ 6, 0 ],
            text: "268"
          },
          {
            bbox: [ 162, 825, 334, 861 ],
            score: 0.98,
            cell_position: [ 6, 1 ],
            text: "Awesome Rubber Shit Gorgeous Corcrete Mouse "
          },
          {
            bbox: [ 334, 825, 417, 861 ],
            score: 0.98,
            cell_position: [ 6, 2 ],
            text: "Bike "
          },
          {
            bbox: [ 417, 825, 514, 861 ],
            score: 0.98,
            cell_position: [ 6, 3 ],
            text: "Kids "
          },
          {
            bbox: [ 514, 825, 557, 861 ],
            score: 0.98,
            cell_position: [ 6, 4 ],
            text: "774568"
          },
          {
            bbox: [ 557, 825, 582, 861 ],
            score: 0.98,
            cell_position: [ 6, 5 ],
            text: ""
          },
          {
            bbox: [ 582, 825, 626, 861 ],
            score: 0.98,
            cell_position: [ 6, 6 ],
            text: "24483"
          },
          {
            bbox: [ 133, 861, 162, 897 ],
            score: 0.98,
            cell_position: [ 7, 0 ],
            text: "541"
          },
          {
            bbox: [ 162, 861, 334, 897 ],
            score: 0.98,
            cell_position: [ 7, 1 ],
            text: "Tasty Steel Gbves, Handmade  PhsticSboes "
          },
          {
            bbox: [ 334, 861, 417, 897 ],
            score: 0.98,
            cell_position: [ 7, 2 ],
            text: "Books "
          },
          {
            bbox: [ 417, 861, 514, 897 ],
            score: 0.98,
            cell_position: [ 7, 3 ],
            text: "Computers "
          },
          {
            bbox: [ 514, 861, 557, 897 ],
            score: 0.98,
            cell_position: [ 7, 4 ],
            text: "685.71"
          },
          {
            bbox: [ 557, 861, 582, 897 ],
            score: 0.98,
            cell_position: [ 7, 5 ],
            text: "20"
          },
          {
            bbox: [ 582, 861, 626, 897 ],
            score: 0.98,
            cell_position: [ 7, 6 ],
            text: "25119"
          },
          {
            bbox: [ 133, 897, 162, 933 ],
            score: 0.98,
            cell_position: [ 8, 0 ],
            text: "799"
          },
          {
            bbox: [ 162, 897, 334, 933 ],
            score: 0.98,
            cell_position: [ 8, 1 ],
            text: "Practical Phstic Gloves, Tasty  Frozen "
          },
          {
            bbox: [ 334, 897, 417, 933 ],
            score: 0.98,
            cell_position: [ 8, 2 ],
            text: "Sitt "
          },
          {
            bbox: [ 417, 897, 514, 933 ],
            score: 0.98,
            cell_position: [ 8, 3 ],
            text: "Shoes "
          },
          {
            bbox: [ 514, 897, 557, 933 ],
            score: 0.98,
            cell_position: [ 8, 4 ],
            text: "66627"
          },
          {
            bbox: [ 557, 897, 582, 933 ],
            score: 0.98,
            cell_position: [ 8, 5 ],
            text: "18"
          },
          {
            bbox: [ 582, 897, 626, 933 ],
            score: 0.98,
            cell_position: [ 8, 6 ],
            text: "43092"
          },
          {
            bbox: [ 133, 933, 162, 970 ],
            score: 0.98,
            cell_position: [ 9, 0 ],
            text: "401"
          },
          {
            bbox: [ 162, 933, 334, 970 ],
            score: 0.98,
            cell_position: [ 9, 1 ],
            text: "Fantastic Wooden Ball. Refirbd  Grafte Ct#s "
          },
          {
            bbox: [ 334, 933, 417, 970 ],
            score: 0.98,
            cell_position: [ 9, 2 ],
            text: "Kids "
          },
          {
            bbox: [ 417, 933, 514, 970 ],
            score: 0.98,
            cell_position: [ 9, 3 ],
            text: "Sausages "
          },
          {
            bbox: [ 514, 933, 557, 970 ],
            score: 0.98,
            cell_position: [ 9, 4 ],
            text: "49666"
          },
          {
            bbox: [ 557, 933, 582, 970 ],
            score: 0.98,
            cell_position: [ 9, 5 ],
            text: "19"
          },
          {
            bbox: [ 582, 933, 626, 970 ],
            score: 0.98,
            cell_position: [ 9, 6 ],
            text: "26.03"
          },
          {
            bbox: [ 133, 970, 162, 1005 ],
            score: 0.98,
            cell_position: [ 10, 0 ],
            text: "321"
          },
          {
            bbox: [ 162, 970, 334, 1005 ],
            score: 0.98,
            cell_position: [ 10, 1 ],
            text: "Generic Frozen Fish. Skek Soft  Shoes "
          },
          {
            bbox: [ 334, 970, 417, 1005 ],
            score: 0.98,
            cell_position: [ 10, 2 ],
            text: "Cheese "
          },
          {
            bbox: [ 417, 970, 514, 1005 ],
            score: 0.98,
            cell_position: [ 10, 3 ],
            text: "RefitBd Concrete Keyboard "
          },
          {
            bbox: [ 514, 970, 557, 1005 ],
            score: 0.98,
            cell_position: [ 10, 4 ],
            text: "209.79"
          },
          {
            bbox: [ 557, 970, 582, 1005 ],
            score: 0.98,
            cell_position: [ 10, 5 ],
            text: "10"
          },
          {
            bbox: [ 582, 970, 626, 1005 ],
            score: 0.98,
            cell_position: [ 10, 6 ],
            text: "91.76"
          }
        ]
      }
    ],
    billing_address: [
      {
        text: "Bill to A\"oss\nMathis\nAddress : 241 Zekim\nPi-ore",
        page: 0
      }
    ],
    origin_address: [
      {
        text: "nv\\u00fce from\nyone Corp\nebsite : pogulecu.com\n033 Gohasi Place. Ofiam Averu. SM\nj@coideby",
        page: 0
      }
    ],
    delivery_address: [
      {
        text: "Address : 1422 Sip to\nName : Jerome Roberson\nav@fus.sh\nJ (678)3914200",
        page: 0
      }
    ],
    tax: [ { text: null, page: 0 } ],
    detected_total: [ { text: "$1254.50", page: 0 } ],
    detected_subtotal: [ { text: null, page: 0 } ],
    discount: [ { text: "15%", page: 0 } ],
    due_date: [ { text: null, page: 0 } ],
    invoice_id: [ { text: "#AE3457", page: 0 } ],
    status: true,
    metadata: {
      info: "Detected Table",
      dimensions: [ 1200, 763, 3 ],
      num_of_pages: 1
    }
  }
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




