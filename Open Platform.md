# Open Platform

This package provides access to the SeaTalk open platform APIs. Particularly, it allows your app to be authenticated on the SeaTalk open platform.

# namespaceOpenAuth

Open platform API client.

## Method fetchAuthToken

```javascript
OpenPlatformClient.fetchAuthToken(): Promise<string> Copy
```

### Description

Request for a short-lived authentication token from the SDK. This token can be verified by the open platform for establishing a session.After an RN app has acquired this token, it's expected to send this token directly to its application server, which will then forward it to the open platform server to get verified.NOTE: Do NOT cache this token, as it's short-lived. If need a new token can request again. However, there's a rate limit for the request per application. Do NOT call this unnecessarily.

### Parameters

|Name|Type|Description|
|---|---|---|
|appID|string|You app's app id|
|completion|(token?: string, error?: Error) => void|Callback after the Auth token is fetched|

Was this document helpful?

No

Yes