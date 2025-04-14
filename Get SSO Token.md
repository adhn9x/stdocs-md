# Get SSO Token

Get a Single-Sign-On (SSO) token of a user's SeaTalk account.

# Support

|App Capability|Android|iOS|PC|
|---|---|---|---|
|Web|✅|✅|✅|

# Parameters

## Input

None.

## Output(String token)

|Name|Type|Description|
|---|---|---|
|token|string|The SSO token|

# Example

```javascript
import { getSSOToken } from '@seatalk/web-app-sdk';

getSSOToken()
.then((token) => {
    console.log(token);
})
.catch((err) => {
    console.log(err);
}); Copy
```

Was this document helpful?

No

Yes