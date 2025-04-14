# Export Admin Audit Logs

# API Description

> This API is only available for selected organizations

Use this API to obtain the logs of all admin actions performed on the SeaTalk Admin Portal for the organization that your app is in. Logs have a retention period of 12 months. Thereafter, they will be deleted and can no longer be accessed.

There are 4 types of actions: CREATE, READ, UPDATE and DELETE. Each action will be recorded as a single log, and the details of the action taken will be returned in the **description** field of the log object. For more details on these descriptions, please refer to the Descriptions Summary section of this doc.

**Request Method:** `POST`

**End Point:**[https://openapi.seatalk.io/governance/admin\_logs](https://openapi.seatalk.io/governance/admin_logs)

# Request Parameters

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|From Get App Access Token|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

**Parameters**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|start\_time|int64|No|Start timestamp for the logs, UNIX format timestamp|12 months before the current time, UNIX format timestamp|1632912334|
|end\_time|int64|No|End timestamp for the logs, UNIX format timestamp|Current time, UNIX format timestamp|1632912334|
|subcategory|list\[str\]|No|Filter logs by where the action was taken "organization\_department" "organization\_employee" "governance\_trusted\_device" "governance\_data\_loss\_prevention" "governance\_chat\_access\_permissions" "governance\_audit\_logs" "settings\_general" "settings\_access\_control" Multiple subcategories can be specified. If not specified, logs matching all subcategories will be retrieved.|N/A|\["organization\_employee", "settings\_general"\]|
|employee\_code|string|No|The employee code of the user who performed an action. If not specified, logs matching all employee codes will be retrieved.|N/A|e\_b75a58b4|
|page\_size|int|No|Number of logs to be included in one API call. Must be an integer from 1-100 (inclusive).|50|50|
|cursor|string|No|Cursor info from previous request. It is not filled in the first request. Use this info to indicate where to start traversal; The next "cursor" will be returned in the response of current request|N/A|gmrdPA7cyZP2qGJkM-hatoA7SySeNmOlDyv8x1p9K0pxvJPxs\_qL5Y2OL2-Dkoq1VH\_FtDccHq5GrpzuMK4pyw==|

**Request Sample**

```json
{
	"start_time": 1632912334,
 	"end_time": 1632912901
	"subcategory": ["organization_employee"],
	"employee_code": "e_b75a58b4",
	"page_size": 50,
	"cursor": "gmrdPA7cyZP2qGJkM-hatoA7SySeNmOlDyv8x1p9K0pxvJPxs_qL5Y2OL2-Dkoq1VH_FtDccHq5GrpzuMK4pyw=="
} Copy
```

# **Response Parameters**

|Parameter|Type|Description|Sample|
|---|---|---|---|
|code|int|Refer to the Error Code for explanation||
|next\_cursor|string|Cursor info for the next request. Put it in the "cursor" field in the next request. If the cursor is empty, it means there is no next request to be called.|gmrdPA7cyZP2qGJkM-hatoA7SySeNmOlDyv8x1p9K0pxvJPxs\_qL5Y2OL2-Dkoq1VH\_FtDccHq5GrpzuMK4pyw==|
|audit\_logs|\[\] object|List of logs||
|∟ log\_id|string|Unique identifier for each log entry|log123|
|∟ timestamp|string|The timestamp of the action , UNIX format timestamp|1632912334|
|∟ actor|string|"user" or "api" that made the action|"user" or "api"|
|∟user|object|(If actor == "user")|\-|
|∟ email|string|The email of the user who performed the action|admin@seatalk.com|
|∟ employee\_code|string|The employee code of the user who performed the action||
|∟seatalk\_id|string|The SeaTalk ID of the user who performed the action||
|∟ api|object|(If actor == "api")|\-|
|∟endpoint|string|The endpoint of the API that performed the action. Onboard Employee: "/oa\_sync/employees/onboard" Offboard Employee: "/oa\_sync/employees/offboard" Reboard Employee: "/oa\_sync/employees/reboard" Delete Employee: "/oa\_sync/employees/delete" Update Employee: "/oa\_sync/employees/update" Update Employee Avatar: "/oa\_sync/employees/update\_avatar" Create Department: "/oa\_sync/departments/create" Update Department: "/oa\_sync/departments/update" Delete Department: "/oa\_sync/departments/delete"|"/oa\_sync/employees/reboard"|
|∟app\_name|string|The name of the app that called the OA sync API|"sample-app"|
|∟app\_id|string|The ID of the app that called the OA sync API|MWZ0OTM5MzJ3FKg9|
|∟subcategory|int|Where the action was taken "organization\_department" "organization\_employee" "governance\_trusted\_device" "governance\_data\_loss\_prevention" "governance\_chat\_access\_permissions" "governance\_audit\_logs" "settings\_general"|"organization\_employee"|
|∟ action\_type|string|Type of action performed (CREATE, READ, UPDATE, DELETE)|CREATE|
|∟descriptions|\[\] object|List of descriptions Refer to Descriptions Summary table|Refer to Descriptions Summary table|

**Response sample**

```json
{
	"code": 0,
	"next_cursor": "gmrdPA7cyZP2qGJkM-hatoA7SySeNmOlDyv8x1p9K0pxvJPxs_qL5Y2OL2-Dkoq1VH_FtDccHq5GrpzuMK4pyw==",
	"admin_audit_logs": [
		{
			"log_id": "log12398753257",
			"timestamp": "1632912334",
			"actor": "user",
			"user":{
				"email": "admin@seatalk.com",
				"employee_code": "12984793460",
				"seatalk_id": "12983475749"
				},
			"api": null,
			"subcategory": "organization_employee",
			"action_type": "CREATE", 
			"descriptions": [
				"employee":{
					"employee_name": "Employee Name",
					"employee_code": "1928479123857",
					"email": "sample@seatalk.biz"
					},
				]
		},
		{
			"log_id": "log12398753239",
			"timestamp": "16329123375",
			"actor": "api",
			"user": null,
			"api": {
				"endpoint": "/oa_sync/departments/update",
				"app_name": "sample-app",
				"app_id": "MWZ0OTM5MzJ3FKg9"
			},
			"subcategory": "organization_department",
			"action_type": "UPDATE", 
			"descriptions": [
				"department": {
					"department_name": {
						"old_value": "Old Name",
						"current_value": "New Name"
						},
					"department_code": {
						"current_value": "SAMPLE DEPARTMENT"
						},
					"department_visibility": {
						"old_value": 0,
						"current_value": 1
						}
					}
				]
			}	
		]
}		 Copy
```

# Error Codes

|Code|Description|Resolution|
|---|---|---|
|100|App access token is expired or invalid|- If the token is expired/invalid, call the Get App Access Token API to get a valid token - Another common error is not specifying the authorization token type as "Bearer"|
|103|App permission denied|Ensure that the app has the approved API permission|
|102|Request body contains invalid input|Ensure that: start\_time and end\_time are properly defined subcategory exists email is properly defined|
|2005|Start time more recent than end time|Ensure that the end timestamp is more recent than the start timestamp|
|2006|Invalid timestamp|Ensure that: Timestamp format is correct Timestamp is not in the future Timestamp is not older than 12 months ago|

# Descriptions Summary

The description field of the API response will provide the exact details of what was changed by the admin operator in the log. Since some actions can affect multiple fields, only the fields that are changed will be returned. These changes will be reflected as a "old\_value" and "current\_value". Additionally, some fields will always be returned as they are identifiers for the resource that was changed:

1. **Employee:** always return employee_name, employee_email and employee_code fields as identifiers
2. **Department:** always return department_name and department_code fields as identifiers

There are also some guiding principles for each of the action types:

1. For CREATE actions, only current\_value field is returned. old\_value field is hidden.
2. For DELETE actions, only the old\_value is returned. current\_value field is hidden.

For some fields, enums will be used to represent certain values. These are listed in the table below:

|Sub-Category|Object|Field|Possible values|
|---|---|---|---|
|organisation\_department|department|department\_visibility|0: all 1: self|
||create\_department\_chat||True: Department chat active False: Department chat inactive|
|organisation\_employee|employee|employee\_type|0: none 1: fulltime 2: parttime 3: shift worker 4: contractor 5: internship 6: other|
||employee\_gender||0: none 1: male 2: female 3: unknown|
||empoyee\_status||1: Pending 2: In position 3: Leaving 4: Terminated|
|governance\_trusted\_device|trusted\_device|trusted\_device\_toggle\_state|True: Toggle on False: Toggle off|
||trusted\_device\_platform||MAC, WINDOWS|
|governance\_data\_loss\_prevention|dlp\_rule|dlp\_rule\_status|True: Enabled False: Disabled|
||dlp\_rule\_location||1: Send text messages in the external conversation and announcement 2: Send file messages in the external conversation 3: Send custom sticker messages in the external conversation 4: Copy messages on the mobile client 5: Download files on the mobile client|
|governance\_chat\_access\_permissions|chat\_access\_permission|external\_comms\_toggle\_state|True: Toggle on False: Toggle off|
||delete\_message\_toggle\_state||True: Toggle on False: Toggle off|
||chat\_audit\_toggle\_state||True: Toggle on False: Toggle off|
|settings\_general|settings\_general|organization\_visibility|0: Private 1: Public|
||organization\_location||1: Others 2: Singapore 3: Thailand 4: Vietnam 5: Taiwan 6: Malaysia 7: Indonesia 8: Philippines|
||organization\_headquarters||1: others 2: Singapore 3: Thailand 4: Vietnam 5: Taiwan 6: Malaysia 7: Indonesia 8: Philippines|
||organization\_language||1: en 2: zh-Hans 3: zh-Hant 4: th 6: vi|
||organization\_industry||1: Others 2: IT 3: Manufacture 4: Trade 5: Construction 6: Finance 7: Services 8: Education 9: Media 10: Government 11: Organizations|
|settings\_access\_control|role|role\_status|True: Active False: Inactive|
||role\_management\_scope||0: All Departments 1: My Department and Sub-Departments 2: My Department Only \[\]: Specified Departments (and their Sub-Departments) 4: No Access|
||role\_permissions||0: DepartmentView 1: EmployeeAddEdit 2: EmployeeProfileView 3: EmployeeDel 5: EmployeeImport 6: EmployeeExport 7: DepartmentAddEdit 9: DepartmentDel 10: JobTitleView 11: JobTitleAddOrEdit 12: JobTitleDel 13: OfficeView 14: OfficeAddOrEdit 15: OfficeDel 16: SettingGeneralView 22: SettingAdminView 23: SettingAdminAddEdit 24: SettingAdminToggle 26: SettingAdminDel 32: PayrollCompanyView 33: PayrollCompanyAddOrEdit 34: PayrollCompanyDel 35: RankView 36: RankAddOrEdit 37: RankDel 59: AppCenter 60: AppCenterDeveloper 63: AppCenterReleaseManager 68: CustomFieldView 69: CustomFieldAddOrEdit 70: CustomFieldDel 72: ConfigOrgChartVisibility 73: ConfigUserGroup|

Was this document helpful?

No

Yes