# Get Department Employees

# API Description

Use this API to obtain employee list under specific departments. The result includes basic information of existing employees.

Note:

* This API requires**Get Department Employees**permission and the relevant**Data Scope**.

**Request Method**: `GET`

**End Point**: <u>[https://openapi.seatalk.io/](https://openapi.seatalk.io/messaging/v2/group_chat)contacts/v2/department/employees</u>

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

**Parameter**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|department\_code|string|Yes|The department code|N/A|"abcdef"|
|fetch\_child (Discarded)|boolean|No|This field has been discarded.|false||
|page\_size|int|No|page\_size defines the number of items included in one response for each list. It must be an integer between 1-100 (inclusive).|50|50|
|cursor|string|No|Cursor info from previous request. It is not filled in the first request. Use this info to indicate where to start traversal; The next "cursor" will be returned in the response of current request|N/A|gmrdPA7cyZP2qGJkM-hatoA7SySeNmOlDyv8x1p9K0pxvJPxs\_qL5Y2OL2-Dkoq1VH\_FtDccHq5GrpzuMK4pyw==|

**Request Sample**

```javascript
https://openapi.seatalk.io/contacts/v2/department/employees?department_code=abcdef Copy
```

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|employees|\[\]object|A list of employees|
|∟employee\_code|string|The employee\_code of the employee|
|∟name|string|The name of the employee|
|∟seatalk\_id|string|The SeaTalk ID of the employee|
|∟departments|\[\]string|The departments the employee are under|
|∟email|string|The email of the employee|
|snapshot\_timestamp|int|Timestamp when our server receive the first request related to current request chain. You can use it to identify a set of chained requests|
|next\_cursor|string|Cursor info for the next request. Put it in the "cursor" field in the next request. Each cursor will be valid for 30 mins. If the cursor is empty, it means there is no next request to be called|

**Response Sample**

```json
{
    "code": 0,
    "employees": [
        {
            "employee_code": "9120",
            "name": "Morgan Jackman",
            "seatalk_id": "9851840192",
            "departments": [
                "12",
                "13"
            ],
            "email": "morgan.jackman@seatalk.biz",
        },
        {
            "employee_code": "3871",
            "name": "Hong Wang",
            "seatalk_id": "7819002318",
            "departments": [
                "2"
            ],
            "email": "hong.wang@seatalk.biz",
        }
    ],
    "snapshot_timestamp": 1632912334,
    "next_cursor": "gmrdPA7cyZP2qGJkM-hatoA7SySeNmOlDyv8x1p9K0pxvJPxs_qL5Y2OL2-Dkoq1VH_FtDccHq5GrpzuMK4pyw=="
} Copy
```

Was this document helpful?

No

Yes