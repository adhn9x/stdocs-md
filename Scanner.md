# Scanner

This package provides an API to push a new QR code scanner page and returns the content of the QR code after the scanning succeeds.

# **namespace Scanner**

### Method

```javascript
scanQRCode(scannerConfig: ScannerConfig, pushOption: PushOption) => Promise<ScannerResult> Copy
```

### Parameters

|Name|Type|Description|
|---|---|---|
|scannerConfig|ScannerConfig|Config for customizing scanner behavior, such as recognized QRCode types|
|pushOption|PushOption|Refer to Navigator Module|

## interface ScannerConfig

Configuration for customizing scanner behaviors.

### Properties

|Name|Type|Description|
|---|---|---|
|supportedTypes|ScannerType\[\]|Only these types will be recognized by the QR code scanner, thus providing a way to control the scope of the Scanner.|

## enum ScannerType

Type of QR codes to be recognized. Each scanner type has a corresponding payload type, as described below.

**Properties**

|Name|Type|Description|Payload Type|Payload Description|
|---|---|---|---|---|
|user|string|Allows scanning a SeaTalk user's profile QR code.|string|SeaTalk userID|

## interface ScannerResult

**Properties**

|Name|Type|Description|
|---|---|---|
|wasCancelled|Boolean|Represents whether the scanner completes or was cancelled by the user|
|type|ScannerType|Type of the result|
|payload|string|A JSON string representation of the payload whose type is as defined by the ScannerType above.|

# Error Specification

When the Promise returned by the**scanQRCode**API is rejected, you may access the 'code' property of the returned value to get more information. Detailed below are the Error Codes and their semantics.

|Error Code|Description|Notes|
|---|---|---|
|1|SDK Error|N/A|
|2|No Camera Permission|App was not granted appropriate permissions|
|3|Unknown Scanner Type|Tried to scan a QR Code not in the provided supportedTypes of ScannerConfig|
|4|Unknown User|Scanner QR code of an Unknown SeaTalkUser|

# Sample

```javascript
Scanner.scanQRCode(
    {
        supportedTypes: ['user'],
    },
    {
        pushType: 'normal',
    }
).then((result) => {
    if (result.wasCancelled) {
        // cancelled
    } else if (result.type === 'user') {
        const userID = result.payload;
        // My own logic
    } else {
        // Handle other QR type. Should not come to this branch since only 'user' scanner type is specified to be supported.
    }
}); Copy
```

Was this document helpful?

No

Yes