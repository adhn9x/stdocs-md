# Navigator

This package provides inter-page navigation service to an RN app.

## namespace Navigator

# Method push

```javascript
NavigatorClient.push(path: string, props: any, options: PushOption): Promise<boolean> Copy
```

### Description

Push a new page corresponding to the (appID, path) with the configuration provided by PushOption.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|path|Yes|string|path of the target page as defined in its application's resolveRoute.|
|props|No|any|props to be passed to the target page. Defaults to undefined.|
|options|No|PushOption|Default pushType: 'normal'|

### Example:

```javascript
// Until v0.0.37// Navigator.push('appID', '/path', undefined, { pushType: 'modal' })// Since v0.1.0
const sdkClient: SDKClient = sdkClient.navigator.push('/path', undefined, {
// get SDKClientpushType: 'modal',
}); Copy
```

# Method redirect

```javascript
NavigatorClient.redirect(path: string, props: any, options: PushOption): Promise<boolean> Copy
```

### Description

Redirect to a new page corresponding to the path with the configuration provided by PushOption.Redirect means closing current page and navigating to a new page.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|path|Yes|string|path of the target page as defined in its application's resolveRoute.|
|props|No|any|props to be passed to the target page. Defaults to undefined.|
|options|No|PushOption|Default pushType: 'normal'|

### Example:

```javascript
const sdkClient: SDKClient = sdkClient.navigator.redirect('/path', undefined, {
    // get SDKClientpushType: 'modal',
}); Copy
```

# Method pop

```javascript
NavigatorClient.pop(data?: string): Promise<boolean> Copy
```

### Description

Pops the top-most page on the navigation stack and reveals the second last page.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|data|No|string|Data to be passed back to the revealed page's pageReceivedData. Defaults to undefined.|

### Example:

```javascript
// Until v0.0.37
// Navigator.push('appID', '/path', undefined, { pushType: 'modal' })
// Navigator.pop()

// Since v0.1.0
const sdkClient: SDKClient = sdkClient.navigator.push('/path', undefined, {
    // get SDKClientpushType: 'modal',
});
sdkClient.navigator.pop(); Copy
```

# Method navigateBack

```javascript
NavigatorClient.navigateBack(option?: NavigateBackOption): Promise<boolean> Copy
```

### Description

Pops the top-most pages according to the parameter delta on the navigation stack and reveals the remaining top most page.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|option|No|NavigateBackOption|Addon parameters including delta|

### Example:

```javascript
const sdkClient: SDKClient = sdkClient.navigator.push('/path', undefined, {
    // get SDKClientpushType: 'modal',
});
sdkClient.navigator.push('/path002', undefined, { pushType: 'modal' });
sdkClient.navigator.navigateBack({ delta: 2, data: "I'm Back" }); Copy
```

## interface PushOption

Options to configure the push style.

### Property

|Name|Type|Description|
|---|---|---|
|pushType|PushType|Controls the type of animation used to push the new page. See Below.|

## enum PushType

Push animation type.

### Property

|Value|Description|
|---|---|
|normal|Default push type that pushes a page from right to left. \[iOS\] Equivalent to UINavigationController.push|
|modal|Pushes the new page in a modal style. \[iOS\] Equivalent to UIViewController.present|

## interface NavigateBackOption

Options to configure the navigateBack API.

### Property

|Name|Type|Description|
|---|---|---|
|delta|number|Number of pages to pop, accept positive integer value. When the value passed in is larger than the number of items in the page stack, will return to the previous app's last page in stack. If there is no previous page, will close all the pages and return to SeaTalk Workspace Tab|
|data|string|Data to be passed back to the revealed page's pageReceivedData. Defaults to undefined.|

Was this document helpful?

No

Yes