# Generate an App Link

# API Description

Use this API to generate a short URL for an app link of your app.

Note:

* An app can generate up to 100k permanent app links.
* An app can generate up to 500k short-term app links every day.

**Request Method**: `POST`

**End Point**: https://openapi.seatalk.io/link/app/short\_url

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|

**Body**

|Parameter|Type|Mandatory|Max Length|Description|Default|Sample|
|---|---|---|---|---|---|---|
|lifecycle|int|Yes|N/A|The time period during which the app link is valid - 0: short-term. Available for 90 days upon generation - 1: permanent|N/A|"1"|
|mobile\_data|object|No|N/A|The path and query of the app page on the mobile client|""||
|∟app\_type|string|Yes|N/A|The app type on the mobile client: "RN" or "WEB"|""|" RN "|
|∟path|string|No|256 chars|The mobile app address of the target app page|""|" /page/mobile/new"|
|∟params|object|No|256 chars|The parameters of the target app page|""|{" page\_number": "1002"}|
|desktop\_data|object|No|N/A|The path and query of the app page on the desktop client|""||
|∟app\_type|string|Yes|N/A|The app type on the desktop client: "WEB"|""|"WEB"|
|∟path|string|No|256 chars|The desktop app address of the target app page|""|" /page/web/new"|
|∟params|object|No|256 chars|The parameters of the target app page|""|{" page\_number": "1002"}|
|fallback\_url|string|No|512 chars|The address of the fallback page if the provided path becomes invalid or unavailable|""|" https://google.com/ "|

**Request Sample**

```json
{
  "lifecycle": 0,
  "mobile_data": {
    "app_type": "RN",
    "path": "page/rn/new",
    "params": {
      "a": "1",
      "b": "1662221913"
    }
  },
  "desktop_data": {
    "app_type": "WEB",
    "path": "/page/web/new",
    "params": {
      "a": "1",
      "b": "211"
    }
  },
  "fallback_url": "https://www.baidu.com"
} Copy
```

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|message|string|- The error message - Return empty if the request is successful|
|short\_url|string|The generated short URL of the target app link|

**Response Sample**

```json
{
  "code": 0,
  "short_url": "https://link.seatalk.io/v4/1/s/1zyRYQ0000000001R185"
} Copy
```

Was this document helpful?

No

Yes