---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
#   - shell : Shell
#   - javascript : Node.js
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

> To upload, use this code:

<!-- ```shell
# With shell, you can just pass the correct header with each request

  curl -X POST   https://api.koireader.com/v1/analyze  
    -H 'content-type: multipart/form-data' 
    -H 'X-ApiKey: APIKEY' -F 'file=@/home/user/invoice.png'
``` -->

 
```python
import requests
headers = { 
    "X-ApiKey": 'APIKEY'
}
response = requests.post('https://api.koireader.com/v1/order/digitize', files={'file': open('./invoice.png', 'rb')}, headers=headers)
print(response.json())
```
> Make sure to enter a valid image path and replace <code>APIKEY</code> with your API key .

> The above command returns JSON structured like this:

```json
{
    "_id": "ck2q6j8mg00030rbccpzblctv",
    "status": true,
    "statusMessage": "Document Uploaded"
}
```
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
    console.log(body);
});
```  -->
<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
``` -->




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

> To receive response, use this code:

```python
import requests
headers = { 
    "X-ApiKey": 'APIKEY'
}
response = requests.get('https://api.koireader.com/v1/order/digitize?id=UNIQUE_ID', headers=headers)
print(response.json())
```
> Make sure to replace the <code>UNIQUE_ID</code> with the the value of <code>_id</code> which you have received from the upload API call 

> The above command returns JSON structured like this:

