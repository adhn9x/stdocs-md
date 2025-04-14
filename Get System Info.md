# Get System Info

Get a user's SeaTalk setting and device settings.

# Support

|App Capability|Android|iOS|PC|
|---|---|---|---|
|Web|✅|✅|✅|

# Parameters

## Input

None.

## Output(Object object)

|Name|Type|Description|Example|
|---|---|---|---|
|seatalkVersion|string|The version of the SeaTalk client|"v3.9.0"|
|sdkVersion|string|The version of the Web SDK|" v0.10.0 "|
|language|string|The display language of SeaTalk|" en "|
|deviceID|string|The unique identifier of the device|" 4AFFB70D-2214-4A46-9710-EB83F485EB8C "|
|deviceModel|string|The model name of the device|"PC"|
|deviceOS|string|The operating system of the device|" Win32 "|
|deviceOrientation|string|The orientation of the device. Possible values are: landsacpe \| protrait|"landscape"|
|devicePixelRatio|number|The pixel ratio of the device|1.25|
|timezone|string|The time zone of the device, in GMT format|"GMT+8"|
|screenWidth|number|The width of the display device in pixel|1536|
|screenHeight|number|The height of the display device in pixel|864|
|windowWidth|number|The width of t he Web App window|1466|
|windowHeight|number|The height of t he Web App window|762|
|theme|string|The current system theme|"light"|
|is24HourTime|boolean|Whether the user is using the 24-hour clock for time display|true|

# Example

```javascript
import { getSystemInfo } from '@seatalk/web-app-sdk';

getSystemInfo()
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
 Copy
```

Was this document helpful?

No

Yes