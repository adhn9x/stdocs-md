# Delete Employee

# API Description

Use this API to Delete an employee in your organization.

This API requires**Onboard/Update/Offboard/Reboard/Delete Employee** permission.

**Request Method**:`POST`

**End Point**: https://openapi.seatalk.io/oa\_sync/employees/delete

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Sample|
|---|---|---|---|---|
|Authorization|string|Yes|obtained through the Get App Access Token API|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|application/json|

**Body**

|Parameter|Type|Mandatory|Length|Description|Sample|
|---|---|---|---|---|---|
|employee\_code|string|Yes|50|the employee code of the employee to be deleted, one employee processed by each call|F8DJFDSA|

**Request Sample**

```json
{
    "employee_code":"12345"
} Copy
```

# Response

**Body**

|Fields|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|message|string|- The error message - Return an empty string if the request is successful|
|rid|string|request id|

**Error Case**

|#|Error|Description|
|---|---|---|
|1|The employee is a dept group chat owner|Error Code: 6000 Error Msg: Request is rejected. The employee is still a dept group chat owner.|
|2|The employee is not found|Error Code: 3001 Error Msg: Request is rejected. The employee is not found.|

**Response Sample**

```json
{
    "code": 0
} Copy
```

Was this document helpful?

No

Yes