```json
{
    "data": [
        {
            "arbitraryFields": [
                {
                    "address_1": "KCS USA, DDC 11100 Valley Blvd #016 ,El Monte, CA 91731, United States Fax: DELIVERY ORDER",
                }
            ],
            "bolID": [
                {
                    "page": 0,
                    "text": " ACHSHEE99944316"
                }
            ],
            "carrier": [
                {
                    "page": 0,
                    "text": "KARTMAN"
                }
            ],
            "city": [
                {
                    "page": 0,
                    "text": "IA 50595 CLARK"
                }
            ],
            "containerDescription": [
                {
                    "page": 0,
                    "text": ""
                }
            ],
            "containerID": [
                {
                    "page": 0,
                    "text": "CAAR3230407\n CMMN9500970\n ECES0040844\n ECES1759046\n ECES1883627\n TKLU9999014"
                }
            ],
            "containerSizeType": [
                {
                    "page": 0,
                    "text": "20 Ft\n 20 Ft\n 20 Ft\n 20 Ft\n 20 Ft\n 20 Ft"
                }
            ],
            "containerVolume": [
                {
                    "page": 0,
                    "text": "5"
                }
            ],
            "containerWeight": [
                {
                    "page": 0,
                    "text": "Total Volume 5,297.20.0 CBF\n +\n PCS: 108Bag\n GLYPHOSATE 95% TECH IN CASE OF SPILL,\n LEAK, EXPOSURE OR ACCIDENT, CALL\n INFOTRAC 24-HR. ER NUMBER 888-323-2200"
                }
            ],
            "date": [
                {
                    "page": 0,
                    "text": "2018-5-8"
                }
            ],
            "deliveryAddress": [
                {
                    "addressDetails": {
                        "city": "Webster City",
                        "country": "USA",
                        "name": "LOG DIEST SUPPLY CO/DAS SWITZ ",
                        "state": "IA",
                        "streetName": "1404 EAST 325TH ST",
                        "zipCode": "50595"
                    },
                    "page": 0,
                    "text": "LOG DIEST SUPPLY CO/DAS SWITZ\n 1404 EAST 325TH ST\n WEBSTER CITY IA 50595\n Tel: 113-332-7697 CLARK Fax:\n -"
                }
            ],
            "detectedDocType": [
                {
                    "page": 0,
                    "text": "Import Order"
                }
            ],
            "faxNum": [
                {
                    "page": 0,
                    "text": ""
                }
            ],
            "freightTerms": [
                {
                    "page": 0,
                    "text": ""
                }
            ],
            "houseBolID": [
                {
                    "page": 0,
                    "text": "ACHSHEE9994431"
                }
            ],
            "lastFreeDate": [
                {
                    "page": 0,
                    "text": ""
                }
            ],
            "load": [
                {
                    "page": 0,
                    "text": ""
                }
            ],
            "location": [
                {
                    "page": 0,
                    "text": ""
                }
            ],
            "masterBolID": [
                {
                    "page": 0,
                    "text": "MCDDNNSE988444"
                }
            ],
            "metadata": {
                "dimensions": [
                    1200,
                    849
                ],
                "docname": "img2.png",
                "info": "Detected Table",
                "numOfPages": 1,
            },
            "numPackages": [
                {
                    "page": 0,
                    "text": ""
                }
            ],
            "orderID": [
                {
                    "page": 0,
                    "text": "8880666770"
                }
            ],
            "originAddress": [
                {
                    "addressDetails": {
                        "city": "Edgerton",
                        "country": "USA",
                        "name": "SNSF Kansas City Edgerton",
                        "state": "KS",
                        "streetName": " 32880 W. 101 Street Edgerton",
                        "zipCode": "66021"
                    },
                    "page": 0,
                    "text": "SNSF Kansas City Edgerton  - 32880 W. 101 Street Edgerton, KS66021, United States "
                }
            ],
            "pieces": [
                {
                    "page": 0,
                    "text": "18"
                }
            ],
            "placeOfLoading": [
                {
                    "page": 0,
                    "text": "ShangHai, China"
                }
            ],
            "referenceID": [
                {
                    "page": 0,
                    "text": "33330666770"
                }
            ],
            "sealID": [
                {
                    "page": 0,
                    "text": "01144430"
                }
            ],
            "status": true,
            "street": [
                {
                    "page": 0,
                    "text": "United States"
                }
            ],
            "subBolID": [
                {
                    "page": 0,
                    "text": ""
                }
            ],
            "tables": [
                {
                    "cells": [
                        {
                            "bbox": [
                                66,
                                520,
                                270,
                                539
                            ],
                            "cellPosition": [
                                0,
                                0
                            ],
                            "score": 0.98,
                            "text": "Marks, Numbers & Remarks"
                        },
                        {
                            "bbox": [
                                270,
                                520,
                                496,
                                539
                            ],
                            "cellPosition": [
                                0,
                                1
                            ],
                            "score": 0.98,
                            "text": "B/L AWB # or"
                        },
                        {
                            "bbox": [
                                496,
                                520,
                                798,
                                539
                            ],
                            "cellPosition": [
                                0,
                                2
                            ],
                            "score": 0.98,
                            "text": "Description of Goods & Weight"
                        },
                        {
                            "bbox": [
                                66,
                                539,
                                270,
                                569
                            ],
                            "cellPosition": [
                                1,
                                0
                            ],
                            "score": 0.98,
                            "text": "P/O# 8880666770"
                        },
                        {
                            "bbox": [
                                270,
                                539,
                                496,
                                569
                            ],
                            "cellPosition": [
                                1,
                                1
                            ],
                            "score": 0.98,
                            "text": "M B/L No. MCDDNNSE988444 :"
                        },
                        {
                            "bbox": [
                                496,
                                539,
                                798,
                                569
                            ],
                            "cellPosition": [
                                1,
                                2
                            ],
                            "score": 0.98,
                            "text": "Total Weight 215,144.3 LBs +"
                        },
                        {
                            "bbox": [
                                66,
                                569,
                                270,
                                584
                            ],
                            "cellPosition": [
                                2,
                                0
                            ],
                            "score": 0.98,
                            "text": "Vessel: JOHN GLENN"
                        },
                        {
                            "bbox": [
                                270,
                                569,
                                496,
                                584
                            ],
                            "cellPosition": [
                                2,
                                1
                            ],
                            "score": 0.98,
                            "text": "AMS No. AKUKACPH99940996"
                        },
                        {
                            "bbox": [
                                496,
                                569,
                                798,
                                584
                            ],
                            "cellPosition": [
                                2,
                                2
                            ],
                            "score": 0.98,
                            "text": "5,297.20.0 CBF Total Volume +"
                        },
                        {
                            "bbox": [
                                66,
                                584,
                                270,
                                745
                            ],
                            "cellPosition": [
                                3,
                                0
                            ],
                            "score": 0.98,
                            "text": "Voyage: 093J"
                        },
                        {
                            "bbox": [
                                270,
                                584,
                                496,
                                745
                            ],
                            "cellPosition": [
                                3,
                                1
                            ],
                            "score": 0.98,
                            "text": "B/L No. ACHSHEE99944316 : Sub B/L No. : Empty Container Return To =>"
                        },
                        {
                            "bbox": [
                                496,
                                584,
                                798,
                                745
                            ],
                            "cellPosition": [
                                3,
                                2
                            ],
                            "score": 0.98,
                            "text": "PCS: 108Bag GLYPHOSATE 95% TECH IN CASE OF SPILL, LEAK, EXPOSURE OR ACCIDENT, CALL INFOTRAC 24-HR. ER NUMBER 888-323-2200"
                        }
                    ],
                    "metadata": {
                        "bbox": [
                            66,
                            520,
                            798,
                            745
                        ],
                        "page": 0,
                        "score": 0.98,
                        "title": "remarksTable"
                    },
                    "summary": [
                        [
                            "Marks, Numbers & Remarks",
                            "B/L AWB # or",
                            "Description of Goods & Weight"
                        ],
                        [
                            "P/O# 8888647740",
                            "M B/L No. MCDDNNSE988444 :",
                            "Total Weight 215,144.3 LBs +"
                        ],
                        [
                            "Vessel: JOHN GLENN",
                            "AMS No. AKUKACPH99940996 :",
                            "5,297.20.0 CBF Total Volume +"
                        ],
                        [
                            "Voyage: 093J",
                            "B/L No. ACHSHEE99944316 : Sub B/L No. : Empty Container Return To =>",
                            "PCS: 108Bag GLYPHOSATE 95% TECH IN CASE OF SPILL, LEAK, EXPOSURE OR ACCIDENT, CALL INFOTRAC 24-HR. ER NUMBER 888-323-2200"
                        ]
                    ]
                },
                {
                    "cells": [
                        {
                            "bbox": [
                                66,
                                795,
                                196,
                                817
                            ],
                            "cellPosition": [
                                0,
                                0
                            ],
                            "score": 0.98,
                            "text": "CONTAINER No."
                        },
                        {
                            "bbox": [
                                196,
                                795,
                                335,
                                817
                            ],
                            "cellPosition": [
                                0,
                                1
                            ],
                            "score": 0.98,
                            "text": "SEAL No."
                        },
                        {
                            "bbox": [
                                335,
                                795,
                                448,
                                817
                            ],
                            "cellPosition": [
                                0,
                                2
                            ],
                            "score": 0.98,
                            "text": "TYPE"
                        },
                        {
                            "bbox": [
                                448,
                                795,
                                504,
                                817
                            ],
                            "cellPosition": [
                                0,
                                3
                            ],
                            "score": 0.98,
                            "text": "PIECE"
                        },
                        {
                            "bbox": [
                                504,
                                795,
                                569,
                                817
                            ],
                            "cellPosition": [
                                0,
                                4
                            ],
                            "score": 0.98,
                            "text": "WEIGHT"
                        },
                        {
                            "bbox": [
                                569,
                                795,
                                623,
                                817
                            ],
                            "cellPosition": [
                                0,
                                5
                            ],
                            "score": 0.98,
                            "text": "CBM"
                        },
                        {
                            "bbox": [
                                623,
                                795,
                                717,
                                817
                            ],
                            "cellPosition": [
                                0,
                                6
                            ],
                            "score": 0.98,
                            "text": "PICK UP No."
                        },
                        {
                            "bbox": [
                                717,
                                795,
                                798,
                                817
                            ],
                            "cellPosition": [
                                0,
                                7
                            ],
                            "score": 0.98,
                            "text": "LAST FREE"
                        },
                        {
                            "bbox": [
                                66,
                                817,
                                196,
                                867
                            ],
                            "cellPosition": [
                                1,
                                0
                            ],
                            "score": 0.98,
                            "text": "CAAR3230407"
                        },
                        {
                            "bbox": [
                                196,
                                817,
                                335,
                                867
                            ],
                            "cellPosition": [
                                1,
                                1
                            ],
                            "score": 0.98,
                            "text": "01144430"
                        },
                        {
                            "bbox": [
                                335,
                                817,
                                448,
                                867
                            ],
                            "cellPosition": [
                                1,
                                2
                            ],
                            "score": 0.98,
                            "text": "20 Ft"
                        },
                        {
                            "bbox": [
                                448,
                                817,
                                504,
                                867
                            ],
                            "cellPosition": [
                                1,
                                3
                            ],
                            "score": 0.98,
                            "text": "18"
                        },
                        {
                            "bbox": [
                                504,
                                817,
                                569,
                                867
                            ],
                            "cellPosition": [
                                1,
                                4
                            ],
                            "score": 0.98,
                            "text": "16,265"
                        },
                        {
                            "bbox": [
                                569,
                                817,
                                623,
                                867
                            ],
                            "cellPosition": [
                                1,
                                5
                            ],
                            "score": 0.98,
                            "text": "0.0"
                        },
                        {
                            "bbox": [
                                623,
                                817,
                                717,
                                867
                            ],
                            "cellPosition": [
                                1,
                                6
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                717,
                                817,
                                798,
                                867
                            ],
                            "cellPosition": [
                                1,
                                7
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                66,
                                867,
                                196,
                                898
                            ],
                            "cellPosition": [
                                2,
                                0
                            ],
                            "score": 0.98,
                            "text": "CMMN9500970"
                        },
                        {
                            "bbox": [
                                196,
                                867,
                                335,
                                898
                            ],
                            "cellPosition": [
                                2,
                                1
                            ],
                            "score": 0.98,
                            "text": "PP110046"
                        },
                        {
                            "bbox": [
                                335,
                                867,
                                448,
                                898
                            ],
                            "cellPosition": [
                                2,
                                2
                            ],
                            "score": 0.98,
                            "text": "20 Ft"
                        },
                        {
                            "bbox": [
                                448,
                                867,
                                504,
                                898
                            ],
                            "cellPosition": [
                                2,
                                3
                            ],
                            "score": 0.98,
                            "text": "18"
                        },
                        {
                            "bbox": [
                                504,
                                867,
                                569,
                                898
                            ],
                            "cellPosition": [
                                2,
                                4
                            ],
                            "score": 0.98,
                            "text": "16,265"
                        },
                        {
                            "bbox": [
                                569,
                                867,
                                623,
                                898
                            ],
                            "cellPosition": [
                                2,
                                5
                            ],
                            "score": 0.98,
                            "text": "0.0"
                        },
                        {
                            "bbox": [
                                623,
                                867,
                                717,
                                898
                            ],
                            "cellPosition": [
                                2,
                                6
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                717,
                                867,
                                798,
                                898
                            ],
                            "cellPosition": [
                                2,
                                7
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                66,
                                898,
                                196,
                                929
                            ],
                            "cellPosition": [
                                3,
                                0
                            ],
                            "score": 0.98,
                            "text": "ECES0040844"
                        },
                        {
                            "bbox": [
                                196,
                                898,
                                335,
                                929
                            ],
                            "cellPosition": [
                                3,
                                1
                            ],
                            "score": 0.98,
                            "text": "11155088"
                        },
                        {
                            "bbox": [
                                335,
                                898,
                                448,
                                929
                            ],
                            "cellPosition": [
                                3,
                                2
                            ],
                            "score": 0.98,
                            "text": "20 Ft"
                        },
                        {
                            "bbox": [
                                448,
                                898,
                                504,
                                929
                            ],
                            "cellPosition": [
                                3,
                                3
                            ],
                            "score": 0.98,
                            "text": "18"
                        },
                        {
                            "bbox": [
                                504,
                                898,
                                569,
                                929
                            ],
                            "cellPosition": [
                                3,
                                4
                            ],
                            "score": 0.98,
                            "text": "16,265"
                        },
                        {
                            "bbox": [
                                569,
                                898,
                                623,
                                929
                            ],
                            "cellPosition": [
                                3,
                                5
                            ],
                            "score": 0.98,
                            "text": "0.0"
                        },
                        {
                            "bbox": [
                                623,
                                898,
                                717,
                                929
                            ],
                            "cellPosition": [
                                3,
                                6
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                717,
                                898,
                                798,
                                929
                            ],
                            "cellPosition": [
                                3,
                                7
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                66,
                                929,
                                196,
                                960
                            ],
                            "cellPosition": [
                                4,
                                0
                            ],
                            "score": 0.98,
                            "text": "ECES1759046"
                        },
                        {
                            "bbox": [
                                196,
                                929,
                                335,
                                960
                            ],
                            "cellPosition": [
                                4,
                                1
                            ],
                            "score": 0.98,
                            "text": "S9899094"
                        },
                        {
                            "bbox": [
                                335,
                                929,
                                448,
                                960
                            ],
                            "cellPosition": [
                                4,
                                2
                            ],
                            "score": 0.98,
                            "text": "20 Ft"
                        },
                        {
                            "bbox": [
                                448,
                                929,
                                504,
                                960
                            ],
                            "cellPosition": [
                                4,
                                3
                            ],
                            "score": 0.98,
                            "text": "18"
                        },
                        {
                            "bbox": [
                                504,
                                929,
                                569,
                                960
                            ],
                            "cellPosition": [
                                4,
                                4
                            ],
                            "score": 0.98,
                            "text": "16,265"
                        },
                        {
                            "bbox": [
                                569,
                                929,
                                623,
                                960
                            ],
                            "cellPosition": [
                                4,
                                5
                            ],
                            "score": 0.98,
                            "text": "0.0"
                        },
                        {
                            "bbox": [
                                623,
                                929,
                                717,
                                960
                            ],
                            "cellPosition": [
                                4,
                                6
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                717,
                                929,
                                798,
                                960
                            ],
                            "cellPosition": [
                                4,
                                7
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                66,
                                960,
                                196,
                                991
                            ],
                            "cellPosition": [
                                5,
                                0
                            ],
                            "score": 0.98,
                            "text": "ECES1883627"
                        },
                        {
                            "bbox": [
                                196,
                                960,
                                335,
                                991
                            ],
                            "cellPosition": [
                                5,
                                1
                            ],
                            "score": 0.98,
                            "text": "S9959259"
                        },
                        {
                            "bbox": [
                                335,
                                960,
                                448,
                                991
                            ],
                            "cellPosition": [
                                5,
                                2
                            ],
                            "score": 0.98,
                            "text": "20 Ft"
                        },
                        {
                            "bbox": [
                                448,
                                960,
                                504,
                                991
                            ],
                            "cellPosition": [
                                5,
                                3
                            ],
                            "score": 0.98,
                            "text": "18"
                        },
                        {
                            "bbox": [
                                504,
                                960,
                                569,
                                991
                            ],
                            "cellPosition": [
                                5,
                                4
                            ],
                            "score": 0.98,
                            "text": "16,265"
                        },
                        {
                            "bbox": [
                                569,
                                960,
                                623,
                                991
                            ],
                            "cellPosition": [
                                5,
                                5
                            ],
                            "score": 0.98,
                            "text": "0.0"
                        },
                        {
                            "bbox": [
                                623,
                                960,
                                717,
                                991
                            ],
                            "cellPosition": [
                                5,
                                6
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                717,
                                960,
                                798,
                                991
                            ],
                            "cellPosition": [
                                5,
                                7
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                66,
                                991,
                                196,
                                1014
                            ],
                            "cellPosition": [
                                6,
                                0
                            ],
                            "score": 0.98,
                            "text": "TKLU9999014"
                        },
                        {
                            "bbox": [
                                196,
                                991,
                                335,
                                1014
                            ],
                            "cellPosition": [
                                6,
                                1
                            ],
                            "score": 0.98,
                            "text": "S9955349"
                        },
                        {
                            "bbox": [
                                335,
                                991,
                                448,
                                1014
                            ],
                            "cellPosition": [
                                6,
                                2
                            ],
                            "score": 0.98,
                            "text": "20 Ft"
                        },
                        {
                            "bbox": [
                                448,
                                991,
                                504,
                                1014
                            ],
                            "cellPosition": [
                                6,
                                3
                            ],
                            "score": 0.98,
                            "text": "18"
                        },
                        {
                            "bbox": [
                                504,
                                991,
                                569,
                                1014
                            ],
                            "cellPosition": [
                                6,
                                4
                            ],
                            "score": 0.98,
                            "text": "16,265"
                        },
                        {
                            "bbox": [
                                569,
                                991,
                                623,
                                1014
                            ],
                            "cellPosition": [
                                6,
                                5
                            ],
                            "score": 0.98,
                            "text": "0.0"
                        },
                        {
                            "bbox": [
                                623,
                                991,
                                717,
                                1014
                            ],
                            "cellPosition": [
                                6,
                                6
                            ],
                            "score": 0.98,
                            "text": ""
                        },
                        {
                            "bbox": [
                                717,
                                991,
                                798,
                                1014
                            ],
                            "cellPosition": [
                                6,
                                7
                            ],
                            "score": 0.98,
                            "text": ""
                        }
                    ],
                    "metadata": {
                        "bbox": [
                            66,
                            795,
                            798,
                            1014
                        ],
                        "page": 0,
                        "score": 0.98,
                        "title": "containerTable"
                    },
                    "summary": [
                        [
                            "containerID",
                            "sealID",
                            "containerType",
                            "pieces",
                            "containerWeight",
                            "containerVolume",
                            "pickupID",
                            "LAST FREE"
                        ],
                        [
                            "CAAR3230407",
                            "01144430",
                            "20 Ft",
                            "18",
                            "16,265",
                            "0.0",
                            "",
                            ""
                        ],
                        [
                            "CMMN9500970",
                            "PP110046",
                            "20 Ft",
                            "18",
                            "16,265",
                            "0.0",
                            "",
                            ""
                        ],
                        [
                            "ECES0040844",
                            "11155088",
                            "20 Ft",
                            "18",
                            "16,265",
                            "0.0",
                            "",
                            ""
                        ],
                        [
                            "ECES1759046",
                            "S9899094",
                            "20 Ft",
                            "18",
                            "16,265",
                            "0.0",
                            "",
                            ""
                        ],
                        [
                            "ECES1883627",
                            "S9959259",
                            "20 Ft",
                            "18",
                            "16,265",
                            "0.0",
                            "",
                            ""
                        ],
                        [
                            "TKLU9999014",
                            "S9955349",
                            "20 Ft",
                            "18",
                            "16,265",
                            "0.0",
                            "",
                            ""
                        ]
                    ]
                }
            ],
            "telephoneNumber": [
                {
                    "page": 0,
                    "text": "888-002-8491"
                }
            ],
            "totalWeight": [
                {
                    "page": 0,
                    "text": "+ 215,144.3 LBs\n Total"
                }
            ],
            "vesselName": [
                {
                    "page": 0,
                    "text": "JOHN GLENN"
                }
            ],
            "voyageID": [
                {
                    "page": 0,
                    "text": "093J"
                }
            ]
        }
    ],
    "status": true
}
```

This endpoint retrieves context and text from the documents .

### HTTPS Request

`GET   https://api.koireader.com/v1/order/digitize?id=UNIQUE_ID`

<!-- ### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include KoiReaders that have already been adopted. -->

<aside class="success">
<p class = 'success-para'>Remember — to use an authenticated KoiReader API and a valid Document ID!</p>
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




