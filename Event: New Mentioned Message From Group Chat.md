# Event: New Mentioned Message From Group Chat

## Event Description

This event is triggered when a group member mentions the bot using '@' in a text message in a group chat. '@All' will**not**trigger this event.

**Starting from 11 June 2024, each event will provide a** **thread\_id** **to indicate whether the user has mentioned the bot in a thread. (Learn more about [threading messages in group chats](https://open.seatalk.io/docs/Threading-Messages-in-Group-Chats))**

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
|event\_type|string|The type of the event. It will be "new\_mentioned\_message\_received\_from\_group\_chat" in this case|
|timestamp|unit64|The time when this event happened|
|app\_id|string|The ID of the app to receive the event notifi|
|event|object|Event-specific information|
|∟group\_id|string|The ID of the group chat which the bot receives the mentioned message from|
|∟message|object|The message received|
|∟message\_id|string|The ID of the message Note: For security reasons, a single message will have different message\_ids when accessed by different apps.|
|∟quoted\_message\_id|string|The ID of the quoted message (If the message has quoted any message) Note: For security reasons, a single message will have different message\_ids when accessed by different apps.|
|∟ thread\_id|string|Effective from 11 June 2024. The ID of the thread. Provided if the message is part of a thread.|
|∟sender|object|Information of the message sender|
|∟seatalk\_id|string|The SeaTalk ID of the message sender|
|∟employee\_code|string|- The employee\_code of the message sender - It will return empty if the message sender and the bot do not belong to the same organisation.|
|∟email|string|- The email of the message sender - It will return empty if the message sender and the bot do not belong to the same organisation.|
|∟sender\_type|int|1: User 2: Bot 3: System Account|
|∟message\_sent\_time|unit64|The time when the message was sent|
|∟tag|string|The type of the message. It will be 'text' in this case|
|∟text|object||
|∟plain\_text|string|- Message content in the plain text format - Refer to this document to understand the details on how plain text format is converted if the original message is formatted.|
|∟mentioned\_list|\[\] object|List of mappings between usernames and SeaTalk ID of users or bots|
|∟username|string|- Mention specific user or bot: User's current username inserted into the plain\_text message content - Mention all: Empty|
|∟seatalk\_id|string|- Mention specific user or bot: SeaTalk ID - Mention all: 0|
|∟employee\_code|string|- Mention specific user: The employee\_code of the mentioned user - Mention specific bot: Empty - Mention all: Empty|
|∟email|string|- Mention specific user: The email of the mentioned user - Mention specific bot: Empty - Mention all: Empty|

**Request Body Sample**

```json
{
  "event_id": "1234567",
  "event_type": "new_mentioned_message_received_from_group_chat",
  "timestamp": 1687764109,
  "app_id": "abcdefghiklmn",
  "event": {
    "group_id": "qwertyui",
    "message": {
      "message_id": "kashfefrhnedf",
      "quoted_message_id": "",
      "thread_id": "hfaohenbkdaj",
      "sender": {
        "seatalk_id": "91234567",
        "employee_code": "abcdefg"
        "email": "sample@seatalk.biz"
      },
      "message_sent_time": 1687764109,
      "tag": "text",
      "text": {
        "plain_text": "Hello @All, kindly be reminded to complete this @Good Bot",
        "mentioned_list": [
          {
            "username": "",
            "seatalk_id": "0"
          },
          {
            "username": "Good Bot",
            "seatalk_id": "1234567"
            "employee_code": "e_1o38475899"
            "email": "sample@seatalk.biz"

          }
        ]
      }
    }
  }
} Copy
```

Was this document helpful?

No

Yes