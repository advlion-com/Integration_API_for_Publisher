# API OF INTEGRATION

- [API OF INTEGRATION](#api-of-integration)
    - [Introduction of document](#introduction-of-document)
    - [Preparation before integration](#preparation-before-integration)
    - [Instruction](#instruction)
        - [URL of request](#url-of-request)
        - [HTTP Method and Encoding](#http-method-and-encoding)
        - [Request](#request)
            - [Request Http Headers](#request-http-headers)
            - [Request Json Fields](#request-json-fields)
                - [Imp information](#imp-information)
                - [App information](#app-information)
                - [Device information](#device-information)
                - [User information](#user-information)
        - [AdResponse](#adresponse)
            - [AdResponse field](#adresponse-field)
                - [seatbid information](#seatbid-information)
                    - [bid information](#bid-information)
            - [Creative forms](#creative-forms)
            - [Reporting macro information](#reporting-macro-information)
            - [Ad response failed reason](#ad-response-failed-reason)


## Introduction of document

This specification is for publishers to integrate with Advlion ADX via API.

## Preparation before integration

Please get the developer account and password through asking for Advlion Adx account manager.

## Instruction

### URL of request

When there is need to request ad, send a HTTP POST request to url: `http://adx.advlion.com/ssp`

### HTTP Method and Encoding

The protocol between Advlion ADX and Publisher is HTTP POST method, data using JSON format, and UTF-8 encoding.

### Request

The Ad Request is a request sent by Publisher to Advlion ADX to request an ad, via the Request URL noted above.

#### Request Http Headers

| http herder information | instruction  |
| --- | --- |
| X-Protocol-Ver | document version，F-1.0 |

#### Request Json Fields

| parameter | type | required | description |
| --- | --- | --- | --- |
| id | string | yes| unique request id |
| imp | array of object | yes | ad information |
| app | object | yes | app information |
| device | object | yes | device information |
| user | object | no | user information |

##### Imp information

| parameter | type | required | description |
| --- | --- | --- | --- |
| id | string | yes | unique imp id |
| instl | integer | yes | adspace type<br>0- banner<br>1- interstitial<br>2- full Screen<br>3- native |
| tagid | string | yes | adslot id |
| secure | integer | no | flag to indicate if the impression requires secure HTTPS URL creative urls and landing page url. By default secure is 0.<br>0- http url <br>1- https url |

##### App information

| parameter | type | required | description |
| --- | --- | --- | --- |
| id | string | yes | APP ID, unique indentifier of an app which is given by AdVlion ADX. |
| name | string | yes | APP name |
| domain | string | no | APP official website domain |
| ver | string | yes | APP version |
| bundle | string | yes | BundleID or package name |
| paid | integer | no | whether need to pay for APP download.<br>0- no<br>1- yes<br>2- pay in app |
| keywords | string | no | APP keywords can be separated by comma. |
| storeurl | string | no | APP download url in app store |

##### Device information

| parameter  | type | required | description |
| --- | --- | --- | --- |
| dnt | integer | no | 0- allow ad tracking<br>1- prohibit ad tracking |
| ua | string | yes | User-Agent of mobile device |
| ip | string | yes | IP adress of client device. It is required when request via S2S. If the request is initiated directly from the client side, the field can be filled in with an empty string. |
| ipv6 | string | no | ipv6 |
| geo | object | no | geographic location informatiom |
| geo.lat | float | no | latitude  |
| geo.lon | float | no | longitude |
| geo.timestamp | integer | no | timestamp when obtaining latitude and longitude data |
| geo.country | string | no | country, using `ISO-3166-1 Alpha-3` |
| geo.region | string | no | area, using `ISO 3166-2` |
| geo.city | string | no | city, using `http://www.unece.org/cefact/locode/service/location.html` |
| devicetype | integer | yes | device type<br>1- mobilephone<br>2- Tablet PC |
| make | string | yes | device manufacturer |
| model | string | yes | device model |
| os | string | yes | Operation system, "iOS" or  "Android" |
| osv | string | yes | Operation system version |
| w | integer | yes | Device screen width pixel. |
| h | integer | yes | Device screen height pixel. |
| ppi | float | yes | Physical pixel density |
| carrier | string | yes | Mobile device carrier: MCC+MNC. If there is no value of MCC+MNC, the field can be filled in with an empty string. View `http://en.wikipedia.org/wiki/Mobile_Network_Code` |
| language | string | no | Device language settings, using `alpha-2/ISO 639-1` |
| js | integer | no | whether Javascript is supported<br>1-yes<br>0-no |
| connectiontype | integer | yes | network connection type<br>1- wifi<br>2- 2G<br>3- 3G<br>4- 4G |
| ext | object | yes | expansion fields |
| ext.orientation | integer | no | Device orientation<br>0- portrait<br>1- landscape |
| ext.imei | string | no | IMEI for android device. |
| ext.idfa | string | no | IDFA for ios device. |
| ext.androidid | string | no | AndroidID is required for android device. |
| ext.gadid | string | no | Google Advertising ID. Publisher must fill AndroidID or Google Advertising ID. |
| ext.mac | string | no | MAC, the field can be filled in with an empty string. |
| ext.imsi | string | no | international Mobile User identifer, which is stored in SIM card  |
| ext.battery | integer | no | Battery volume of the device between 0~100 |
| ext.density | float | yes | Device screen density |

##### User information

| parameter | type | required | description |
| --- | --- | --- | --- |
| id | string | no | user id |
| yob | integer | no | Year of birth, 4 digits |
| gender | string | no | gender<br>M- Male<br>F- Female<br>O- Other<br>Null- Unknown |
| geo | object | no | geographic location informatiom |
| geo.lat | float | no | latitude |
| geo.lon | float | no | longitude |
| geo.timestamp | integer | no | timestamp when obtaining latitude and longitude data |
| geo.country | string | no | country, using `ISO-3166-1 Alpha-3` |
| geo.region | string | no | area, using `ISO 3166-2` |
| geo.city | string | no | city, using `http://www.unece.org/cefact/locode/service/location.html` |


### AdResponse

#### AdResponse field

| parameter | type | required | description |
| --- | --- | --- | --- |
| id | string | yes | unique request id in ad request|
| nbr | integer | no | adresponse failed reason when there is no official adresponse, view [Ad response failed reason](#ad-response-failed-reason). |
| seatbid | array of object | no | Ad information, if request succeed |

##### seatbid information

| parameter | type | required | description |
| --- | --- | --- | --- |
| bid | array of object | yes | ad information |
                                                                                
###### bid information
| parameter | type | required | description |
| --- | --- | --- | --- |
| impid | string | yes | impression id in ad request |
| cid | string | yes | creative id |
| w | integer | no | creative width pixel |
| h | integer | no | creative height pixel |
| adm | string | yes | Creative types of the ad response,view [Ad format](#ad-format)<br>image（HTML）: HTML<br>image（image and landing page）: JSON<br>native: JSON |
| ext | object | yes | Extended field |
| ext.ctype | integer | yes | adm type of banner/interstitial/full Screen<br>1- HTML<br>2- json |
| ext.instl | integer | yes | adspace<br>0- banner<br>1- interstitial<br>2- full Screen<br>3- native |
| ext.interact_type | integer | yes | types of click action, <br>1- open the url within webview in-app<br>2- download App |
| ext.ad_logo | string | no | Ad source Logo |
| ext.ad_icon | string | no | "ad" character. It's optional, Publisher can use their own design. |
| ext.deeplink | string | no | Redirect URL which of deep-link, use 'ldp' if it doesn't work. <br>If the app is installed beforehand, it redirects to the specific page,otherwise it redirects to the normal landing page. |
| ext.imp_t | array of string | no | Impression tracking URL,multiple reporting URLs should all be reported.<br>Client side shall substitute macro variables in imp_t when reporting (if macro variable is existed). View [Reporting macro information](#reporting-macro-informationn) |
| ext.clk_t | array of string | no | Click tracking URL,multiple reporting URLs should all be reported.<br>Client side shall substitute macro variables in imp_t when reporting (if macro variable is existed). View [Reporting macro information](#reporting-macro-informationn) |
| ext.ds_t | array of string | no | When ext.interact_type = 2 publisher should deal with this attribute.<br>Client side needs to visit one by one when download triggered. |
| ext.dc_t | array of string | no | When ext.interact_type = 2 publisher should deal with this attribute.<br>Client side needs to visit one by one when the app has been downloaded. |
| ext.ic_t | array of string | no | When ext.interact_type = 2 publisher should deal with this attribute.<br>Client side needs to visit one by one when the app has been installed. |
| ext.op_t | array of string | no | When ext.interact_type = 2 publisher should deal with this attribute.<br>Client side needs to visit one by one when the app has benn opened. |
| ext.d_app_name | string | no | When ext.interact_type = 2 publisher should deal with this attribute.<br>APP name.|
| ext.d_app_icon | string | no | When ext.interact_type = 2 publisher should deal with this attribute.<br>APP icon url. |
| ext.d_app_pkg | string | no | When ext.interact_type = 2 publisher should deal with this attribute.<br>APP package name. |
| ext.d_app_size | integer | no | When ext.interact_type = 2 publisher should deal with this attribute.<br>APP package size. |

#### Creative forms
- image（image + landing page）
```json
{
    // image url
    "url": "",
    // landing page
    "ldp": "",
    // ad title, not required
    "title": "",
    // ad subtitle, not required
    "subtitle": "",
    // ad description, not required
    "desc": ""
}
```

- native
```json
{
    // title, not required
    "title": "",
    // description, not required
    "desc": "",
    // image（single image or three images）
    "img": [
        {
            // image url
            "url": "",
            "w": 300,
            "h": 250
        },
        {
            // image url
            "url": "",
            "w": 300,
            "h": 250
            
        },
        {
            // image url
            "url": "",
            "w": 300,
            "h": 250
        }
    ],
    // icon
    "icon": {
        // icon url
        "url": "",
        "w": 300,
        "h": 250
    },
    // landing page
    "ldp": ""
}
```

#### Reporting macro information

> Client shall substitute macro variables of urls in imp_t and clk_t url when reporting (if macro variable is existed).
> The following macros should all be substituted: 

| macro | type | description |
| --- | --- | --- |
| {UUID} | string | Unique identifer of device<br>IMEI for Android<br>IDFA for iOS |
| {LATITUDE} | float | Geo information, latitude  |
| {LONGITUDE} | float | Geo information, longitude |
| {CLICK_DOWN_X} | integer | The absolute X-axis value of where user clicks |
| {CLICK_DOWN_Y} | integer | The absolute Y-axis value of where user clicks  |
| {CLICK_UP_X}   | integer | The absolute X-axis value of when user’s fingers leave the screen  |
| {CLICK_UP_Y}   | integer | The absolute Y-axis value of when user’s fingers leave the screen  |
| {R_CLICK_DOWN_X} | integer | The relative X-axis value of where user clicks |
| {R_CLICK_DOWN_Y} | integer | The relative Y-axis value of where user clicks |
| {R_CLICK_UP_X}   | integer | The relative X-axis value of when user’s fingers leave the screen |
| {R_CLICK_UP_Y}   | integer | The relative Y-axis value of when user’s fingers leave the screen |

#### Ad response failed reason

| code | description |
| --- | --- |
| 101 | test ad response |
| 102 | no test ad and official ads response |
| 104 | Ad Request JSON parsing failed |
| 105 | adslot id invalid |
| 302 | device.ext.androidid missing |
| 304 | device.ext.idfa missing |
| 311 | app.id missing |
| 312 | app.name missing |
| 313 | app.bundle missing |
| 314 | app.ver missing |
| 315 | device.os missing |
| 316 | device.os invalid |
| 317 | device.osv missing |
| 318 | device.carrier missing |
| 320 | device.connectiontype missing |
| 321 | device.connectiontype invalid |
| 322 | device.ip missing |
| 323 | device.make missing |
| 324 | device.model missing |
| 325 | device.w missing |
| 326 | device.h missing |
| 327 | device.devicetype missing |
| 328 | device.devicetype invalid |
| 341 | imp.instl missing |
| 342 | imp.instl invalid |
| 351 | request id missing |
| 352 | impression id missing |
| 353 | device.ua missing |
| 354 | device.ext.ppi missing |
| 355 | device.ext.density missing |
| 410 | device.ext.anid, wrong format |
| 411 | device.ext.imei, wrong format |
| 412 | device.ip, wrong format |
| 414 | device.ext.idfa, wrong format |
| 500 | low quality request |
| 900 | ADX server internal error，please contact Advlion ADX |
