# Create Group Chat

> Requires SeaTalk App version 3.50.0 or above, releasing at the end of November 2024

# API Description

This API allows a bot to create a group chat.

* Size of Group member list must be between 1 and 30

* Rate Limit: 100 groups per app each day, 10 groups per app every minute

* All users in the member list must be in the service scope of the Bot, else they will not be added to the group
* Since February 6, 2025, this API no longer validates the user's subscriber identity

**Request API Permission:** Create Group Chat  
**Request Method:** `POST`**End Point:** [https://openapi.seatalk.io/messaging/v2/group\_chat/create\_group](https://openapi.seatalk.io/messaging/v2/group_chat/create_group)

# Request Parameter

## **Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

## **Parameter**

|Parameter|Type|Mandatory|Description|Default|Length Limit|
|---|---|---|---|---|---|
|group\_owner|string|Yes|The employee\_code of the group owner.|N/A|N/A|
|group\_member\_list|\[\]object|Yes|The list of users invited into the group. Only users in the bot's service scope can be invited into the group. Regardless of the duplicates, the maximum size will still be 30, and at least 1 member.|N/A|N/A|
|∟employee\_code|string|Yes|The employee code(s) of the list of members|N/A|N/A|
|∟role|integer|No|0 - “group member” 1 - “group admin”|0|N/A|
|group\_name|string|No|The group name|The name of the users until reaches the limit|120 characters|
|group\_settings|object|No|Group settings|NA|NA|
|∟chat\_history\_for\_new\_members|integer|No|The chat history settings 0 - “Off” 1 - “24 hours” 2 - “7 days”|0|NA|

## **Request Sample**

```json
{
     "group_owner": "xxx",
     "group_member_list": [
           {
                "employee_code": "xxx",
                "role": 1
            },
            {
                 "employee_code": "xxx",
                 "role": 0
            }
        ],
         "group_name": "Group Chat Test 123",
         "group_settings": {
              "chat_history_for_new_members": 2
         }
}
 Copy
```

# **Response Parameter**

|Parameter|Type|Mandatory|Description|
|---|---|---|---|
|code|int|Yes|Refer to Error Code for explanation. 0 if updating the message successfully.|
|group\_id|string|Yes|Group id of the group created|
|users\_not\_added|string\[\]|Yes|Employee codes of users who could not be added to the group they are not in the service scope of the bot the employee codes are invalid|

## **Error Codes**

|Value|Description|Resolution|
|---|---|---|
|102|Request body contains invalid input|Ensure that the group\_member\_list contains 1 - 30 valid employee codes Ensure that group\_owner is provided|
|3001|User not found with the current code|Check whether the group owner's code belongs to a valid employee within the app's service/data scope|
|3002|User is not in the service scope of the bot|Ensure that the group owner is currently not in the service scope of the bot|

## **Response Sample**

```json
{
        "code": 0,
        "group_id": "NTk2NjAxMDUyMzMz",
        "users_not_added": []
} Copy
```

Was this document helpful?

No

Yes