# Get Chat History

> *****API Updates:** *Effective from 14 November 2024.  
> **Sending Images, Files and Videos to 1-1 chats with Bots on SeaTalk App**: Requires SeaTalk App version 3.50 or above, releasing on 28 November 2024, for full functionality.****

# API Description

Use this API to obtain the group chat histories**sent within 7 days**.For chat histories sent before the bot joins the group, it will be limited by the "Chat History For New Members" group setting when bot is added to the group.

Messages will be returned in**reverse chronological order** based on their sent time (from the latest to the earliest)

Images, files and videos sent to bots can be downloaded with the URL starting with **https://openapi.seatalk.io/messaging/v2/file/**. For more information, please refer to [this document](https://open.seatalk.io/docs/Introduction-to-Received-Message-Types). The rate limit for this endpoint is 100 requests/min.

Note:

* This API requires permission to access the **Get Chat History** API. Due to the sensitive nature of the chat histories, only apps that have **obtained approval from management** will be granted access.
* To call this API, your app must enable the **bot capability** and have an**Online**status. See more at<u>[Quickly build a Bot](https://open.seatalk.io/docs/quickly-build-a-bot)</u>.
* This API is limited to**100** requests per minute under one app ID.

**Request Method**: `GET`

**End Point**: <u>[https://openapi.seatalk.io/messaging/v2/group\_chat/history](https://openapi.seatalk.io/messaging/v2/group_chat)</u>

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

**Parameter**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|group\_id|string|Yes|The group chat ID|N/A|"abcdef"|
|page\_size|int|No|Number of messages included in one response for each list. It must be an integer between 1-100 (inclusive). Remarks: In very few cases, it is possible that due to the large size of the message body requested, it may not be possible to return the desired number of pages.|50|50|
|cursor|string|No|- Pagination markup. It is not filled in the first request, indicating traversal from the latest message. - When there will be more messages, the next cursor will be returned in the response of the current request, and the next traversal can use the cursor to get the rest of chat histories.|N/A|gmrdPA7cyZP2qGJkM-hatoA7SySeNmOlDyv8x1p9K0pxvJPxs\_qL5Y2OL2-Dkoq1VH\_FtDccHq5GrpzuMK4pyw==|

**Request Sample**

```markup
https://openapi.seatalk.io/messaging/v2/group_chat/history?group_id=abcdef&page_size=50 Copy
```

# Response Parameter

|Parameter|Type|Description|Size/Length Limit|
|---|---|---|---|
|code|int|Refer to the Error Code for explanation||
|next\_cursor|string|Cursor info for the next request. Put it in the "cursor" field in the next request. If the cursor is empty, it means there is no next request to be called.||
|chat\_history|\[\] object|List of Message object||
|∟message\_id|string|The message ID||
|∟quoted\_message\_id|string|- The message ID of the quoted message. - Return empty if not quoting any message.||
|∟thread\_id|string|Effective from 11 June 2024. The thread ID. Provided if the message is part of a thread.||
|∟sender|object|||
|∟seatalk\_id|string|The SeaTalk ID of the message sender.||
|∟employee\_code|string|- The employee code of the message sender. - Return empty if the message sender does not belong to the same org as bot.||
|∟email|string|- The email of the message sender - Return empty when the user and the bot do not belong to the same org as bot.||
|∟sender\_type|int|1: User 2: Bot 3: System Account||
|∟message\_sent\_time|unit64|The time when the message is sent.||
|∟tag|string|The message type. Allowed tags: "text", "combined\_forwarded\_message\_history", "image", "file", "video" For more details on suppported message types for bots, refer to this document.||
|∟ text|object|The text message object||
|∟plain\_text|string|The text message content||
|∟last\_edited\_time|unit64|- Return the message's most recent edit time - Return 0 if the message is not edited||
|∟mentioned\_list|\[\] object|List of mappings between usernames and SeaTalk IDs of users or bots||
|∟username|string|- Mention specific user or bot: User's current username inserted into the plain\_text message content - Mention all: Empty||
|∟seatalk\_id|string|- Mention specific user or bot: SeaTalk ID - Mention all: 0||
|∟employee\_code|string|- Mention specific user: Employee Code - Mention specific bot: Empty - Mention all: Empty||
|∟email|string|- Mention specific user: Email - Mention specific bot: Empty - Mention all: Empty||
|∟combined\_forwarded\_chat\_history|object|The combined forwarded chat history message object||
|∟content|Multi-layered Array List of Message object|Support returning up to 3 layers of combined forwarded chat history: - If the message is a text message, return the text object mentioned in the above "1.1 Text" section. - If the message is of any other type, return null.||
|∟image|object|The image object||
|∟content|string|The URL of the image. Requires a valid API token to access. The image message expires in 7 days and cannot be downloaded using the URL subsequently.|Max: 250 MB|
|∟file|object|The file object||
|∟content|string|The URL of the file. Requires a valid API token to access. The file message expires in 7 days and cannot be downloaded using the URL subsequently.|Max: 250 MB|
|∟filename|string|The file name with extension; files with no extension specified will be sent as unidentified files|Max: 100 characters|
|∟video|object|The video object||
|∟content|string|The URL of the video. Requires a valid API token to access. The video message expires in 7 days and cannot be downloaded using the URL subsequently.|Max: 250 MB|

**Response Sample**

```json
{
    "code": 0,
    "next_cursor": "zswdefvffggff",
    "chat_history": [

//unsupported tag
    {
        "message_id": "abcdefghi",
        "quoted_message_id": "",
        "sender": {
        "seatalk_id": "123456789",
        "employee_code": "abcdefg"
        "email": "sample@seatalk.biz"
        },
        "message_sent_time": 1687944555,
        "tag": "note",
        "text":null,
        "combined_forwarded_chat_history":null,
        "image":null,
        "video":null,
        "file":null
    },

//text
    {
        "message_id": "bcdefghiu",
        "quoted_message_id": "",
        "sender": {
            "seatalk_id": "123456789",
            "employee_code": "abcdefg"
            "email": "sample@seatalk.biz"
        },
        "message_sent_time": 1687944533,
        "tag": "text",
        "text": {
            "plain_text": "@User1 Today is Monday",
            "last_edited_time": 1710919702,
            "mentioned_list": [
            {
                "username": "User1",
                "seatalk_id": "234567890"
                "employee_code": "e_19283719"
                "email": "sample@seatalk.biz"

            }
            ]
        },
        "combined_forwarded_chat_history": null
    },

//combined forwarded 
    {
        "message_id": "bcdefghiu",
        "quoted_message_id": "",
        "sender": {
            "seatalk_id": "123456789",
            "employee_code": "abcdefg"
            "email": "sample@seatalk.biz"
        },
        "message_sent_time": 1687944533,
        "tag":"combined_forwarded_chat_history",
        "combined_forwarded_chat_history":{
            "content":[
                {
                    "message_id":"",
                    "quoted_message_id":"",
                    "sender":{
                        "seatalk_id":"9440420845",
                        "employee_code":"e_n29j6jjq",
                        "sender_type":1
                    },
                    "message_sent_time":1693463635,
                    "tag":"text",
                    "text":{
                        "plain_text":"Hello, world!",
                        "last_edited_time":0,
                        "mentioned_list":[
                            
                        ]
                    },
                    "combined_forwarded_chat_history":null,
                    "image":null,
                    "video":null,
                    "file":null 
                },
                {
                    "message_id":"",
                    "quoted_message_id":"",
                    "sender":{
                        "seatalk_id":"9440420845",
                        "employee_code":"e_n29j6jjq",
                        "email": "sample@seatalk.biz"
                        "sender_type":1
                    },
                    "message_sent_time":1693463639,
                    "tag":"text",
                    "text":{
                        "plain_text":"Hello, world!",
                        "last_edited_time":0,
                        "mentioned_list":[
                            
                        ]
                    },
                    "combined_forwarded_chat_history":null,
                    "image":null,
                    "video":null,
                    "file":null
                }
            ]
        },
        "image":null,
        "video":null,
        "file":null
    },       

//image
    {
        "message_id": "bcdefghiu",
        "quoted_message_id": "",
        "sender": {
            "seatalk_id": "123456789",
            "employee_code": "abcdefg"
            "email": "sample@seatalk.biz"
        },
        "message_sent_time": 1687944533,
        "tag":"image",
        "text":null,
        "combined_forwarded_chat_history":null,
        "image": {
            "content":"https://openapi.seatalk.io/messaging/v2/file/asjewnJHe7dfjsWK8LksdmsMN90JjsdwekjU1efwefscvLKJ"
        },
        "video":null,
        "file":null
        
    },

//video
    {
        "message_id": "bcdefghiu",
        "quoted_message_id": "",
        "sender": {
            "seatalk_id": "123456789",
            "employee_code": "abcdefg"
            "email": "sample@seatalk.biz"
        },
        "message_sent_time": 1687944533,
        "tag":"image",
        "text":null,
        "combined_forwarded_chat_history":null,
        "image":null,
        "video":{
            "content":"https://openapi.seatalk.io/messaging/v2/file/uieLdasuUWhebwrBksadfjBMSFIUEmwkefjhgjksdJKK8GJSFNsdjk"
        },
        "file":null
        
    },

//file
    {
        "message_id": "bcdefghiu",
        "quoted_message_id": "",
        "sender": {
            "seatalk_id": "123456789",
            "employee_code": "abcdefg"
            "email": "sample@seatalk.biz"
        },
        "message_sent_time": 1687944533,
        "tag":"image",
        "text":null,
        "combined_forwarded_chat_history":null,
        "image":null,
        "video":null,
        "file":{
            "content":"https://openapi.seatalk.io/messaging/v2/file/lskdfewnOKNFiewbeBKuKEKQW7JWEfjefnqwesdi8JFNekqlkfwqef",
            "filename":"sample.txt"
        }
    }
  ]
} Copy
```

Was this document helpful?

No

Yes