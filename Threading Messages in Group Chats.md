# Threading Messages in Group Chats

> ***Effective Date:  
> **API Updates:** *Effective from 11 June 2024.  
> **Interacting with Bots in Threads on SeaTalk App**: Requires SeaTalk App version 3.44.5 or above, releasing on 14 June 2024, for full functionality.****

# **Introduction**

In SeaTalk, certain messages generate discussions that lead to replies, forming a thread. A threaded message, along with its replies, allows for organised and focused conversations.

Bots can read and write messages in threads with ease. Before diving into the implementation details, let's cover some thread terminology:

* **Thread**: The collection of a root message and its replies.
* **Root Message**: A message with replies, initiating a thread.
* **Thread Reply**: A reply to the root message.
* **Threaded Message**:Any message within a thread, whether root or reply.
* **Unthreaded Message**:A message that has not yet received any replies.

# **Identifying Threads**

How do you know when the message you've received or retrieved is part of a thread? Here’s how to navigate:

* **Detect a Threaded Message**: Look for a thread\_id value in the message object. The presence of this value indicates the message is part of a thread.
* **Identify a Root Message**: Compare the thread\_id and message\_id values. If they are equal, the message is a root message.
* **Identify a Thread Reply**: If the thread\_id and message\_id values differ, the message is a reply.

A root message retains a thread\_id value even if all its replies have been deleted.

See the sample code snippet below:

```json
// Below is a thread reply
{
    "message_id":"kashfefrhnedf",
    "quoted_message_id":"",
    "thread_id":"qwertyuiop", // Different from the message_id
    "sender":{
        "seatalk_id":"91234567",
        "employee_code":"abcdefg"
    },
    "message_sent_time":1687764109,
    "tag":"text",
    "text":{
        "plain_text":"Hello, kindly be reminded to update the invitation, thx.",
        "mentioned_list":[]
    }
} Copy
```

# **Bot Interactions with Threads**

## **1.Replying in a Thread**

Bots can reply to a specific thread by including the thread\_id in their request. This maintains context and relevance within threaded conversations. Please note that tagging everyone (@all) is not allowed when replying in a thread.

**Key Actions:**

* Use the thread\_id to identify the thread.
* Send a reply that will be nested within the specified thread.

Learn more about**<u>[Send a Message to Group Chat](https://open.seatalk.io/docs/Send-Message-to-Group-Chat)</u>**.

## **2\. Getting Mentioned in a Thread**

Bots can be notified when they are mentioned in a thread. This notification will include the thread\_id, allowing the bot to understand the context of the mention and respond appropriately.

**Key Actions:**

* Listen for the mention event callback that includes the thread\_id.
* Process the message and respond within the same thread to maintain context and avoid confusion for the end user.

Learn more about**<u>[Event: New Mentioned Message From Group Chat](https://open.seatalk.io/docs/event_new_mentioned_message_from_group_chat)</u>**.

## **3\. Retrieving a Thread by Thread ID**

Bots can retrieve the entire conversation thread using the thread\_id. This is useful for analysing the conversation history or providing contextual responses.Note that only replies sent in the past 7 days will be available.

**Key Actions:**

* Use the thread\_id to fetch the entire thread.
* Analyse messages within the thread to maintain context.

Learn more about**[Get Thread by Thread ID](https://open.seatalk.io/docs/Get-Thread-by-Thread-ID)**.

# **Example Use Cases**

**Customer Support Bot**

A customer support bot can use threads to manage separate customer queries, replying in the same thread to maintain context and continuity.

**Project Management Bot**

A project management bot can be tagged in threads related to specific tasks, allowing it to provide updates or fetch relevant information based on the ongoing discussion.

Was this document helpful?

No

Yes