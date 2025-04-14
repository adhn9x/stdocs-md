# Application

This package provides API for an RN application to register itself in our mobile client.

# interface ISeaTalkApplication

Representation of a SeaTalk RN application.

## Property

|Name|Type|Description|SDK Version|
|---|---|---|---|
|rootPage|string|Module name of the page to be displayed when user enters from the SeaTalk mobile's discover page.|0.0.37|

## Method resolveRoute

```javascript
resolveRoute(path: string) => string | undefined Copy
```

### Description

Given a path, this method should return the corresponding page component's module name. If the path does not match, it should return undefined.

NOTE: This is mainly used for navigation purpose. For details, please refer to Navigator.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|path|Yes|string|The path to be resolved|

## Method registerPages

```javascript
registerPages(registry: IPageRegistry) Copy
```

### Description

This method is a hook provided for the application to register all the page components, similar to AppRegistry's role.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|registry|Yes|IPageRegistry||

### Sample:

```javascript
registerPages(registry) {
    registry.registerPage("ModuleName", () => MyPage);
} Copy
```

# interface IPageRegistry

Similar to AppRegistry.

## Method registerPages

```javascript
registerPage(pageName: string, provider: () => ComponentType) Copy
```

### Description

Registers a page component to the react-native side. Similar to AppRegistry.registerComponents.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|pageName|Yes|string|Self-defined module(page) name of the page. It will be scoped within your own application bundle and needs to be unique within the RN application. However, two different RN application with different appID can have the same pageName.|
|provider|Yes|() => ComponentType|Generator for the component to be registered.|

## Sample:

```javascript
registerPages(registry) {
    registry.registerPage("ModuleName", () => MyPage);
} Copy
```

# interface STAppRegistry

A registry containing all the registered SeaTalk RN applications.

## Method getInstance

```javascript
SDKClient.getInstance(app: ISeaTalkApplication) Copy
```

### Description

Registers an application to the registry.

### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|app|Yes|ISeaTalkApplication||

### Sample

```javascript
class MyApp implements ISeaTalkApplication {
    appID: string = 'appID';
    rootPage: string = 'LIST_VIEW';

    registerPages(registry) {
        registry.registerPage('LIST_VIEW', () => MyPage);
    }

    resolveRoute(path: string) {
        switch (path) {
            case '/':
                return 'LIST_VIEW';
            default:
                return undefined;
        }
    }
}

// Until v0.0.37// STAppRegistry.registerApp(new MyApp())// Since v0.1.0const sdkClient: Promise<SDKClient> = SDKClient.getInstance(new MyApp()); Copy
```

Was this document helpful?

No

Yes