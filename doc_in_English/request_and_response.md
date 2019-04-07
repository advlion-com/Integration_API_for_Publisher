# API OF INTEGRATION

- [API OF INTEGRATION](#api-of-integration)
    - [Introduction of document](#introduction-of-document)
    - [Preparation before integration](#preparation-before-integration)
    - [Instruction](#instruction)
        - [URL of request](#url-of-request)
        - [Communication Mode and Encoding](#communication-mode-and-encoding)
        - [Request](#request)
            - [Request header](#request-header)
            - [AdRequest field](#adrequest-field)
                - [imp information](#imp-information)
                - [app information](#app-information)
                - [device information](#device-information)
                - [user information](#user-information)
        - [Responce](#responce)
            - [AdResponse information](#adresponse-information)
                - [seatbid information](#seatbid-information)
                    - [bid information](#bid-information)
            - [Creative forms](#creative-forms)
            - [Report click-macro information](#report-click-macro-information)
            - [Ad response failed reason](#ad-responce-failed-reason)

## Introduction of document

This specification is for publishers to integrate with Advlion ADX via API.

## Preparation before integration

Please get the developer account and password through asking for Advlion Adx account manager.

## Instruction

### URL of request

When there is need to request ad, send a HTTP POST to the following address: `http://adx.advlion.com/ssp`

### Communication Mode and Encoding

The underlying communication protocol between Advlion ADX and SSP is HTTP, POST method, data using JSON format, UTF-8 encoding.

### Request

The Ad Request is a request sent by the SSP to Advlion ADX to call for an ad, via the Request URL noted above.

#### Request header

| http herder information | instruction  |
| --- | --- |
| X-Protocol-Ver | document version，F-1.0 |

#### Request field

| parameter | type | mandatory | description |
| --- | --- | --- | --- |
| id | string | yes| unique request id   |
| imp | array of object | yes | Ad information |
| app | object | yes | app information |
| device | object | yes | device information |
| user | object | no | user information |

##### Imp information

| parameter | type | mandatory | description |
| --- | --- | --- | --- |
| id | string | yes | unique imp id |
| instl | integer | yes | adspace type<br>0- banner<br>1- interstitial<br>2- full Screen <br>3- native  |
| tagid | string | yes | adspace id |
| secure | integer | no |Flag to indicate if the impression requires secure HTTPS URL creative assets and markup, where 0 = nonsecure, 1 = secure. If omitted, the secure state is unknown, but non-secure HTTP support can be assumed. <br>0- creative from http url <br>1-  creative from https url  |

##### App information

| parameter | type | mandatory | description |
| --- | --- | --- | --- |
| id | string | yes | app ID，unique indentifier of an app which is given after registering app in Advlion publisher UI  (http://mammut.vlion.cn). |
| name | string | yes | APP name |
| domain | string | no | APP official website |
| ver | string | yes | APP version |
| bundle | string | yes | BundleID or package name |
| paid | integer | no | whether need to pay for APP download <br>0- no<br>1- yes<br>2- pay in app |
| keywords | string | no | APP keywords can be separated by commas  |
| storeurl | string | no | APP adress in app download store |

##### Device information

| parameter  | type | mandatory | description |
| --- | --- | --- | --- |
| dnt | integer | no | 0- allow ad tracking；1-prohibit ad tracking |
| ua | string | yes | User-Agent of mobile device |
| ip | string | yes | IP adress of client device. It is required when request via S2S.If the request is initiated directly from the client side, the field can be filled in with an empty string. |
| ipv6 | string | no | ipv6 |
| geo | object | no | geographic location informatiom |
| geo.lat | float | no | latitude  |
| geo.lon | float | no | longitude |
| geo.timestamp | integer | no | timestamp when obtaining latitude and longitude data |
| geo.country | string | no | country,using `ISO-3166-1 Alpha-3` |
| geo.region | string | no | area,using `ISO 3166-2` |
| geo.city | string | no | city,using`http://www.unece.org/cefact/locode/service/location.html` |
| devicetype | integer | yes | device type<br>1- mobilephone <br>2- Tablet PC |
| make | string | yes | manufacturer, e.g. “Samsung” |
| model | string | yes | device model |
| os | string | yes | Operation system, "ios" or  "android" |
| osv | string | yes | Operation system version |
| w | integer | yes | Device screen width, unit:pixel. If not passed, fill rate will be affected. |
| h | integer | yes | Device screen height, unit:pixel. If not passed, fill rate will be affected. |
| ppi | float | yes | Physical pixel density |
| carrier | string | yes | Mobile device carrier ：MCC+MNC. If there is no value of MCC+MNC, the field can be filled in with an empty string. view`http://en.wikipedia.org/wiki/Mobile_Network_Code` |
| language | string | no | Device language settings,use `alpha-2/ISO 639-1` |
| js | integer | no | whether Javascript is supported<br>1-yes<br>0-no |
| connectiontype | integer | yes | network connection type <br>1- wifi<br>2- 2G<br>3- 3G<br>4- 4G |
| ext | object | yes | expansion field  |
| ext.orientation | integer | no | Device orientation<br>0- portrait<br>1- landscape |
| ext.imei | string | no | Unique identifer of android device. |
| ext.idfa | string | no | Unique identifer of ios device. |
| ext.androidid | string | no | AndroidID is used to identify your device for market downloads |
| ext.mac | string | yes | MAC value,empty means unknown. |
| ext.imsi | string | no | international Mobile User identifer, which is stored in SIM card  |
| ext.battery | integer | no | Battery volume of the device, integer from 0~100%  |
| ext.density | float | yes | Device screen density  |

##### User information

| parameter | type | mandatory | description |
| --- | --- | --- | --- |
| id | string | no | user id |
| yob | integer | no | Year of birth, 4 digits |
| gender | string | no | gender<br>M- Male<br>F- Female<br>O- Other<br>Null- Unknown |
| geo | object | no | geographic location informatiom |
| geo.lat | float | no | latitude |
| geo.lon | float | no | longitude |
| geo.timestamp | integer | no | timestamp when obtaining latitude and longitude data |
| geo.country | string | no | country,use `ISO-3166-1 Alpha-3` |
| geo.region | string | no | area,use `ISO 3166-2` |
| geo.city | string | no | city,use`http://www.unece.org/cefact/locode/service/location.html` |


### AdResponse

#### AdResponse field

| parameter | type | mandatory | description |
| --- | --- | --- | --- |
| id | string | yes | unique request id |
| nbr | integer | no | adresponse failed reason when there is no official adresponse, view[Ad response failed reason](#Ad response failed reason) |
| seatbid | array of object | no | Ad information, if request succeed |

##### seatbid information

| parameter | type | mandatory | description |
| --- | --- | --- | --- |
| bid | array of object | yes | ad information |
                                                                                
###### bid information
| parameter | type | mandatory | description |
| --- | --- | --- | --- |
| impid | string | yes | impression id |
| cid | string | yes | creative id |
| w | integer | no | Ad width, unit: pixel |
| h | integer | no | Ad height, unit: pixel |
| adm | string | yes | Creative types of the ad response ,view[Ad format](#Ad format)<br>image（HTML）：HTML<br>image（image and text）：JSON<br>native：JSON |
| ext | object | yes | expansion field |
| ext.instl | integer | yes | adspace<br>0- banner<br>1- 插屏<br>2- 开屏<br>3- native |
| ext.interact_type | integer | yes | types of click action, <br>1- open the url within webview in-app<br>2- download App |
| ext.ad_logo | string | no | Ad source Logo |
| ext.ad_icon | string | no | “ad” character, It’s optional, publishers can use their own design. |
| ext.deeplink | string | no | Redirect URL which of deep-link, use ’Click redirect URL’ if it doesn’t work. <br>If the app is installed beforehand, it redirects to the specific page,otherwise it redirects to the normal landing page.   |
| ext.imp_t | array of string | no | Impression tracking URL,multiple reporting URLs should all be reported.<br>Client side shall substitute macro variables of click_tracking url ， target_url and Video information_url when reporting (if macro variable is existed) in pixels. view[Reporting the information of macro substitution](#Reporting the information of macro substitution) |
| ext.clk_t | array of string | no | Click redirect URL,multiple reporting URLs should all be reported.<br>Client side shall substitute macro variables of click_tracking url ， target_url and Video information_url when reporting (if macro variable is existed) in pixels. view[Reporting the information of macro substitution](#Reporting the information of macro substitution) |
| ext.ds_t | array of string | no | when ext.interact_type = 2 need to deal with this attribute.<br>Download performance tracker, client side needs to visit one by one when download triggered. ["url1","url2", ...]  |
| ext.dc_t | array of string | no | when ext.interact_type = 2 need to deal with this attribute.<br>Download performance tracker, client side needs to visit one by one when the app download is finished. ["url1","url2", ...] 
Android  |
| ext.ic_t | array of string | no | when ext.interact_type = 2 need to deal with this attribute. <br>Download performance tracker, client side needs to visit one by one when the app is installed. ["url1","url2", ...]  |
| ext.op_t | array of string | no |when ext.interact_type = 2 need to deal with this attribute.<br>Download performance tracker, client side needs to visit one by one when the app is opened. "url1","url2", ...]  |

#### Creative forms
- image（image+landing page）
```json
{
    // image url
    "url": "",
    // landing page
    "ldp": ""
}
```

- native
```json
{
    // title
    "title": "",
    // description
    "desc": "",
    // image（single image or three images）
    "img": [
        {
            // image url
            "url": ""
        },
        {
            // image url
            "url": ""
        },
        {
            // image url
            "url": ""
        }
    ],
    // icon
    "icon": {
        // icon url
        "url": ""
    },
    // landing page
    "ldp": ""
}
```

#### Report click-macro information

> When Ad has been Start_play,end_play，show，clicked, Closed，client shall substitute macro variables of click_tracking url ， target_url and Video information_url when reporting (if macro variable is existed) in pixels. 
> The following macros should all be substituted: 

| macro | type | description |
| --- | --- | --- |
| {UUID} | string | Unique identifer of device<br>Android use IMEI, ios use IDFA |
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
| 104 | BidRequest parsing JSON failed |
| 105 | adspace id invalid |
| 301 | device.ext.imei missing |
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
| 900 | ADX server internal error，please contact Advlion adx |
