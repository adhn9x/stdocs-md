# Storage

# Storage

This package provides persistent storage for your RN app.

## function createStore

#### function

```javascript
StoreClient.createStore(scopeID: string = ''): IStore Copy
```

### Description

Builder function to create a store object

### Parameters

|Parameter|Type|Description|Default Value|
|---|---|---|---|
|appID|string|Your RN app's appID|N/A|
|scopeID|string|A string to represent your defined scope for the store. The store is isolated by app and user (See Sample Usage below for more info)|Empty|

## object Store

Object returned by the store builder function, that provides persistent storage capabilities. The API is designed to resemble a typical key-value store.

### methods`set`

```javascript
set(key: string, value: string) => Promise<void> Copy
```

### **Description**

Stores the*value*, associated with the provided*key*. It will override any existing value.

### **Parameters**

|Parameter|Type|Description|
|---|---|---|
|key|string|The key to access this value|
|value|string|The value you want to store, associated with this key|

### methods`get`

```javascript
get(key: string) => Promise<string | null> Copy
```

### **Description**

Retrieves the*value*associated with this*key*, if any. Will return null if none.

### **Parameters**

|Parameter|Type|Description|
|---|---|---|
|key|string|The key to access this value|

### methods`remove`

```javascript
remove(key: string) => Promise<void> Copy
```

### **Description**

Removes the*value*associate with this*key*, if any.

### **Parameters**

|Parameter|Type|Description|
|---|---|---|
|key|string|The key to access this value|

## **interface**`IStore`

Interface that provides persistent storage capabilities. The API is designed to resemble a typical key-value store.

### methods`set`

```javascript
set(key: string, value: string) => Promise<void> Copy
```

### **Description**

Stores the*value*, associated with the provided*key*. It will override any existing value

### **Parameters**

|Parameter|Type|Description|
|---|---|---|
|key|string|The key to access this value|
|value|string|The value you want to store, associated with this key|

### methods`get`

```javascript
get(key: string) => Promise<string | null> Copy
```

### **Description**

Retrieves the*value*associated with this*key*, if any. Will return null if none.

### **Parameters**

|Parameter|Type|Description|
|---|---|---|
|key|string|The key to access this value|

### methods`remove`

```javascript
remove(key: string) => Promise<void> Copy
```

### **Description**

Removes the*value*associate with this*key*, if any.

### **Parameters**

|Parameter|Type|Description|
|---|---|---|
|key|string|The key to access this value|

## **Samples**

### **Store Sample Usage**

```javascript
// Until v0.0.37
// Use the StoreBuilder to get a Store object
// const store = Store("your_app_id")

// Since v0.1.0
const sdkClient: SDKClient = // get SDKClient
const store: IStore = sdkClient.store.createStore()

// Set some value here
await store.set("awesome_key", "awesome_value")

// Do some more work

// Retrieve the same value
let value = await store.get("awesome_key")
console.log(value) // Prints "awesome_value"

// Override the previous value
await store.set("awesome_key", "super_value")
let value = await store.get("awesome_key")
console.log(value) // Prints "super_value"

// Store objects by stringifying them
let myObject = {
    key1: 'special_value',
    key2: 'another_value',
    key3: {
        nested_key1: 'nested_value1'
    }
}

// Retrieve and use object
await store.set("cool_object", JSON.stringify(myObject))
let objString = await store.get("cool_object")
let myRetrievedObject = JSON.parse(objString)
console.log(myRetrievedObject.key1) // Prints "special_value"

// Delete values
await store.remove("awesome_key")
let maybeValue = store.get("awesome_key")
console.log(maybeValue === null) // Prints true Copy
```

### **Store Scoping Sample Usage**

```javascript
// Until v0.0.37
// Use the StoreBuilder to get a 'scoped' store object
// const userStore = Store("your_app_id", "user_id")

// Since v0.1.0
const sdkClient: SDKClient = // get SDKClient
const userStore: IStore = sdkClient.store.createStore('user_id')

// Usage is the same as before
await userStore.set("username", "brendan_eich")

// Do some more work

// Retrieve the same value
let username = await userStore.get("username")
console.log(username) // Prints "brendan_eich"

// However, this value only exists in the store scope of this 'user_id'
// So if you create a store with a different scope, you will not be able to access this value
// For example, let's create a globally scoped store and try to get the value for 'username'
const globalStore = Store("your_app_id")
console.log(await globalStore.get("username")) // Prints null, since the username was only inserted in the 'user_id' scoped store

// Therefore, you can be assured that only stores with the same scopeID can manipulate the same data
await globalStore.remove("username")
let storeUsername = await userStore.get("username")
console.log(storeUsername) // Prints "brendan_eich"

// In this manner, you can scope your storage in any manner you see fit for your app
// Another example is to have a sessionStore, to store information regarding the last session
const sessionStore = Store("your_app_id", "session")

await sessionStore.set("lastLoginTime", someLoginTime)

let sessionInfo = JSON.parse(await sessionStore.get("sessionInfo"))

// Do some work with sessionInfo Copy
```

Was this document helpful?

No

Yes