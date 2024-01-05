# Requesting code requests order
Notes : the get.php gets the captcha image 
 

https://github.com/minanagehsalalma/ATO/assets/20546638/9e21f91b-5598-4f62-bc07-b007a2b7cf50



1. https://m.shein.com/roe/api/auth/phoneValidate/get?_ver=1.1.8&_lang=en

(this request just checks if a phone number is a vaild number or not as soon as you type it, it can be skipped)

Request body :
```json
{"alias_type":2,"alias":"489921018","area_code":"61","area_abbr":"AU"}
```
The Response is always (if the phone number is correct)
```json
{"code":0}
```
if the number is an invalid number
```json
{"code":-410,"msg":"Invalid phone number"}
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
# Full order from start to finish 

1. api/auth/phoneValidate/  (can be skipped)

* Requesting First Captcha
2. reset.php
3. ajax.php
4. get.php

* Sending First Captcha Solution
5. ajax.php

* Finally Actually Requesting a verify code
6. api/auth/sendUicsCode

* Confirming the code shows another Captcha
7. reset.php
8. ajax.php
9. get.php

* Sending Second Captcha Solution

10. ajax.php

* The Final Request
11. api/auth/aliasBind/update
