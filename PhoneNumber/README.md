# Requesting code requests order

Essential
1. https://m.shein.com/roe/api/auth/phoneValidate/get?_ver=1.1.8&_lang=en

(this one initiates the phone number adding or change)

Request body :
```json
{"alias_type":2,"alias":"489921018","area_code":"61","area_abbr":"AU"}
```
The Response is always 
```json
{"code":0}
```

2. https://m.shein.com/roe/api/risk/geetest/reset.php

(a post request with encrypted values)

The Response:
```json
{
    "status": 0,
    "data": {
        "challenge": "991b0573245f0e03950a5a8ad9ad1a6a",
        "api_server": "https://m.shein.com/roe/api/risk/geetest/"
    }
}
```

3. https://m.shein.com/roe/api/risk/geetest/ajax.php

(a post request with encrypted values)

The Response:
```json
{
    "status": 0,
    "data": {
        "risk": false,
        "result": "success",
        "sub_type": "click"
    },
    "token": ""
}
```
4. https://m.shein.com/roe/api/risk/geetest/get.php

(a post request with encrypted values)

The Response:
```json
{
    "status": 0,
    "data": {
        "cid": "032a4d124dd9598cb268400caaa2394a",
        "challenge": "991b0573245f0e03950a5a8ad9ad1a6a",
        "spec": "1*1",
        "sign": "",
        "pic": "/www/assests/30/click/icon/ff7d4bd057c1e253ce68c7b8a15c62f7.jpg",
        "pic_type": "icon",
        "num": 0,
        "static_servers": [
            "https://sheinsz.ltwebstatic.com/she_dist/libs/geetest"
        ],
        "css": "www/css/silver/style.1.0.0.css",
        "aspect_radio": {
            "voice": 128,
            "click": 128,
            "slide": 103
        },
        "logo": false,
        "feedback": "",
        "show_voice": true,
        "i18n_labels": {
            "refresh": "Refresh",
            "cancel": "Cancel",
            "close": "Close",
            "commit": "OK",
            "fail_short": "Please try again",
            "voice": "Vision Impaired",
            "tip": "Select in _this order_:",
            "forbidden": "Try again in 3 seconds",
            "success": "You passed! You beat %s%% of users.",
            "fail": "Please try again",
            "feedback": "More info",
            "small_tip": "Please choose all the:",
            "loading": "Loading",
            "read_reversed": false,
            "success_short": "You passed",
            "logo": ""
        },
        "image_static": [
            "http://shein.ltwebstatic.com"
        ],
        "api_server": "https://m.shein.com/roe/api/risk/geetest/"
    }
}
```
