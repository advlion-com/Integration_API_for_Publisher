# SSP 对接文档协议

- [SSP 对接文档协议](#ssp-对接文档协议)
    - [文档说明](#文档说明)
    - [接入准备](#接入准备)
    - [接入说明](#接入说明)
        - [请求 URL](#请求-url)
        - [通信方式及编码](#通信方式及编码)
        - [广告请求](#广告请求)
            - [请求头](#请求头)
            - [AdRequest 字段信息](#adrequest-字段信息)
                - [imp 对象信息](#imp-对象信息)
                - [app 对象信息](#app-对象信息)
                - [device 对象信息](#device-对象信息)
                - [user 对象信息](#user-对象信息)
        - [广告返回](#广告返回)
            - [AdResponse 字段信息](#adresponse-字段信息)
                - [seatbid 对象信息](#seatbid-对象信息)
                    - [bid 对象信息](#bid-对象信息)
            - [素材格式](#素材格式)
            - [上报地址宏替换信息](#上报地址宏替换信息)
            - [不填充广告原因](#不填充广告原因)

## 文档说明

此文档仅供开发者或 SSP 与 AdVlion 交易平台（ADX） 使用 API 方式对接时使用。

## 接入准备

在 开发者（SSP）和 AdVlion交易平台（ADX） 商务人员沟通后，由 AdVlion交易平台（ADX）商务人员提供 开发者 账号和密码。

## 接入说明

### 请求 URL

当需要请求广告时，发送一个 HTTP POST 请求到下面的地址`http://adx.advlion.com/ssp`

### 通信方式及编码

ADX 和 开发者（SSP） 之间的基础通信协议采用 HTTP 协议、POST 方法，数据使用 JSON 格式，编码采用 UTF-8 编码。

### 广告请求

AdRequest 请求是广告位请求广告的入口，由 SSP 按本文档中规定 URL 向 ADX 发送。

#### 请求头

| http 头信息段 | 说明  |
| --- | --- |
| X-Protocol-Ver | 文档版本号，F-1.0 |

#### AdRequest 字段信息

| 字段名称 | 类型 | 必须 | 描述 |
| --- | --- | --- | --- |
| id | string | 是| 唯一请求id |
| imp | array of object | 是 | 请求广告的信息 |
| app | object | 是 | APP 信息 |
| device | object | 是 | 设备信息 |
| user | object | 否 | 用户信息 |

##### imp 对象信息

| 字段名称 | 类型 | 必须 | 描述 |
| --- | --- | --- | --- |
| id | string | 是 | 唯一曝光id |
| instl | integer | 是 | 广告位类型<br>0- banner<br>1- 插屏<br>2- 开屏<br>3- 原生 |
| tagid | string | 是 | 广告位id |
| secure | integer | 否 | 是否需要 https 链接的标识，默认为 0<br>0- 不需要<br>1- 需要 |

##### app 对象信息

| 字段名称 | 类型 | 必须 | 描述 |
| --- | --- | --- | --- |
| id | string | 是 | 媒体 ID，注册 ADX 平台生成的 ID |
| name | string | 是 | APP 名称 |
| domain | string | 否 | APP 官网域名 |
| ver | string | 是 | APP 版本号 |
| bundle | string | 是 | BundleID 或者包名 |
| paid | integer | 否 | 是否为付费 APP<br>0- 不是<br>1- 是<br>2- 应用内付费 |
| keywords | string | 否 | APP 关键字，可以用英文逗号分隔多个 |
| storeurl | string | 否 | APP 在应用市场的下载地址 |

##### device 对象信息

| 字段名称  | 类型 | 必须 | 描述 |
| --- | --- | --- | --- |
| dnt | integer | 否 | 0- 允许广告追踪<br>1- 不允许广告追踪 |
| ua | string | 是 | 移动设备的 User-Agent |
| ip | string | 是 | 客户端IP地址。如果从客户端直接发起请求，该字段可填空字符串；如果从服务端发起请求，请填写客户端的IP |
| ipv6 | string | 否 | ipv6 |
| geo | object | 否 | 地理位置信息对象 |
| geo.lat | float | 否 | 纬度 |
| geo.lon | float | 否 | 经度 |
| geo.timestamp | integer | 否 | 获取经纬度数据时的时间戳 |
| geo.country | string | 否 | 国家，使用 `ISO-3166-1 Alpha-3` |
| geo.region | string | 否 | 地区，使用 `ISO 3166-2` |
| geo.city | string | 否 | 城市，使用 `http://www.unece.org/cefact/locode/service/location.html` |
| devicetype | integer | 是 | 设备类型<br>1- 手机<br>2- 平板 |
| make | string | 是 | 设备制造商 |
| model | string | 是 | 设备型号 |
| os | string | 是 | 设备操作系统，二选一填写 Android 或 iOS |
| osv | string | 是 | 设备操作系统版本号 |
| w | integer | 是 | 设备屏幕分辨率宽，单位为像素 |
| h | integer | 是 | 设备屏幕分辨率高，单位为像素 |
| ppi | float | 是 | 每英寸像素密度 |
| carrier | string | 是 | 设备使用的运营商：MCC+MNC的值。没有则为空字符串。参考 `http://en.wikipedia.org/wiki/Mobile_Network_Code` |
| language | string | 否 | 设备的语言设置,使用 `alpha-2/ISO 639-1` |
| js | integer | 否 | 是否支持 Javascript 脚本<br>1-支持<br>0-不支持 |
| connectiontype | integer | 是 | 设备联网类型<br>1- wifi<br>2- 2G<br>3- 3G<br>4- 4G |
| ext | object | 是 | 扩展字段 |
| ext.orientation | integer | 否 | 设备屏幕方向<br>0- 竖向<br>1- 横向 |
| ext.imei | string | 否 | Android 设备的 IMEI 值 |
| ext.idfa | string | 否 | iOS 设备必填，IDFA 值 |
| ext.idfv | string | 否 | iOS 设备必填，IDFV 值 |
| ext.androidid | string | 否 | Android 设备必填，AndroidID |
| ext.gadid | string | 否 | Android 设备选填，Google Advertising ID<br>imei 或 gadid 必填其中一个 |
| ext.mac | string | 否 | MAC 值，没有填空字符串 |
| ext.imsi | string | 否 | 国际移动用户识别码，储存在 SIM 卡中 |
| ext.battery | integer | 否 | 设备电量百分比，取整数，数值区间 0~100 |
| ext.density | float | 是 | 设备屏幕像素密度 |

##### user 对象信息

| 字段名称 | 类别 | 必须 | 描述 |
| --- | --- | --- | --- |
| id | string | 否 | 用户唯一 ID |
| yob | integer | 否 | 出生年，4 位数字 |
| gender | string | 否 | 性别<br>M- 男性<br>F- 女性<br>O- 其他<br>Null- 不确定 |
| geo | object | 否 | 用户家庭位置 |
| geo.lat | float | 否 | 纬度 |
| geo.lon | float | 否 | 经度 |
| geo.timestamp | integer | 否 | 获取经纬度数据时的时间戳 |
| geo.country | string | 否 | 国家，使用 `ISO-3166-1 Alpha-3` |
| geo.region | string | 否 | 地区，使用 `ISO 3166-2` |
| geo.city | string | 否 | 城市，使用`http://www.unece.org/cefact/locode/service/location.html` |


### 广告返回

#### AdResponse 字段信息

| 字段名称 | 类型 | 必须 | 描述 |
| --- | --- | --- | --- |
| id | string | 是 | 对应请求中的唯一请求id |
| nbr | integer | 否 | 无正式广告填充时返回，不填充的原因，详情见[不填充广告原因](#不填充广告原因) |
| seatbid | array of object | 否 | 有广告填充时返回，广告信息 |

##### seatbid 对象信息

| 字段名称 | 类型 | 必须 | 描述 |
| --- | --- | --- | --- |
| bid | array of object | 是 | 广告信息 |
                                                                                
###### bid 对象信息
| 字段名称 | 类型 | 必须 | 描述 |
| --- | --- | --- | --- |
| impid | string | 是 | 对应请求中的曝光id |
| cid | string | 是 | 创意id |
| w | integer | 否 | 广告物料宽度，单位：像素 |
| h | integer | 否 | 广告物料高度，单位：像素 |
| adm | string | 是 | 素材，详情见[素材格式](#素材格式)<br>图片类（HTML）：HTML<br>图片类（图片+落地页）：JSON<br>原生：JSON |
| ext | object | 是 | 扩展字段 |
| ext.instl | integer | 是 | 广告位类型<br>0- banner<br>1- 插屏<br>2- 开屏<br>3- 原生 |
| ext.interact_type | integer | 是 | 用户点击行为<br>1- 浏览网页<br>2- 下载应用 |
| ext.ad_logo | string | 否 | 广告来源LOGO图片 |
| ext.ad_icon | string | 否 | "广告"字样图片 |
| ext.deeplink | string | 否 | deeplink<br>如果终端安装了对应的APP，则跳转到deeplink<br>如果没有安装，则跳转普通落地页 |
| ext.imp_t | array of string | 否 | 曝光监测，可能有多条，需要依次上报<br>监测链接中可能有宏，需要开发者替换，见[上报地址宏替换信息](#上报地址宏替换信息) |
| ext.clk_t | array of string | 否 | 点击监测，可能有多条，需要依次上报<br>监测链接中可能有宏，需要开发者替换，见[上报地址宏替换信息](#上报地址宏替换信息) |
| ext.ds_t | array of string | 否 | ext.interact_type = 2 时可能返回<br>应用下载开始监测，可能有多条，需要依次上报 |
| ext.dc_t | array of string | 否 | ext.interact_type = 2 时可能返回<br>应用下载完成监测，可能有多条，需要依次上报 |
| ext.ic_t | array of string | 否 | ext.interact_type = 2 时可能返回<br>应用安装完成监测，可能有多条，需要依次上报 |
| ext.op_t | array of string | 否 | ext.interact_type = 2 时可能返回<br>应用打开监测，可能有多条，需要依次上报 |
| ext.d_app_name | string | 否 | ext.interact_type = 2 时可能返回<br>下载应用的名称 |
| ext.d_app_icon | string | 否 | ext.interact_type = 2 时可能返回<br>下载应用的图标 |
| ext.d_app_pkg | string | 否 | ext.interact_type = 2 时可能返回<br>下载应用的包名 |
| ext.d_app_size | integer | 否 | ext.interact_type = 2 时可能返回<br>下载应用的大小 |

#### 素材格式
- 图片类（图片+落地页）
```json
{
    // 图片地址
    "url": "",
    // 落地页
    "ldp": "",
    // 广告标题，非必填
    "title": "",
    // 广告副标题，非必填
    "subtitle": "",
    // 广告描述，非必填
    "desc": ""
}
```

- 原生
```json
{
    // 标题，非必填
    "title": "",
    // 描述，非必填
    "desc": "",
    // 大图（可能有单图或三图）
    "img": [
        {
            // 图片地址
            "url": "",
            "w": 300,
            "h": 250
        },
        {
            // 图地址
            "url": "",
            "w": 300,
            "h": 250
        },
        {
            // 图地址
            "url": "",
            "w": 300,
            "h": 250
        }
    ],
    // 图标，非必填
    "icon": {
        // 图标地址
        "url": "",
        "w": 300,
        "h": 250
    },
    // 落地页
    "ldp": ""
}
```

#### 上报地址宏替换信息

> 客户端在触发上报信息时，必须将监测链接中的宏变量替换上报。可能出现宏
> 需要替换的宏坐标如下：

| 宏变量 | 类型 | 说明 |
| --- | --- | --- |
| {UUID} | string | 设备唯一标识<br>iOS 使用 IDFA， Android 使用 IMEI |
| {LATITUDE} | float | 地理位置信息，纬度 |
| {LONGITUDE} | float | 地理位置信息，经度 |
| {CLICK_DOWN_X} | integer | 用户点击绝对坐标宏，用于回传用户点击坐标，广告位左上角为原点<br>获取用户点击落下的X坐标 |
| {CLICK_DOWN_Y} | integer | 获取用户点击落下的绝对Y坐标 |
| {CLICK_UP_X}   | integer | 获取用户点击抬起的绝对X坐标 |
| {CLICK_UP_Y}   | integer | 获取用户点击抬起的绝对Y坐标 |
| {R_CLICK_DOWN_X} | integer | 用户点击相对坐标宏，用于回传用户点击坐标相对于广告的位置，广告位左上角为原点，获取用户按下抬起坐标与广告右下角（广告最大尺寸值）的坐标的比，之后扩大 1000 倍取整数的结果<br>获取用户点击落下的相对X坐标 |
| {R_CLICK_DOWN_Y} | integer | 获取用户点击落下的相对Y坐标 |
| {R_CLICK_UP_X}   | integer | 获取用户点击抬起的相对X坐标 |
| {R_CLICK_UP_Y}   | integer | 获取用户点击抬起的相对Y坐标 |

#### 不填充广告原因

| 状态码 | 说明 |
| --- | --- |
| 101 | 返回测试广告 |
| 102 | 无测试广告且无正式广告返回 |
| 104 | BidRequest 解析 JSON 失败 |
| 105 | 广告位id无效 |
| 302 | device.ext.androidid 缺失 |
| 304 | device.ext.idfa 缺失 |
| 311 | app.id 缺失 |
| 312 | app.name 缺失 |
| 313 | app.bundle 缺失 |
| 314 | app.ver 缺失 |
| 315 | device.os 缺失 |
| 316 | device.os 无效 |
| 317 | device.osv 缺失 |
| 318 | device.carrier 缺失 |
| 320 | device.connectiontype 缺失 |
| 321 | device.connectiontype 无效 |
| 322 | device.ip 缺失 |
| 323 | device.make 缺失 |
| 324 | device.model 缺失 |
| 325 | device.w 缺失 |
| 326 | device.h 缺失 |
| 327 | device.devicetype 缺失 |
| 328 | device.devicetype 无效 |
| 341 | imp.instl 缺失 |
| 342 | imp.instl 无效 |
| 351 | 请求id 缺失 |
| 352 | 曝光id 缺失 |
| 353 | device.ua 缺失 |
| 354 | device.ext.ppi 缺失 |
| 355 | device.ext.density 缺失 |
| 410 | device.ext.anid 格式错误 |
| 411 | device.ext.imei 格式错误 |
| 412 | device.ip 格式错误 |
| 414 | device.ext.idfa 格式错误 |
| 500 | 低质量流量 |
| 900 | ADX 广告服务器内部错误，请联系平台 |
