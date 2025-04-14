# Overview of Messaging Methods

Messaging lies at the foundation of SeaTalk IM. Messaging enables information to flow between different users, systems and places. SeaTalk Open Platform provides several messaging methods (open capabilities) to cater for diverse scenarios and needs.

Currently, three messaging methods are supported:

1. **System accounts** that push messages to a group chat
2. **Bots** that send and receive messages in both 1-on-1 chats and group chats.
3. **Service notices** that push one-way messages to an aggregated notification center called Application Center

# Which Messaging Method I Should Use?

Wondering which messaging method should you select for your case? See the table below for a comparison of the three methods:

|Messaging Method|Communication Channel|Communication Style|Introduction|More Suitable For...|Typical Scenarios|Requirements|
|---|---|---|---|---|---|---|
|System Accounts|A group chat|One-way communication|Push Group Chat Messages Through System Account|Group announcements|- Send system alert messages to a group chat where engineers on duty need to stand by - Consolidate product feedback to a product team's group chat|- You have to be the group chat owner/admin or a group chat system account admin to create a system account - You have to build a service to push messages via a system account's webhook URL|
|Bots|A 1-on-1 chat or a group chat|Two-way communication|Quickly Build a Bot|- FAQs automation - Simple task execution|- Address FAQs on a product/business line - Automate info/data query through simple commands|- You have to create an app on SeaTalk Open Platform to access the bot messaging capability - You have to set up event callback for your bot to receive messages from users|
|Service Notices|Application Center (a standalone notification center that appears in the chat list and aggregates service notices sent by all the apps a user uses)|One-way communication|Send Service Notice|- Lightweight announcements - Personalised one-way notifications|- Notify users when some approval is pending for review - Inform employees when the payslip of the new month is out|- You have to create an app on SeaTalk Open Platform to access the service notice capability - If you want to use interactive buttons that trigger callback, you have to set up event callback for your app|

Was this document helpful?

No

Yes