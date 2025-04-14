# Deprecated Soon - Get Bot Subscriber List

**Since February 6, 2025, the bot subscription logic has been removed. This API will also be deprecated soon. We recommend using alternative logic to achieve your goal.**

# API Description

Obtain the subscriber list of the app's bot, including the current subscribers.

Note:

* To call this API, your app must enable the**bot capability** and have an**Online** status. See more at<u>[Quickly build a Bot](https://open.seatalk.io/docs/quickly-build-a-bot)</u>.
* This API requires**Get Bot Subscriber List** permission

**Request Method**:`GET`

**End Point**: https://openapi.seatalk.io/messaging/v2/get\_bot\_subscriber\_list

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|

**Parameter**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|page\_size|int|No|Number of items included in one response, must be an integer between 1 - 100 (inclusive)|50|50|
|cursor|string|No|Cursor info from previous request. It is not filled in the first request. Use this info to indicate where to start traversal; The next "cursor" will be returned in the response of current request|N/A|N/A|

**Request Sample**

```bash
https://openapi.seatalk.io/messaging/v2/get_bot_subscriber_list?page_size=10&cursor=xxxxx Copy
```

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|the general error code|
|next\_cursor|string|cursor info for the next request. Put it in the "cursor" field in the next request. If the cursor is empty, it means there is no next request to be called.|
|subscribers|object|a list of subscribers|
|∟employee\_code|\[\]string|the employee\_code of the subscribers|

**Response Sample**

```json
{
    "code":0,
    "next_cursor":"",
    "subscribers":{
        "employee_code":[
            "e_12345678"
        ]
    }
} Copy
```

Was this document helpful?

No

Yes