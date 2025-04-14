# Understanding Bot Capabilities

Welcome to the Bot API Overview page! Here, you will find all the essential APIs and Events you need to build powerful and interactive bots on SeaTalk. From understanding the capabilities of SeaTalk bots to exploring the various APIs available, this page is your go-to guide for creating seamless and engaging bot experiences. Let's dive in and unlock the full potential of SeaTalk bots together!

Here is the list of API and Event related to Bot:

|Category|API / Event Name|Description|Documentation Link|
|---|---|---|---|
|Authentication|Get App Access Token|This API is used to obtain an access token for your application. This access token is necessary to authenticate your application when making API requests to the SeaTalk Open Platform.|https://open.seatalk.io/docs/get-app-access-token|
|Contact|Get Employee Profile|This API allows you to obtain an employee's basic profile information, including their email, employee code, name, mobile number, department, reporting manager, etc.|https://open.seatalk.io/docs/get-employee-profile|
||Get Employee Code with Email|This API allows you to exchange a user's email for their corresponding employee code within your organization|https://open.seatalk.io/docs/get-employee-code-with-email|
||Get User Language Preference|This API allows you to retrieve the language preference of a user, provides you with the information about the language that the user has set as their preferred language for the application or platform.|https://open.seatalk.io/docs/get-user-lang-pref|
||Event: Bot Added To Group Chat|This event is triggered when a bot user adds the bot to a group chat. This event provides information about the group chat where the bot has been added, including the group ID. It allows you to track and handle the event of your bot being added to a group chat, enabling you to perform actions or send messages in response to this event.|https://open.seatalk.io/docs/event-bot-added-to-group-chat|
||Get Joined Group Chat List|This API allows you to retrieve a list of group chats that the bot has joined. This API provides information about the group chats, including their IDs, names, member counts, and other relevant details.|https://open.seatalk.io/docs/Get-Joined-Group-Chat-List|
||Get Group Info|This API allows you to retrieve the basic information of a group chat that the bot has been added to. This API provides details such as the group chat name, group settings, total number of users, bots, and system accounts in the group.|https://open.seatalk.io/docs/get-group-info|
||Event: Bot Removed From Group Chat|This event is triggered when the bot has been removed from a group chat. This event indicates that the bot is no longer a member of the group chat due to manual removal or group disbandment. It provides information such as the event ID, event type, timestamp, app ID, and the ID of the group chat from which the bot was removed.|https://open.seatalk.io/docs/Event-Bot-Removed-From-Group-Chat|
|Messaging: 1-1 Chat|Send Message to A Bot User|T his API allows you to send a message to a user of your bot in a 1-on-1 chat. The API enables you to communicate with your bot's users by sending text messages, formatted messages, or even interactive messages.|https://open.seatalk.io/docs/messaging\_send-message-to-bot-subscriber\_|
||Event: Message Received from Bot User|This event is triggered when a bot user sends a message to the bot in a 1-on-1 chat. This event allows you to receive and handle the messages sent by your bot's users, enabling you to respond or take appropriate actions based on the received message.|https://open.seatalk.io/docs/event\_message\_received\_from\_bot\_subscriber|
|Messaging: Group Chat|Event: New Mentioned Message From Group Chat|This event is triggered when a group member mentions the bot using '@' in a text message in a group chat. This event allows you to receive and handle the mentioned messages sent by group members, providing you with the message content, sender information, and the group ID. You can use this event to respond to the mentioned messages or perform specific actions based on the received message.|https://open.seatalk.io/docs/event\_new\_mentioned\_message\_from\_group\_chat|
||Send Message to Group Chat|This API allows you to send a message to a group chat where the bot has been added. With this API, you can send text messages with or without formatting, as well as images.|https://open.seatalk.io/docs/Send-Message-to-Group-Chat|
||Get Message by Message ID API|This API allows you to retrieve a specific message by its unique message ID. By providing the message ID as a parameter, you can retrieve detailed information about the message, including its content, sender, timestamp, and other relevant data.|https://open.seatalk.io/docs/Get-Message-by-Message-ID|
||Get Chat History|This API allows you to retrieve the chat history of a group chat where the bot has been added. This API provides you with a list of messages exchanged in the group chat, including the message content, sender information, timestamps, and other relevant details. It is a useful API for retrieving past conversations and analyzing the chat history within your application or system.|https://open.seatalk.io/docs/get-chat-history|
|Messaging: Other|Event: Interactive Message Click|This event is triggered when a user clicks on a callback button on an interactive message card. This event provides information such as the event ID, event type, timestamp, app ID, message ID, employee code of the user, and the callback value of the button clicked. It allows you to capture user interactions with interactive message cards and perform specific actions or responses based on the button clicked.|https://open.seatalk.io/docs/event\_interactive\_message\_click|

# What's next?

Interested in seeing how a bot is implemented to provide day to day value? Check this out!

[Example: Stockwatch](https://open.seatalk.io/docs/Example-Stockwatch)

Was this document helpful?

No

Yes