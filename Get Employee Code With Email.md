# Get Employee Code With Email

# API Description

Use this API to exchange a user's email for employee\_code. Employees with all types of employee statuses can be queried (i.e., pending, in position, leaving and terminated).

If there is more than one employee with the same email, all their information will be returned. You can use the "employee\_status" field in the response to differentiate between employees under different statuses. Because there might be more than one employee\_code returned that points to one email, the exact ordering of the employee objects in the response might differ from the ordering of the emails passed in.

Note:

* This API requires **Get Employee Code with Email** permission.
* The "employee\_status" field in the response is not supported in v1 of this API.

**Request Method**: `POST`

**End Point**: https://openapi.seatalk.io/contacts/v2/get\_employee\_code\_with\_email

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

**Body**

|Parameter|Type|Mandatory|Description|Default|Size Limit|Sample|
|---|---|---|---|---|---|---|
|emails|\[\]string|Yes|A list of employees' emails that are used to exchange for their employee\_code|N/A|Maximum: 500|"morgan.jackman@example.email.com" , "hong.wang@example.email.com", "bowen.huai@example.email.com"|

**Request Body Sample**

```json
{
    "emails": [
        "morgan.jackman@example.email.com",
        "hong.wang@example.email.com",
        "bowen.huai@example.email.com"
    ]
} Copy
```

# Response Parameter

**Result Fields**

|Parameter|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|employees|\[\]object|A list of employees|
|∟code|int|0: success 3000: user not found with the current email|
|∟email|string|Email of the employee|
|∟employee\_code|string|The employee\_code if the user with the current email exists Null if the user is not an employee of the current organisation|
|∟employee\_status|int|The status of the employee if a user with the email exists 0: the employee is not found 1: pending 2: in position 3: leaving 4: terminated|

**Response Sample**

```json
{
    "code": 0,
    "employees": [
        {
            "code": 0,
            "email": "morgan.jackman@example.email.com",
            "employee_code": "9120",
            "employee_status": 2
        },
        {
            "code": 0,
            "email": "morgan.jackman@example.email.com",
            "employee_code": "1234",
            "employee_status": 4
        },
        {
            "code": 0,
            "email": "hong.wang@example.email.com",
            "employee_code": "3871",
            "employee_status": 2
        },
        {
            "code": 3000,
            "email": "bowen.huai@example.email.com",
            "employee_code": null,
            "employee_status": 0
        }
    ]
} Copy
```

Was this document helpful?

No

Yes