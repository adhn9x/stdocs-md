# Get Departments

# API Description

Use this API to obtain a list of departments including the department ID, name, parent department ID, and other related information.

Note:

* This API requires**Get Department List**permission and the relevant**Data Scope**.

**Request Method**:`GET`

**End Point**: https://openapi.seatalk.io/contacts/v2/departments

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|

**Parameter**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|department\_code|string|No|- The department\_code - If not specified, the result will return all departments that are accessible to the app|N/A|dep123|
|fetch\_child|int|No|0: fetch the current department only 1: fetch the current department and its direct child departments 2: fetch the current department and its all sub-departments|N/A|0|
|page\_size|int|No|Number of items included in one response, must be an integer between 1 - 100 (inclusive)|50|50|
|cursor|string|No|Cursor info from previous request. It is not filled in the first request. Use this info to indicate where to start traversal; The next "cursor" will be returned in the response of current request|N/A|gmrdPA7cyZP2qGJkM-hatoA7SySeNmOlDyv8x1p9K0pxvJPxs\_qL5Y2OL2-Dkoq1VH\_FtDccHq5GrpzuMK4pyw==|

**Request Sample**

```javascript
https://openapi.seatalk.io/contacts/v2/departments?department_code=123&fetch_child=0 Copy
```

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|departments|\[\]object|A list of departments|
|∟department\_code|string|The unique identifier of the department|
|∟name|string|The name of this department|
|∟alias|string|The department alias|
|∟lead\_employee\_code|string|The employee\_code of this department's head|
|∟lead\_employee\_email|string|The email of this department's head|
|∟visibility\_info|object|The visibility info of this department|
|∟is\_hidden|bool|True if this department is hidden in the organization|
|∟hide\_type|int|0: visible to sub-departments 1: visible to the specified department whitelist|
|∟department\_whitelist|\[\]string||
|∟direct\_employee\_count|int|The number of employees directly under this department|
|∟parent\_department\_code|string|- The parent department's department\_code - 0 if there is no parent or the parent is beyond the app's server API data scope|
|snapshot\_timestamp|int|Timestamp when our server receive the first request related to current request chain. You can use it to identify a set of chained requests|
|next\_cursor|string|Cursor info for the next request. Put it in the "cursor" field in the next request. Each cursor will be valid for 30 mins. If the cursor is empty, it means there is no next request to be called|

**Response Sample**

```json
{
    "code": 0,
    "departments": [
        {
            "department_code": "12",
            "name": "Human Resource",
            "department_alias": "",
            "lead_employee_code": "998",
            "lead_employee_email": "sample1@seatalk.biz",
            "visibility_info": [
                {
                    "is_hidden": false,
                    "hide_type": 0,
                    "department_whitelist": [
                        "20",
                        "21"
                    ]
                }
            ],
            "direct_employee_count": 15,
            "parent_department_code": "10"
        },
        {
            "department_code": "13",
            "name": "Marketing",
            "department_alias": "",
            "lead_employee_code": "102",
            "lead_employee_email": "sample2@seatalk.biz",
            "visibility_info": [
                {
                    "is_hidden": false,
                    "hide_type": 0,
                    "department_whitelist": [
                        "30",
                        "40"
                    ]
                }
            ],
            "direct_employee_count": 6,
            "parent_department_code": "10"
        }
    ],
    "snapshot_timestamp": 1663120230,
    "next_cursor": "2MRrNpKbirXAte2pgZoJETWK10pqQZtEOzJH2kx3BhFWOS_h58ry1Y8jSOim5vgh5QQpF-SKsemiA4HL5G7_7w=="
} Copy
```

Was this document helpful?

No

Yes