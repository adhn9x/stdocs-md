# Event: Bot Added To Group Chat

## Event Description

This event is triggered when a bot user has added the bot to a group chat.

## Event Parameter

**Header**

|Parameter|Type|Description|
|---|---|---|
|Content-Type|string|Request header format|
|Signature|unit64|A signature to ensure that the request is sent by SeaTalk|

**Body**

|Parameter|Type|Description|
|---|---|---|
|event\_id|string|The ID of the event|
|event\_type|string|The type of the event. It will be " bot\_added\_to\_group\_chat " in this case|
|timestamp|unit64|The time when this event happened|
|app\_id|string|The ID of the app to receive the event notification|
|event|object|Event-object information|
|∟group|object|Information of the group chat which the bot is added to|
|∟group\_id|string|The ID of the group chat|
|∟group\_name|string|Group name when the bot is added|
|∟group\_settings|object|Current group settings when the bot is added|
|∟chat\_history\_for\_new\_members|string|The extent to which the bot can access the chat histories sent prior to joining. Possible values are "disabled", "1 day" and "7 days".|
|∟can\_notify\_with\_at\_all|boolean|Whether group members are allowed to notify all group members with '@All'.|
|∟can\_view\_member\_list|boolean|Whether group members are allowed to view the group member list|
|∟inviter|object||
|∟seatalk\_id|string|The SeaTalk ID of the user who has added the bot to the group chat|
|∟employee\_code|string|The employee\_code of the user who has added the bot to the group chat|
|∟email|string|The email of the user who added the bot to the group chat|

**Request Body Sample**

```json
{
    "event_id":"1234567",
    "event_type":"bot_added_to_group_chat",
    "timestamp":1687764109,
    "app_id":"abcdefghiklmn",
    "event":{
        "group":{
            "group_id":"qwertyui",
            "group_name":"Test Group",
            "group_settings":{
                "chat_history_for_new_members":"disabled",
                "can_notify_with_at_all":false,
                "can_view_member_list":false
            }
        },
        "inviter":{
            "seatalk_id":"1234567890",
            "employee_code":"e_12345678"            
            "email":"sample@seatalk.biz"
        }
    }
} Copy
```

Was this document helpful?

No

Yes