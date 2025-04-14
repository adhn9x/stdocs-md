# Update Department

# API Description

Use this API to update an existing department in your organization.

Note:

* This API requires **Create, Update, and Delete a Department** permission

**Request Method**:`POST`

**End Point**:[https://openapi.seatalk.io/oa\_sync/departments/update](https://openapi.seatalk.io/oa_sync/departments/update)

# Request Parameter

### Header

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Content-Type|string|Yes|||application/json|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|

**Body(JSON)**

|Parameter|Type|Mandatory|Size Limit|Description|Default|Sample|
|---|---|---|---|---|---|---|
|departments|\[\]Department|Yes|Maximum: 10|A list of Departments|||

**Type Department**

|Parameter|Type|Mandatory|Size Limit|Description|Default|Sample|
|---|---|---|---|---|---|---|
|department\_code|string|Yes||The department\_code of the department to update|||
|department\_name|string|No||The new department name|||
|department\_alias|string|No|128 Characters|The optional field for a department alias|||
|parent\_department|string|No||The department\_code of its parent department|||
|visibility|int|No||0: visible to only its sub-departments 1: visible to the specified department whitelist|||
|department\_lead|string|No||The employee\_code of the department lead|||
|visible\_to\_departments|string|No||- A list of department\_code of departments to which the new department is visible - Must be passed in if "visibility" is 1|||

# Response Parameter

**Body (JSON)**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|message|string|The error message if the request has failed|
|rid|string|The R equest ID|
|update\_result|DepartmentOperationResults|The operation result|

**Type** **DepartmentOperationResults**

|Parameters|Type|Description|
|---|---|---|
|departments|\[\]DepartmentOperationResult|The operation results|
|total\_num|int|The total number of departments in the request|
|success\_num|int|The total number of successfully created departments in the request|
|fail\_num|int|Total number of failed departments in the request|

**Type** **DepartmentOperationResult**

|Parameters|Type|Description|
|---|---|---|
|department\_code|string|The OA ErrCode|
|error|int|0: success|
|error\_message|string|The error message|

Was this document helpful?

No

Yes