# Changelog

Hi SeaTalk Open Platform developers, you can find all changelogs related to the open platform in this doc. We will also post important notices here too!

# 26 Feb 2025

**API updates: Addition of email and employee code fields to responses**

* We've heard your feedback that it can be difficult to retrieve user emails and employee codes!
* Various APIs have been updated to add these fields, allowing for more seamless integrations. Please refer to our API docs for further details.
* **APIs and Events updated:**

  * Check Employee Existence
  * Get Departments
  * Get Department Employees
  * Get Message by Message ID
  * Event: Message Received From Bot User
  * Event: New Mentioned Message From Group Chat
  * Event: Interactive Message Click
  * Get Approval Item
  * Get Thread by Thread ID
  * Event: Bot Added To Group Chat
  * Get Group Info
  * Event: Bot Removed From Group Chat
  * Get Chat History

# 06 Feb 2025

**Subscription layer removal for all bots**

* With the removal of the subscription layer for all bots users can now chat with bots in their service scope without having to subscribe to it.
* Impact on bots' development:
  * **API Changes**: The “Send Message to a Bot Subscriber” API will be updated, the validation requiring user subscription will be removed. The “Get Bot Subscriber List” and the event “New Bot Subscriber” will be deprecated.
  * **App Changes**: Users will no longer see a “Subscribe” button on bot profile pages. Instead, the “Message” button will always be present, streamlining user access.
  * **Review Your Bot’s Logic**: Ensure that any feature relying on the “API: Get Bot Subscriber List”, "Event: New Bot Subscriber" and any subscription-based interactions is adjusted accordingly.

# 28 Nov 2024

**Bots can now receive images, files and videos from private chats!**

* With the release of SeaTalk v3.50.0, the SeaTalk UI for private chatrooms with bots now supports sending images, files and videos
* Update your app to experience this functionality!

# 14 Nov 2024

**APIs updated to allow bots to receive images, files and videos**

* The following APIs/events can now support tag types "image", "video" and "file"
  1. Event: New Message Received from Bot User
  2. Get Message by Message ID
  3. Get Chat History
  4. Get Thread by Thread ID

**Coming soon in SeaTalk v3.50.0**

* SeaTalk UI for 1-1 chatrooms with bots will allow users to send images, files and videos
* Estimated release date: 28 Nov 2024

# **17 October 2024**

### **New API "Update Message" to update sent interactive message card**

* ### Update Message API https://open.seatalk.io/docs/Update-Interactive-Message-Card

# **18 July 2024**

### **New API "Delete Employee Profile"**

* Delete Employee API https://open.seatalk.io/docs/Delete-Employee

### **New Parameter "Offboarding\_time" to be returned in "Get Employee Profile" API**

* Get Employee Profile API https://open.seatalk.io/docs/get-employee-profile

# **6 June 2024**

> ***Effective Date:***

> ***API Updates:*** *Effective from 11 June 2024.*

> ***Interacting with Bots in Threads on SeaTalk App*** *: Requires SeaTalk App version 3.44.5 or above, releasing on 14 June 2024, for full functionality.*

### **Thread Support for Bots**

Introduce support for bots to interact with threads in group chats. Effective from 11 June 2024.

