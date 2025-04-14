# Update Employee Avatar

# API Description

Use this API to update an existing employee's avatar.

Note:

* This API requires**Update Employee Avatar**permission

**Request Method**: `POST`

**End Point**: https://openapi.seatalk.io/oa\_sync/employees/update\_avatar

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|"multipart/form-data; boundary=auto calculated"|

**Body**

|Parameter|Type|Mandatory|Description|Size/Length Limit|
|---|---|---|---|---|
|employee\_code|string|Yes|The employee's employee\_code|Max: 30 characters|
|avatar\_image|Binary|Yes|- The image of the employee's new avatar - Must be a JEPG, PNG, JPG file - SeaTalk Open Platform will crop out a square in the middle of the image and compress the square image's size to less than 400\*400 px|Max: 1 MB|

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|message|string|- Error Message - Return the empty string if the request is successful|
|rid|string|The request ID|

**Response Sample**

```json
{
    "code": 0,
    "message": "",
    "rid": "bb10b5e3-8ca2-4f6b-abd0-b1d6f9d2b712"
} Copy
```

Was this document helpful?

No

Yes