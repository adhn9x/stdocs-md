# Get Original App Link Detail

# API Description

Use this API to retrieve the app link details by passing in the generated short URL of the target app link.

**Request Method**: `GET`**End Point**: https://openapi.seatalk.io/link/app/origin\_url

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|

**Parameter**

|Parameter|Type|Mandatory|Max Length|Description|Default|Sample|
|---|---|---|---|---|---|---|
|short\_url|string|Yes|N/A|The generated app link short URL|N/A|" https://link.seatalk.io/v4/1/s/1zyRYQ0000000001R185 "|

**Request Sample**

```markup
GET https://openapi.seatalk.io/open/link/app/origin_url?short_url=https://link.test.seatalk.io/v4/1/s/1zyRYQ0000000001R185 Copy
```

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|message|string|- The error message - Return empty if the request is successful|
|mobile\_data|object|The information about the mobile target app page|
|∟app\_type|string|The type of mobile link. Can be "WEB" or "RN"|
|∟path|string|The path of the RN App link, or the full URL of the web app URL|
|∟params|object|The parameters passed along with the app link path|
|desktop\_data|object|The information about the desktop target app page|
|∟app\_type|string|The type of desktop link. Currently only "WEB" is supported|
|∟path|string|The full URL of the web app URL|
|∟params|object|The parameters passed along with the app link path|
|fallback\_url|string|The address of the fallback page if the provided path becomes invalid or unavailable|

**Response Sample**

```json
{
  "code": 0,
  "app_id": "XXXXXXXXXXXXXXXX",
  "mobile_data": {
    "app_type": "RN",
    "path": "/rn/path",
    "params": {
      "a": "1",
      "b": "1662221913"
    }
  },
  "desktop_data": {
    "app_type": "WEB",
    "path": "https://yourwebapp.com/path",
    "params": {
      "a": "1"
    }
  },
  "fallback_url": "https://baidu.com"
} Copy
```

Was this document helpful?

No

Yes