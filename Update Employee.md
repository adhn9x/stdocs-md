# Update Employee

# API Description

Use this API to update an existing employee's information in your organization.

Note:

* This API requires**Onboard/Update/Re-board Employee** permission and the relevant**Data Scope**.
* If some fields are not passed in inside a request, they won't get updated. SeaTalk will only update fields that are passed in.

**Request Method**: `POST`

**End Point**: https://openapi.seatalk.io/oa\_sync/employees/update

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

**Body**

|Parameter|Type|Mandatory|Max Length|
|---|---|---|---|
|employees|\[\]UpdateEmployeeParam|Yes|50|

**UpdateEmployeeParam**

|Parameter|Type|Mandatory|Max Length|Description|Default|Sample|
|---|---|---|---|---|---|---|
|employee\_code|string|Yes|30 char|- The unique Identifier of the employee in the organization - It must belong to an existing employee|N/A|"202101"|
|name|string|No|100 char|The name of the employee|N/A||
|hand\_phone|string|No|100 char|- The phone number of the employee - Must be in a valid phone number format and unique within the organization|N/A||
|company\_email|string|No|100 char|- The company email of the employee - Must be in a valid email format and unique within the organization|N/A||
|personal\_email|string|No|100 char|- The personal email of the employee - Must be in a valid email format|N/A||
|department\_code|string|No|255 char|- The department this employee belongs to - Must be a valid department\_code within the organization|N/A||
|report\_to|string|No|255 char|- The employee\_code of the reporting manager - Must be a valid employee\_code within the organization|N/A||
|birth\_date|string|No|100 char|- The date of birth of the employee - Must be in a valid date format: "YYYY-MM-DD" or "MM-DD"|N/A||
|board\_date|string|No|N/A|- The onboarding date - Must be valid date format: "YYYY-MM-DD"|N/A||
|probation\_end\_date|string|No|N/A|- The end date of this employee's probation - Must be valid date format: "YYYY-MM-DD" - Must be later than the employee's board\_date|N/A||
|gender|int|No|N/A|1: Male 2: Female 3: Others|N/A||
|martial\_status|int|No|N/A|1: Single 2: Married 3: Divorced 4: Widowed 5: Others|N/A||
|address|string|No|255 char|The address of the employee|N/A||
|employment\_type|int|No|N/A|1: Full-time 2: Part-time 3: Shift work 4: Contractor 5: Internship 6: Others|N/A||
|number\_of\_children|int|No|N/A|The number of children the current employee has|N/A||
|job\_title|string|No|255 char|- The employee's job title - Must correspond to one of the Job Titles set in the current organization's OA system|N/A||
|office|string|No|255 char|- The employee's office - Must correspond to one of the Offices set in the current organization's OA system|N/A||
|payroll\_company|string|No|255 char|- The employee's payroll company - Must correspond to one of the Payroll Companys set in the current organization's OA system|N/A||
|rank|string|No|255 char|- The employee's rank - Must correspond to one of the Ranks set in the current organization's OA system|N/A||

**Request Sample**

```json
{
    "employees": [
        {
            "employee_code": "e_pfu5zya3",
            "office": "Shanghai",
            "payroll_company": "sea limited"
        },
        {
            "employee_code": "e_226n0tn6",
            "office": "Guangzhou",
            "payroll_company": "sea limited"
        }
    ]
} Copy
```

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|message|string|- The error message - Return empty string if the request is successful|
|rid|string|The request ID|
|update\_result|UpdateEmployeeResult|The update request result|

**UpdateEmployeeResult**

|Parameters|Type|Description|
|---|---|---|
|employees|\[\]Employee|A list of employees|
|total\_num|int|The total number of employees in this request|
|success\_num|int|The number of successfully updated employees in this request|
|error\_num|int|The Number of employees that haven't been updated successfully in this request|

**Employee**

|Parameters|Type|Description|
|---|---|---|
|email|string|The email of the target employee|
|employee\_code|string|The employee\_code of this employee|
|error|string|- Error message for this employee if he/she hasn't been updated successfully - Empty if success|
|error\_code|string|- Error code for this employee's onboarding request - 0 if success|

**Response Sample**

```json
{
    "code": 0,
    "message": "",
    "rid": "bb10b5e3-8ca2-4f6b-abd0-b1d6f9d2b712",
    "update_result": {
        "employees": [
            {
                "email": "",
                "employee_code": "e_pfu5zya3",
                "error": "",
                "error_code": 0
            },
            {
                "email": "",
                "employee_code": "e_226n0tn6",
                "error": "",
                "error_code": 0
            }
        ],
        "total_num": 2,
        "success_num": 2,
        "error_num": 0
    }
} Copy
```

Was this document helpful?

No

Yes