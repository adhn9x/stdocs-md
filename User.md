# User

# User

This package provides API(s) governing actions related to SeaTalk users

## namespace UserModule

#### function`navigateToUserProfile`

```markup
navigateToUserProfile(userID: String) => Promise<boolean> Copy
```

### Description

This API enables the caller to navigate to a user's SeaTalk profile page using the corresponding userID.The promise will resolve with false if there was any problem while loading the user profile, and true in all other cases

### Parameters

|Parameter|Type|Description|
|---|---|---|
|userID|string|SeaTalk userID|

Was this document helpful?

No

Yes