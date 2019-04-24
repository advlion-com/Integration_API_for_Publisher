# 广告请求和返回json示例

- [广告请求和返回json示例](#广告请求和返回json示例)
    - [横幅](#横幅)
        - [横幅请求示例](#横幅请求示例)
        - [横幅广告返回示例（HTML）](#横幅广告返回示例html)
        - [横幅广告返回示例（图片）](#横幅广告返回示例图片)
        - [横幅广告返回示例（图文）](#横幅广告返回示例图文)
    - [原生](#原生)
        - [原生请求示例](#原生请求示例)
        - [原生广告返回示例](#原生广告返回示例)

- 可以使用的测试参数：

> | tagid | appid | os | 广告位类型 | 返回格式 | 交互类型 |
> | --- | --- | --- | --- | --- | --- |
> | 23448 | 30087 | Android | 横幅 | html | 网页 |
> | 23449 | 30087 | Android | 横幅 | image | 网页 |
> | 23450 | 30087 | Android | 横幅 | image | 下载 |
> | 23452 | 30087 | Android | 原生 | - | 网页 |
> | 23453 | 30087 | Android | 原生 | - | 下载 |
> | 23454 | 30087 | Android | 开屏 | html | 网页 |
> | 23457 | 30087 | Android | 开屏 | image | 网页 |
> | 23458 | 30087 | Android | 开屏 | image | 下载 |
> | 23459 | 30087 | Android | 插屏 | html | 网页 |
> | 23461 | 30087 | Android | 插屏 | image | 网页 |
> | 23462 | 30087 | Android | 插屏 | image | 下载 |
> | 23463 | 30088 | iOS | 横幅 | html | 网页 |
> | 23465 | 30088 | iOS | 横幅 | image | 网页 |
> | 23466 | 30088 | iOS | 横幅 | image | 下载 |
> | 23467 | 30088 | iOS | 原生 | - | 网页 |
> | 23468 | 30088 | iOS | 原生 | - | 下载 |
> | 23469 | 30088 | iOS | 开屏 | html | 网页 |
> | 23471 | 30088 | iOS | 开屏 | image | 网页 |
> | 23472 | 30088 | iOS | 开屏 | image | 下载 |
> | 23473 | 30088 | iOS | 插屏 | html | 网页 |
> | 23475 | 30088 | iOS | 插屏 | image | 网页 |
> | 23476 | 30088 | iOS | 插屏 | image | 下载 |

> - 使用测试参数获取的广告，仅供查看效果使用，正式上线后请切换为正式的id，否则将不会产生任何请求，展示，点击，收益等数据。

## 横幅

> 开屏、插屏和横幅广告的请求、返回结构类似，不另外举例

### 横幅请求示例

``` json
{
    "device": {
        "ip": "183.95.251.96",
        "ppi": 340,
        "connectiontype": 1,
        "osv": "7.0.0",
        "devicetype": 1,
        "h": "2160",
        "make": "Xiaomi",
        "ext": {
            "imei": "865736033717029",
            "mac": "02:00:00:00:00:00",
            "density": 2.0,
            "orientation": 0,
            "androidid": "b999ed49d1d64664"
        },
        "dnt": 0,
        "ua": "Mozilla/5.0 (Linux; Android 8.0.0; MIX 2 Build/OPR1.170623.027; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/62.0.3202.84 Mobile Safari/537.36",
        "carrier": "46000",
        "w": "1080",
        "model": "MIX2",
        "os": "Android"
    },
    "imp": [
        {
            "instl": 0,
            "tagid": "23448",
            "id": "imp_id",
            "secure": 0
        }
    ],
    "app": {
        "paid": 0,
        "ver": "1.0",
        "id": "30087",
        "bundle": "com",
        "name": "appname"
    },
    "id": "req_id"
}
```

### 横幅广告返回示例（HTML）

```json
{
    "id": "req_id",
    "seatbid": [
        {
            "bid": [
                {
                    "adm": "<meta http-equiv='Content-Type' content='textml charset=UTF-8' /><style type='text/css'>*{padding:0px;margin:0px;} a:link{text-decoration:none;}</style><a target='_blank' href='http://baidu.com'><img src='http://mammut.vlion.cn/ui/assets/img/advimg/300_300.png' width='100%' height='100%' border='0' alt='' /></a>",
                    "cid": "23448_d",
                    "ext": {
                        "ad_icon": "http://c.vlion.cn/ms/tj/dsp/cornermark/arrow-ll-ad.png",
                        "ad_logo": "http://c.vlion.cn/ms/tj/dsp/cornermark/bule/arrow-max-up-a.png",
                        "clk_t": [
                            "http://test.vlion.cn:8045/sc?downx=__CLICK_DOWN_X__&downy=__CLICK_DOWN_Y__&upx=__CLICK_UP_X__&upy=__CLICK_UP_Y__&m=0&e=MTU1NjEwMDMyNQkzMDA4NwkyMzQ0OAkJCXJlcV9pZAkwCQkxCTAJODY1NzM2MDMzNzE3MDI5CQkJCWI5OTllZDQ5ZDFkNjQ2NjQJCQkJCQ==&t=23448&f=0&g="
                        ],
                        "ctype": 1,
                        "imp_t": [
                            "http://test.vlion.cn:8045/se?e=MTU1NjEwMDMyNQkzMDA4NwkyMzQ0OAkJCXJlcV9pZAkwCQkxCTAJODY1NzM2MDMzNzE3MDI5CQkJCWI5OTllZDQ5ZDFkNjQ2NjQJCQkJCQ==&t=23448"
                        ],
                        "instl": 0,
                        "interact_type": 1
                    },
                    "h": 50,
                    "impid": "imp_id",
                    "w": 320
                }
            ]
        }
    ]
}
```

### 横幅广告返回示例（图片）

```json
{
    "id": "req_id",
    "seatbid": [
        {
            "bid": [
                {
                    "adm": "{\"url\":\"http:\\/\\/mammut.vlion.cn\\/ui\\/assets\\/img\\/advimg\\/300_300.png\",\"ldp\":\"http:\\/\\/baidu.com\"}",
                    "cid": "23449_d",
                    "ext": {
                        "ad_icon": "http://c.vlion.cn/ms/tj/dsp/cornermark/arrow-ll-ad.png",
                        "ad_logo": "http://c.vlion.cn/ms/tj/dsp/cornermark/bule/arrow-max-up-a.png",
                        "clk_t": [
                            "http://test.vlion.cn:8045/sc?downx=__CLICK_DOWN_X__&downy=__CLICK_DOWN_Y__&upx=__CLICK_UP_X__&upy=__CLICK_UP_Y__&m=0&e=MTU1NjEwMDQ5NwkzMDA4NwkyMzQ0OQkJCXJlcV9pZAkwCQkxCTAJODY1NzM2MDMzNzE3MDI5CQkJCWI5OTllZDQ5ZDFkNjQ2NjQJCQkJCQ==&t=23449&f=0&g="
                        ],
                        "ctype": 2,
                        "imp_t": [
                            "http://test.vlion.cn:8045/se?e=MTU1NjEwMDQ5NwkzMDA4NwkyMzQ0OQkJCXJlcV9pZAkwCQkxCTAJODY1NzM2MDMzNzE3MDI5CQkJCWI5OTllZDQ5ZDFkNjQ2NjQJCQkJCQ==&t=23449"
                        ],
                        "instl": 0,
                        "interact_type": 0
                    },
                    "h": 50,
                    "impid": "imp_id",
                    "w": 320
                }
            ]
        }
    ]
}
```

### 横幅广告返回示例（图文）

```json
{
    "id": "req_id",
    "seatbid": [
        {
            "bid": [
                {
                    "adm": "{\"url\":\"http:\\/\\/mammut.vlion.cn\\/ui\\/assets\\/img\\/advimg\\/300_300.png\",\"ldp\":\"http:\\/\\/baidu.com\",\"title\":\"testtitle\",\"desc\":\"testdesc\"}",
                    "cid": "23449_d",
                    "ext": {
                        "ad_icon": "http://c.vlion.cn/ms/tj/dsp/cornermark/arrow-ll-ad.png",
                        "ad_logo": "http://c.vlion.cn/ms/tj/dsp/cornermark/bule/arrow-max-up-a.png",
                        "clk_t": [
                            "http://test.vlion.cn:8045/sc?downx=__CLICK_DOWN_X__&downy=__CLICK_DOWN_Y__&upx=__CLICK_UP_X__&upy=__CLICK_UP_Y__&m=0&e=MTU1NjEwMDQ5NwkzMDA4NwkyMzQ0OQkJCXJlcV9pZAkwCQkxCTAJODY1NzM2MDMzNzE3MDI5CQkJCWI5OTllZDQ5ZDFkNjQ2NjQJCQkJCQ==&t=23449&f=0&g="
                        ],
                        "ctype": 2,
                        "imp_t": [
                            "http://test.vlion.cn:8045/se?e=MTU1NjEwMDQ5NwkzMDA4NwkyMzQ0OQkJCXJlcV9pZAkwCQkxCTAJODY1NzM2MDMzNzE3MDI5CQkJCWI5OTllZDQ5ZDFkNjQ2NjQJCQkJCQ==&t=23449"
                        ],
                        "instl": 0,
                        "interact_type": 0
                    },
                    "h": 50,
                    "impid": "imp_id",
                    "w": 320
                }
            ]
        }
    ]
}
```

## 原生

### 原生请求示例

```json
{
    "device": {
        "ip": "183.95.251.96",
        "ppi": 340,
        "connectiontype": 1,
        "osv": "7.0.0",
        "devicetype": 1,
        "h": "2160",
        "make": "Xiaomi",
        "ext": {
            "imei": "865736033717029",
            "mac": "02:00:00:00:00:00",
            "density": 2.0,
            "orientation": 0,
            "androidid": "b999ed49d1d64664"
        },
        "dnt": 0,
        "ua": "Mozilla/5.0 (Linux; Android 8.0.0; MIX 2 Build/OPR1.170623.027; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/62.0.3202.84 Mobile Safari/537.36",
        "carrier": "46000",
        "w": "1080",
        "model": "MIX2",
        "os": "Android"
    },
    "imp": [
        {
            "instl": 3,
            "tagid": "23452",
            "id": "imp_id",
            "secure": 0
        }
    ],
    "app": {
        "paid": 0,
        "ver": "1.0",
        "id": "30087",
        "bundle": "com",
        "name": "appname"
    },
    "id": "req_id"
}
```

### 原生广告返回示例

```json
{
    "id": "req_id",
    "seatbid": [
        {
            "bid": [
                {
                    "adm": "{\"desc\":\"测试描述\",\"ldp\":\"http:\\/\\/baidu.com\",\"title\":\"测试标题\",\"img\":[{\"url\":\"http:\\/\\/mammut.vlion.cn\\/ui\\/assets\\/img\\/advimg\\/300_300.png\",\"h\":300,\"w\":600}],\"icon\":{\"url\":\"http:\\/\\/mammut.vlion.cn\\/ui\\/assets\\/img\\/advimg\\/300_300.png\",\"h\":75,\"w\":75}}",
                    "cid": "23452_d",
                    "ext": {
                        "ad_icon": "http://c.vlion.cn/ms/tj/dsp/cornermark/arrow-ll-ad.png",
                        "ad_logo": "http://c.vlion.cn/ms/tj/dsp/cornermark/bule/arrow-max-up-a.png",
                        "clk_t": [
                            "http://test.vlion.cn:8045/sc?downx=__CLICK_DOWN_X__&downy=__CLICK_DOWN_Y__&upx=__CLICK_UP_X__&upy=__CLICK_UP_Y__&m=0&e=MTU1NjEwMTA3NwkzMDA4NwkyMzQ1MgkJCXJlcV9pZAkwCQkxCTAJODY1NzM2MDMzNzE3MDI5CQkJCWI5OTllZDQ5ZDFkNjQ2NjQJCQkJCQ==&t=23452&f=0&g="
                        ],
                        "imp_t": [
                            "http://test.vlion.cn:8045/se?e=MTU1NjEwMTA3NwkzMDA4NwkyMzQ1MgkJCXJlcV9pZAkwCQkxCTAJODY1NzM2MDMzNzE3MDI5CQkJCWI5OTllZDQ5ZDFkNjQ2NjQJCQkJCQ==&t=23452"
                        ],
                        "instl": 3
                    },
                    "impid": "imp_id"
                }
            ]
        }
    ]
}
```