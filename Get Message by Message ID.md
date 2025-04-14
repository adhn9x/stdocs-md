# Get Message by Message ID

> *****API Updates:** *Effective from 14 November 2024.  
> **Sending Images, Files and Videos to 1-1 chats with Bots on SeaTalk App**: Requires SeaTalk App version 3.50 or above, releasing on 28 November 2024, for full functionality.****

# API Description

Obtain the message content by the message\_id.

Images, files and videos sent to bots can be downloaded with the URL starting with **https://openapi.seatalk.io/messaging/v2/file/**. For more information, please refer to [this document](https://open.seatalk.io/docs/Introduction-to-Received-Message-Types). The rate limit for this endpoint is 100 requests/min.

**Request Method**:`GET`

**End Point**: https://openapi.seatalk.io/messaging/v2/get\_message\_by\_message\_id

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|

**Parameter**

|Parameter|Type|Mandatory|Description|Default|
|---|---|---|---|---|
|message\_id|string|Yes|The ID of the target message, which can be obtained via the event "New Mentioned Message From Group Chat", which can be the "quoted\_message\_id".|N/A|

**Request Sample**

https://openapi.seatalk.io/messaging/v2/get\_message\_by\_message\_id?message\_id=xxxxx

# Response Parameter

**Result Fields**

|Parameter|Type|Description|Size/Length Limit|
|---|---|---|---|
|code|int|Refer to the Error Code for explanation||
|quoted\_message\_id|string|- The message ID of the quoted message. - Return empty if not quoting any message.||
|thread\_id|string|Effective from 11 June 2024. The thread ID. Provided if the message is part of a thread.||
|sender|object|||
|∟seatalk\_id|string|The SeaTalk ID of the message sender.||
|∟employee\_code|string|- The employee code of the message sender. - Return empty if the message sender does not belong to the same org as bot.||
|∟email|string|- The email of the message sender - Return empty if the message sender does not belong to the same org as bot.||
|∟sender\_type|int|The message sender's type. 1 is User, 2 is Bot, 3 is System Account.||
|message\_sent\_time|unit64|The time when the message is sent.||
|tag|string|The message type. Allowed tags: "text", "combined\_forwarded\_chat\_history", "image", "file", "video" For more details on suppported message types for bots, refer to this document.||
|text|object|The text message object||
|∟plain\_text|string|The text message content||
|∟last\_edited\_time|unit64|- Return the message's most recent edit time - Return 0 if the message is not edited||
|∟mentioned\_list|\[\] object|List of mappings between usernames and SeaTalk IDs of users or bots||
|∟username|string|- Mention specific user or bot: User's current username inserted into the plain\_text message content - Mention all: Empty||
|∟seatalk\_id|string|- Mention specific user or bot: SeaTalk ID - Mention all: 0||
|combined\_forwarded\_chat\_history|object|The combined forwarded chat history message object||
|∟content|Multi-layered Array List of Message object|Support returning up to 3 layers of combined forwarded chat history: - If the message is a text message, return the text object mentioned in the above "1.1 Text" section. - If the message is of any other type, return null.||
|image|object|The image object||
|∟content|string|The URL of the image. Requires a valid API token to access. The image message expires in 7 days and cannot be downloaded using the URL subsequently.|Max: 250 MB|
|file|object|The file object||
|∟content|string|The URL of the file. Requires a valid API token to access. The file message expires in 7 days and cannot be downloaded using the URL subsequently.|Max: 250 MB|
|∟filename|string|The file name with extension; files with no extension specified will be sent as unidentified files|Max: 100 characters|
|video|object|The video object||
|∟content|string|The URL of the video. Requires a valid API token to access. The file message expires in 7 days and cannot be downloaded using the URL subsequently.|Max: 250 MB|

**Response Sample**

