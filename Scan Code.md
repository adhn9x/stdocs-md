# Scan Code

Scan a code and return the result.

# Support

|App Capability|Android|iOS|PC|SDK Version|
|---|---|---|---|---|
|Web|✅|✅|❌|1.5.0|

# Parameters

## Input(Object object)

|Name|Type|Required|Default|Description|
|---|---|---|---|---|
|codeType|string\[\]|No|'qrCode'|The code scanning type. Multiple types of codes can be inputted. Available types include: - qrCode: QR Code|

## Output(Object object)

|Name|Type|Description|Example|
|---|---|---|---|
|wasCancelled|boolean|True if the native page was dismissed before the scanner could recognize a valid code. False otherwise||
|type|string|The type of code that was recognised. Available values include: - user - externalLink - appLink - chat - others||
|result|string|The scanned value from the code||
|errCode|number|The error code||
|errMsg|string|The error message||

# Example

```go
import {
    scanCode
}
from '@seatalk/web-app-sdk';


scanCode({
        codeType: ['qrCode'],
    })
    .then((res) => {
        console.log(res);
    })
    .catch((err) => {
        console.log(err);
    }); Copy
```

Was this document helpful?

No

Yes