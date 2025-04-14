# Event: Bot Removed From Group Chat

## Event Description

This event is triggered when the bot has been removed from a group successfully due to manual removal or group disbandment.

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
|event\_type|string|The type of the event. It will be " bot\_removed\_from\_group\_chat " in this case|
|timestamp|unit64|The time when this event happened|
|app\_id|string|The ID of the app to receive the event notifi|
|event|object|Event-specific information|
|∟group\_id|string|The ID of the group chat|
|∟remover|object|Information of the user who has removed the bot from the group chat|
|∟seatalk\_id|string|The SeaTalk ID of the remover|
|∟employee\_code|string|- The employee\_code of the remover - Return empty if the remover and the bot do not belong to the same organisation|
|∟email|string|- The email of the remover - Return empty when the user and the bot do not belong to the same organisation.|

**Request Body Sample**

```json
{
  "event_id": "1234567",
  "event_type": "bot_removed_from_group_chat",
  "timestamp": 1687764109,
  "app_id": "abcdefghiklmn",
  "event": {
    "group_id": "qwertyui",
    "remover": {
      "seatalk_id": "1234567890",
      "employee_code": "e_12345678"
      "email": "sample@seatalk.biz"
    }
  }
} Copy
```

Was this document helpful?

No

Yes