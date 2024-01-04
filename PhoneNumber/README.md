# Requests order

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