```json
//text 
{
    "code":0,
    "message_id":"qsyVDuPj0D1SP50b-tBR2p2u9N576W3z32Y83qr64hqeUIq4jQozu7yW5Dz1EKzu",
    "quoted_message_id":"",
    "sender":{
        "seatalk_id":"12345678",
        "employee_code":"e_12345678",
        "employee_code":"e_12345678",
        "email":"sample1@seatalk.biz",
        "sender_type":1
    },
    "message_sent_time":1693454853,
    "tag":"text",
    "text":{
        "plain_text":"Hello world!",
        "last_edited_time":0,
        "mentioned_list":[
            
        ]
    },
    "combined_forwarded_chat_history":null,
    "image":null,
    "video":null,
    "file":null
}

//combined forwarded
{
    "code":0,
    "message_id":"qsyVDuPj0D1SP50b-tBR2poyuM2ZAmuTLq6GJN6wS35lJXxbn0pFyQFI34EmwPoe",
    "quoted_message_id":"",
    "sender":{
        "seatalk_id":"9440420845",
        "employee_code":"e_n29j6jjq",
        "email":"sample2@seatalk.biz",
        "sender_type":1
    },
    "message_sent_time":1693463681,
    "tag":"combined_forwarded_chat_history",
    "text":null,
    "combined_forwarded_chat_history":{
        "content":[
            {
                "message_id":"",
                "quoted_message_id":"",
                "sender":{
                    "seatalk_id":"9440420845",
                    "employee_code":"e_n29j6jjq",
                    "email":"sample3@seatalk.biz",
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
                    "email":"sample4@seatalk.biz",vcc
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
}

//image 
{
    "code":0,
    "message_id":"qsyVDuPj0D1SP50b-tBR2p2u9N576W3z32Y83qr64hqeUIq4jQozu7yW5Dz1EKzu",
    "quoted_message_id":"",
    "sender":{
        "seatalk_id":"12345678",
        "employee_code":"e_12345678",
        "email":"sample5@seatalk.biz",
        "sender_type":1
    },
    "message_sent_time":1693454853,
    "tag":"image",
    "text":null,
    "combined_forwarded_chat_history":null,
    "image":{
        "content":"https://openapi.seatalk.io/messaging/v2/file/asjewnJHe7dfjsWK8LksdmsMN90JjsdwekjU1efwefscvLKJ"
    },
    "video":null,
    "file":null
}

//video 
{
    "code":0,
    "message_id":"qsyVDuPj0D1SP50b-tBR2p2u9N576W3z32Y83qr64hqeUIq4jQozu7yW5Dz1EKzu",
    "quoted_message_id":"",
    "sender":{
        "seatalk_id":"12345678",
        "employee_code":"e_12345678",
        "email":"sample6@seatalk.biz",
        "sender_type":1
    },
    "message_sent_time":1693454853,
    "tag":"video",
    "text":null,
    "combined_forwarded_chat_history":null,
    "image":null,
    "video":{
        "content":"https://openapi.seatalk.io/messaging/v2/file/uieLdasuUWhebwrBksadfjBMSFIUEmwkefjhgjksdJKK8GJSFNsdjk"
    },
    "file":null
}

//file
{
    "code":0,
    "message_id":"qsyVDuPj0D1SP50b-tBR2p2u9N576W3z32Y83qr64hqeUIq4jQozu7yW5Dz1EKzu",
    "quoted_message_id":"",
    "sender":{
        "seatalk_id":"12345678",
        "employee_code":"e_12345678",
        "email":"sample7@seatalk.biz",
        "sender_type":1
    },
    "message_sent_time":1693454853,
    "tag":"file",
    "text":null,
    "combined_forwarded_chat_history":null,
    "image":null,
    "video":null,
    "file":{
        "content":"https://openapi.seatalk.io/messaging/v2/file/lskdfewnOKNFiewbeBKuKEKQW7JWEfjefnqwesdi8JFNekqlkfwqef",
        "filename": "sample.txt"
    }
} Copy
```

Was this document helpful?

No

Yes