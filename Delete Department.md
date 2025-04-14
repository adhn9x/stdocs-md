# Delete Department

# API Description

Use this API to delete a department in your organization.

Note:

1. This API requires **Create, Update, and Delete a Department** permission
2. To successfully delete a department, make sure **there is no employee** under that department

**Request Method**:`POST`

**End Point**:[https://openapi.seatalk.io/oa\_sync/departments/delete](https://openapi.seatalk.io/oa_sync/departments/delete)

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Content-Type|string|Yes|||application/json|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|

**Parameter**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|department\_code|string|Yes|The department code of the very department to be deleted|||

# Response Parameter

**Body(JSON)**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code|
|rid|string|Request id|
|oa\_result|OAResult|Error reason|

**OAResult**

|Parameters|Type|Description|
|---|---|---|
|oa\_error|int|OA ErrCode|
|oa\_message|string|Error reason|

Was this document helpful?

No

Yes