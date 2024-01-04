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
# Solving The captcha

1. https://m.shein.com/roe/api/risk/geetest/ajax.php

 (a post request with encrypted values)

The Response:
```json
{"status":0,"data":{"result":"success","score":"38"},"token":""}
```

# The Final Request code Request 

1. https://m.shein.com/roe/api/auth/sendUicsCode/get?_ver=1.1.8&_lang=en

Request body :
```json
{"alias_type":2,"alias":"489921018","scene":"bind_msg_verify","third_party_type":8,"area_code":"61","area_abbr":"AU","verification_abt":"new","challenge":"a2fc1f8456bff4930933383ec6981c1c","gtRisk":"","blackbox":"","risk_id":"a8dca359-251b-404b-a306-0a75d53c75fe","risk_scene":"send_message","isGeetest":true}
```
The Response:
```json
{"code":"0","msg":"OK","info":{"is_send":1,"ttl":60}}
```
The verify code valid within 10 minutes

# Confirm Code Shows a second captcha 

1. reset 
2. ajax.php
3. get.php
then the final request with the solved captcha answer
4. ajax.php

# Then the final confirm number with code request

1. https://m.shein.com/roe/api/auth/aliasBind/update?_ver=1.1.8&_lang=en

Request body :
```json
{"alias_type":2,"alias":"489921018","verification_code":"540045","area_code":"61","area_abbr":"AU","verify_qa":0,"bind_type":1,"force_bind":0,"bind_scene":"personalcenter","verify_switch":0,"daId":"2-8-22","verification_abt":"new","challenge":"eae8c1a5552259195cb0abb47c510e14","gtRisk":""}
```
