# Logger

Just a Logger. It's optional but recommended for an RN App.We do have plans to integrate this with the SeaTalk bug report system in future versions of the SDK, so when user submits a bug report to SeaTalk we can forward their logs to the application developer. Therefore, we strongly recommend all RN App to use this package for logging purpose.

## function Logger

Builder function to create a logger object.

### Parameters

|Name|Type|Description|Default Value|SDK Version|
|---|---|---|---|---|
|filename|string \| undefined|File name to be put into each log message.|undefined||
|packagename|string \| undefined|Package name to be put into each log message.|undefined||
|minLevel|LogLevel|Threshold for log message filtering, following the order of debug < verbose < info < warning < error Logs below the minLevel will NOT be shown.|DEV mode: verbose PROD mode: info||

Example

```javascript
// Provide a package level logger 
builderconst PackageLogger = (filename: string) => {
    return Logger(filename, 'my-app');
};

// In your ListView.js fileconst logger = PackageLogger('ListView');

// ...
logger.debug('Some log message');
logger.verbose('Some log message');
logger.info('Some log message');
logger.warning('Some log message');
logger.error('Error encountered'); Copy
```

Was this document helpful?

No

Yes