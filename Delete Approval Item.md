# Delete Approval Item

# API Description

Use this API to delete an existing approval item in approval center server.

Note:

* This API requires **Delete Approval Item** permission

**Request Method**: `POST`

**End Point**: https://openapi.seatalk.io/approval\_center/v2/delete

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

**Parameter**

|Parameter|Type|Mandatory|Max Length|Description|Default|Sample|
|---|---|---|---|---|---|---|
|item\_id|string|Yes|30 char|The ID of the approval item|N/A|202101|

**Request Sample**

```json
{
    "item_id": "202101"
} Copy
```

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|

**Response Sample**

```json
{
    "code": 0
} Copy
```

Was this document helpful?

No

Yes