# Create Department

# API Description

Use this API to create a new department in your organization.

Note:

* This API requires **Create, Update, and Delete a Department** permission

**Request Method**:`POST`

**End Point**:[https://openapi.seatalk.io/oa\_sync/departments/create](https://openapi.seatalk.io/oa_sync/departments/create)

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

**Body (JSON)**

|Parameter|Type|Mandatory|Size Limit|Description|Default|Sample|
|---|---|---|---|---|---|---|
|departments|\[\]Department|Yes||A list of Departments|N/A||

**Department**

|Parameter|Type|Mandatory|Size Limit|Description|Default|Sample|
|---|---|---|---|---|---|---|
|department\_name|string|Yes||The department name|||
|department\_code|string|No|128 Characters|- The optional field for the new department's department\_code - If no value is given, SeaTalk will generate a random value for the department as its department\_code|||
|department\_alias|string|No|128 Characters|The optional field for the new department's alias|||
|parent\_department|string|Yes||The department code of the parent department of this new department|||
|visibility|int|||0: visible to only its sub-departments 1: visible to the specified department whitelist|||
|department\_lead|string|||The employee\_code of the department leader|||
|visible\_to\_departments|string\[\]|||- A list of department\_code of departments to which the new department is visible - Must be passed in if "visibility" is 1|||

# Response Parameter

**Body (JSON)**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|message|string|Error Message|
|rid|string|R equest id|
|result|DepartmentOperationResults|Operation result|

**DepartmentOperationResults**

|Parameters|Type|Description|
|---|---|---|
|departments|\[\]DepartmentOperationResult|The operation results|
|total\_num|int|The total number of departments in the request|
|success\_num|int|The total number of successfully created departments in the request|
|fail\_num|int|The total number of failed departments in the request|

**DepartmentOperationResult**

|Parameters|Type|Description|
|---|---|---|
|department\_code|string|The OA ErrCode|
|error|int|0: success|
|error\_message|string|The error message|

Was this document helpful?

No

Yes