* **[Sending Messages to Threads](https://open.seatalk.io/docs/Send-Message-to-Group-Chat):** Bots can now send replies to specific threads usingthread\_id.
* **[Receiving Mentions in Threads](https://open.seatalk.io/docs/event_new_mentioned_message_from_group_chat)**: Event updates will includethread\_id to indicate mentions in threads.
* **[Retrieving Threads](https://open.seatalk.io/docs/Get-Thread-by-Thread-ID)**: Fetch entire conversation threads usingthread\_id.
* Existing APIs, such as getting messages by message\_id and getting chat history, will now includethread\_id in the response.

# **17 May 2024**

### **New parameter "last\_edited\_time" to return the time of the most recent message edit**

* Get Message by Message ID API[https://open.seatalk.io/docs/Get-Message-by-Message-ID](https://open.seatalk.io/docs/Get-Message-by-Message-ID)

# **16 Nov 2023**

### **Bot and System Account Enhancement**

Introduce support for **sending formatted messages** using markdown in the **“text” message type**.

1. \[System Account\] [https://open.seatalk.io/docs/system-account#Send%20a%20Message-2](https://open.seatalk.io/docs/system-account#Send%20a%20Message-2)
2. \[1-on-1 Bot\] [https://open.seatalk.io/docs/messaging\_send-message-to-bot-subscriber\_](https://open.seatalk.io/docs/messaging_send-message-to-bot-subscriber_)
3. \[Group Bot\] [https://open.seatalk.io/docs/Send-Message-to-Group-Chat](https://open.seatalk.io/docs/Send-Message-to-Group-Chat)
4. \[Overview of supported message formats\] [https://open.seatalk.io/docs/format-a-message](https://open.seatalk.io/docs/format-a-message)

# **15 Sept 2023**

### **Bot Enhancement**

1. New API to [get quoted message content by message ID](https://open.seatalk.io/docs/Get-Message-by-Message-ID)

# **14 Sept 2023**

### **Approval Center - Create / Update Approval Item API**

1. The**app\_path** field is now an optional field to cater for lightweight approval scenarios.
2. Please take note that **app\_path** field is still requiredif the **action\_button** field is set to 2.
3. The doc of<u>[Create Approval Item API](https://open.seatalk.io/docs/create-approval-item)</u>and<u>[Update Approval Item API](https://open.seatalk.io/docs/update-approval-item)</u>has been updated accordingly.

# **7 Sept 2023**

### **Bot Enhancement**

1. New API to support [get Bot's joined group chat list](https://open.seatalk.io/docs/Get-Joined-Group-Chat-List)
2. New API to support [get Bot's subscriber list](https://open.seatalk.io/docs/Get-Bot-Subscriber-List)
3. Bot can [send Image messages to subscribers in 1-on-1 chat](https://open.seatalk.io/docs/messaging_send-message-to-bot-subscriber_#Send%20an%20Image%20Message-3)

# **5 July 2023**

### **Group Chat Bot Capability**

1. Support bots to interact with users in group chats. See more at<u>[Quickly build a Bot](https://open.seatalk.io/docs/quickly-build-a-bot)</u>for more detail.
2. This capability iseffective from SeaTalk client version 3.33.

# **16 June 2023**

### **Configuration**

RN SDK -[getSystemInfo](https://open.seatalk.io/docs/rn-sdk-apis_configuration)

* New parameter called '**theme**' added to provide SeaTalk client appearance settings for RN Apps.

RN SDK - onListenerThemeChange

* New method added to provide a listener in RN Apps on SeaTalk client appearance changes.

# **17 March 2023**

### **Workspace App**

RN SDK -[Calendar Picker API](https://open.seatalk.io/docs/rn-sdk-apis_widgets#Calendar%20Picker-4)

* Two new parameters called '**selectableDateStart**' and '**selectableDateEnd**' are added to support cases when certain dates need to be disabled from selection.

# **29 December 2022**

### **Server API**

[Send Service Notice (New)](/docs/messaging_send-service-notice)

* A new parameter called "**usable\_platform**" is added to support cases where a service notice message is usable on mobile/desktop platforms only, effective from SeaTalk client version 3.27 for iOS and Desktop and version 3.28 for Android

# **1 December 2022**

### **App Link**

* App Link, a new common capability, supports SeaTalk users to enter a specific app page quickly through a link generated with standard protocols either in or out of the SeaTalk app. See[App Link Overview](/docs/app-link-overview) for more detail.
* This capability iseffective from SeaTalk client version 3.26.

# **16 September 2022**

### **General Changes**

Open Platform Documentation

* You can now search through our documents by keywords

### **SeaTalk Developer Tool**

* Debug your web app through our[SeaTalk Developer Tool](https://open.seatalk.io/docs/seatalk-developer-tools), available for Mac and Windows

### **Workspace App**

General

* IMPORTANTWe will update[Top Navigation Bar system](https://open.seatalk.io/docs/top-navigation-bar)for both RN App and Web App in**13 October**for a unified UI/UX experience. New Top Navigation Bar will be provaided by SeaTalk Native instead of RN App. Existing RN Apps will need to adapt to this new top navigation bar system as soon as possible by removingthe[<NavBarPage>](https://open.seatalk.io/docs/rn-sdk-apis_widgets#Navigation%20Bar-2)component from your code.

Web SDK

* New SOP Web SDK Demo App to allow you test and experiment our Web SDK APIs on SeaTalk Client
* New[Scan QR Code API](https://open.seatalk.io/docs/web-sdk_scan-code)to allow user scan QR Codes using their device camera

RN SDK

* New[Media File Picker API](https://open.seatalk.io/docs/choose-media-file)to allow user upload image & video through album and device camera
* New[Scan QR Code API](https://open.seatalk.io/docs/rn-sdk-apis_scanner)to allow user scan QR Codes using their device camera

### **Server API**

General

* IMPORTANTStandardize error handling for all existing APIs, you can find new error code in[Error Code Reference](https://open.seatalk.io/docs/reference_error-code)doc or each API document for the updated error codes

Was this document helpful?

No

Yes