# List of Events

This document lists out all the available events for bot users. See [Event Callback](/docs/server-apis-event-callback) for how event callback works on SeaTalk Open Platform and how to configure the callback URL for your app.

|Category|Event Name|Description|
|---|---|---|
|Messaging|(Deprecated) new\_bot\_subscriber|(Deprecated) When a user has subscribed to the bot|
||message\_from\_bot\_subscriber|When a message is received from a bot user in 1-on-1 chat|
||new\_mentioned\_message\_from\_group\_chat|When a group member mentions the bot using '@' in a text message in a group chat.|
||interactive\_message\_click|When a callback button on an interactive message card is clicked by a user|
|Group Chat|bot\_added\_to\_group\_chat|When a bot user has added the bot to a group chat|
||bot\_removed\_from\_group\_chat|When a bot has been removed from a group chat due to manual removal or group disbandment.|

Was this document helpful?

No

Yes