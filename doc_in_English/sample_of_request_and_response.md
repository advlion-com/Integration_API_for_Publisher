# Sample of ad request and response



- avaible appid and tagid for testing:

> | tagid | appid | os | adtype | creative type | interact_type |
> | --- | --- | --- | --- | --- | --- |
> | 23448 | 30087 | Android | banner | html | view |
> | 23449 | 30087 | Android | banner | image | view |
> | 23450 | 30087 | Android | banner | image | download |
> | 23452 | 30087 | Android | native | - | view |
> | 23453 | 30087 | Android | native | - | download |
> | 23454 | 30087 | Android | splash | html | view |
> | 23457 | 30087 | Android | splash | image | view |
> | 23458 | 30087 | Android | splash | image | download |
> | 23459 | 30087 | Android | interstitial | html | view |
> | 23461 | 30087 | Android | interstitial | image | view |
> | 23462 | 30087 | Android | interstitial | image | download |
> | 23463 | 30088 | iOS | 横幅 | html | view |
> | 23465 | 30088 | iOS | 横幅 | image | view |
> | 23466 | 30088 | iOS | 横幅 | image | download |
> | 23467 | 30088 | iOS | native | - | view |
> | 23468 | 30088 | iOS | native | - | download |
> | 23469 | 30088 | iOS | splash | html | view |
> | 23471 | 30088 | iOS | splash | image | view |
> | 23472 | 30088 | iOS | splash | image | download |
> | 23473 | 30088 | iOS | interstitial | html | view |
> | 23475 | 30088 | iOS | interstitial | image | view |
> | 23476 | 30088 | iOS | interstitial | image | download |

> - Please notive that ad response which get from test id above is for testing only. 

## banner

> Ad request and ad response of splash and interstitial is similar to banner. 

### ad request sample of banner

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

### ad respnose sample of banner(html)

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

### ad respnose sample of banner(image)

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

### ad respnose sample of banner(image and text)

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

## native

### ad request sample of native

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

### ad response of native

```json
{
    "id": "req_id",
    "seatbid": [
        {
            "bid": [
                {
                    "adm": "{\"desc\":\"testdesc\",\"ldp\":\"http:\\/\\/baidu.com\",\"title\":\"testtitle\",\"img\":[{\"url\":\"http:\\/\\/mammut.vlion.cn\\/ui\\/assets\\/img\\/advimg\\/300_300.png\",\"h\":300,\"w\":600}],\"icon\":{\"url\":\"http:\\/\\/mammut.vlion.cn\\/ui\\/assets\\/img\\/advimg\\/300_300.png\",\"h\":75,\"w\":75}}",
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