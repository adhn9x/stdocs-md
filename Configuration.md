# Configuration

# Method getSystemInfo

```javascript
getSystemInfo(option: ISystemInfoOption): Promise<Record<string, any>> Copy
```

### Description

Get specific settings of the Seatalk Client. e.g. is24HourTime, themeIt will resolve with key-value data of specific settings.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|option|Yes|ISystemInfoOption|Options to configure getSystemInfo|

### Interface ISystemInfoOption

|Name|Required|Type|Description|
|---|---|---|---|
|keys|Yes|String Array|Settings you need to fetch from client. e.g. \[ 'is24HourTime', 'theme' \]|

### Supported setting keys

|Key|Return Type|Description|Return Value|
|---|---|---|---|
|is24HourTime|String|Whether the system time display is in 24-hour format or not|"true" \| "false"|
|theme|String|SeaTalk client's current appearance setting|"light" \| "dark"|
|system (iOS only)|String|The operating system of the device|e.g. "16.0.0"|

### Example:

```javascript
import { Config, getSystemInfo } from '@seatalk-rn/sdk-config';

// Since v0.1.0
let option = {
    keys: ['is24HourTime', 'theme'],
};
getSystemInfo(option).then((res: any) => {
    console.log(`is24HourTime: ${res.is24HourTime}`, `theme: ${res.theme}`);
}) Copy
```

### Error Codes

|Code|Scenario|
|---|---|
|1|Input parameter is empty.|
|2|There's an unsupported setting key parameter detected in the keys array.|

# Method onListenerThemeChange()

```javascript
onListenerThemeChange() Copy
```

### Description

API Subsciption to notify RN App at the pageView level when the appearance has changed

|Field|Return Type|Description|Return Value|
|---|---|---|---|
|theme|String|SeaTalk client's updated appearance setting|"light" \| "dark"|

### Example:

```javascript
(await sdkClient).appearanceEmitter.onListenerThemeChange((body: any) => {
    this.setState({ theme: body.theme || "light" });
}); Copy
```

Was this document helpful?

No

Yes