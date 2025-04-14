# SDK Clients

This package provides a unified`SDKClient`to access the SDK APIs provided by SeaTalk. This is the main entry point of your app, and will provide access to many of the APIs defined in this SDK.**Note: If you have been developing using SeaTalk SDK 0.0.37 or earlier,**with the introduction of`SDKClient`, all APIs that requires`app id`are deprecated, and are replaced by the corresponding`XXXClient`s defined inside this package.

# class SDKClient

The class that provides unified access for the SeaTalk RN SDK APIs. The same`SDKClient`instance obtained from`SDKClient.getInstance(app: ISeaTalkApplication)`should be shared within the same RN App.

## Property

|Name|Type|Description|SDK Version|
|---|---|---|---|
|navigator (readonly)|NavigatorClient|The client that manages navigation APIs|>= 0.1.0|
|openPlatform (readonly)|OpenPlatformClient|The client that manages Open Platform APIs|>= 0.1.0|
|share (readonly)|ShareClient|The client that manages share APIs|>= 0.1.0|
|storage (readonly)|StorageClient|The client that manages APIs to access the key-value store|>= 0.1.0|
|fileSystem (readonly)|FileSystemClient|The client that manages APIs to access the file system|>= 0.1.0|

## Method

```javascript
getInstance(app: ISeaTalkApplication): Promise<SDKClient> Copy
```

## Description

Registers a SeaTalk RN application. Returns a`Promise`that resolves to the`SDKClient`that can be used to query SDK APIs.

**NOTE**: Each RN application should only call this method**ONCE**, inside the file that will be used as the**ENTRY FILE**when bundling (e.g., index.ts). The returned`Promise`(and the resolved`SDKClient`) is intended to be**SHARED**across this RN application. Components that needs to query the RN APIs should obtain the same instance first, so it is advised to save the returned instance somewhere so that other classes/functions can access later. Within the execution of this function, the app's`rootPage`and`registerPages()`will be called.

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|app|Yes|ISeaTalkApplication|The application to be registered|

## Sample

```javascript
// index.ts
import { setSDKClient } from './client';
import { ISeaTalkApplication } from '@seatalk-rn/sdk-application';
import { SDKClient } from '@seatalk-rn/sdk-client';

class MyApp implements ISeaTalkApplication {
    // implementation
}

const sdkClient = SDKClient.getInstance(new MyApp());
setSDKClient(sdkClient);

// client.tsimport { SDKClient } from '@seatalk-rn/sdk-client';

let sdkClient: Promise<SDKClient>;
export async function getSDKClient(): SDKClient {
    // This can be invoked multiple times since it's OK to await an already-resolved Promisereturn await sdkClient;
}
export function setSDKClient(client: Promise<SDKClient>) {
    sdkClient = client;
}

// use-client.tsimport { getSdkClient } from './client';

async function useSdkClient() {
    const client = await getSDKClient();
    // use client from here on
} Copy
```

# class NavigatorClient

The client that manages navigation. Replaces the`Navigator`namespace in`@seatalk-rn/sdk-navigator`to remove the`app id`usage.

## Method

```javascript
push(path: string, props: any = undefined, options: PushOption = { pushType: 'normal' }): Promise<boolean> Copy
```

## Description

Push a new page corresponding to the`path`with the configuration provided by`PushOption`.

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|path|Yes|string|path of the target page as defined in its application's resolveRoute|
|props|No|any|props to be passed to the target page. Defaults to undefined .|
|options|No|PushOption|See Below. Defaults to { pushType: 'normal' }|

## Method

```javascript
pop(data: string | undefined = undefined): Promise<boolean> Copy
```

## Description

Pops the top-most page on the navigation stack and reveals the second last page.

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|data|No|string|Data to be passed back to the revealed page's pageReceivedData. Defaults to undefined .|

## Sample

```javascript
const sdkClient: SDKClient = sdkClient.navigator.push('/path', undefined, {
    // get SDKClient
    pushType: 'modal',
});
sdkClient.navigator.pop(); Copy
```

# class OpenPlatformClient

The client that manages Open Platform APIs. Replaces the`OpenAuth`module in`@seatalk-rn/sdk-navigator`package to remove the`app id`usage.

## Method

```javascript
fetchAuthToken(): Promise<string> Copy
```

## Description

Request for a short-lived authentication token from the SDK. This token can be verified by the open platform for establishing a session. After an RN app has acquired this token, it's expected to send this token directly to its application server, which will then forward it to the open platform server to get verified.**NOTE**: Do NOT cache this token, as it's short-lived. If need a new token can request again. However, there's a rate limit for the request per application. Do NOT call this unnecessarily.

# class ShareClient

The client that manages share APIs. Replaces the`shareAppLink`function in`@seatalk-rn/sdk-share`to remove the`app id`usage.

## Method

```javascript
shareAppLink(content: ShareAppLinkContent): Promise<void> Copy
```

## Description

Launches a new page to allow sharing information specified in`content`to chat. The shared content will be a message which once clicked, the app will navigate to the page specified in`content.url`. The returned`Promise`will be rejected with`ShareAppLinkError`when there are errors.

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|content|Yes|ShareAppLinkContent|Data describing the content to be shared|

## Sample

```javascript
import { shareAppLink, ShareAppLinkErrorCodes } from '@seatalk-rn/sdk-share'async onPressShareAppLink(): Promise < void> {
    try {
        const sdkClient: SDKClient = // get SDKClientawait sdkClient.share.shareAppLink({
        title: 'Share App Link',
        subtitle: 'This is a subtitle',
        url: 'seatalk://application/rn/appID/home',
        imageUrl: 'https://is2-ssl.mzstatic.com/image/thumb/Purple114/v4/4f/17/73/4f177329-378a-87ac-fad2-8e4a6dc302f3/AppIcon-0-0-1x_U007emarketing-0-0-0-4-0-0-sRGB-0-0-0-GLES2_U002c0-512MB-85-220-0-0.png/230x0w.png'
    })
} catch (error) {
    switch (error.code) {
        case ShareAppLinkErrorCodes.SDK_ERROR:
            HUD.hudShowError(`ShareAppLink: SDK_ERROR, ${error.message}`)
            breakdefault:
            HUD.hudShowError(`ShareAppLink: ${error.code}, ${error.message}`)
    }
}
    } Copy
```

# class StorageClient

The client that manages APIs to access the key-value store. Replaces the`Store`builder function in`@seatalk-rn/sdk-storage`to remove the`app id`usage.

## Method

```javascript
createStore(scopeID: string = ''): IStore Copy
```

## Description

Builder function to create an IStore object

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|scopeID|No|string|A string to represent your defined scope for the store. Defaults to ''|

## Sample

```javascript
const sdkClient: SDKClient = // get SDKClient
const userStore: IStore = sdkClient.store.createStore('user_id')

// Usage is the same as before
await userStore.set("username", "brendan_eich")
    ..
// Do some more work
..

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
// Another example is to have a sessionStore, to store information regarding the last sessionconst sessionStore = Store("your_app_id", "session")

await sessionStore.set("lastLoginTime", someLoginTime)

let sessionInfo = JSON.parse(await sessionStore.get("sessionInfo"))
    ..
// Do some work with sessionInfo
.. Copy
```

# class FileSystemClient

The client that manages APIs to access the file system. Find more detailed APIs [here](https://confluence.garenanow.com/display/SEATALK/3.14+SDK-Filesystem#id-3.14SDKFilesystem-IFileManager).

## Properties

|Name|Type|Description|SDK Version|
|---|---|---|---|
|fileManager (readonly)|IFileManager|An IFileManager that provides APIs to create, access, modify and delete files/directories.|>= 0.1.0|

# class PickerClient

The client that manages APIs to access the image file system. Find more detailed APIs [here](https://confluence.shopee.io/display/STKSZ/%5BTemp%5D+New+Image+Picker+API).

## Method

```javascript
selectImagesFiles(maxNumberOfImages: number): Promise<ImagePickerFileResult> Copy
```

## Description

Launches a new page to select the images from the on-device album. When the returned`Promise`is rejected, it will be rejected with an`ImagePickerError`**NOTE**: The operations on the native side can be time-consuming, so it's recommended for the app to show a loading hint using HUD.hudShowLoading()

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|maxNumberOfImages|Yes|number|Integer that specifies how many images can be selected at most at the same time|

## Sample

```javascript
import { ImagePicker, ImagePickerError } from '@seatalk-rn/sdk-widgets'

async onPressImageFilePicker(): Promise < void> {
    HUD.hudShowLoading();
    try {
        const result = await (await sdkClient).picker.selectImagesFiles(5);
        HUD.hudHide();
        if(!result.wasCancelled) {
        logger.info(`onPressImageFilePicker success: ${JSON.stringify(result)}`);
        const images = await Promise.all(
            result.images.map(async (image) => ({
                fileUri: await (await sdkClient).fileSystem.fileManager.getFullURI(image.fileInfo),
                width: image.width,
                height: image.height,
            }))
        );
        await(await sdkClient).navigator.push('/imageviewer', { images: images });
    } else {
        HUD.hudShowError('Cancelled');
        logger.info('onPressImageFilePicker cancelled');
    }
} catch (error) {
    HUD.hudHide();
    logger.error(error);
    switch (error.code) {
        case ImagePickerError.SDK_ERROR: {
            HUD.hudShowError(`ImageFilePicker: SDK_ERROR, ${error.message}`);
            break;
        }
        case ImagePickerError.NO_PERMISSION: {
            HUD.hudShowError(`ImageFilePicker: NO_PERMISSION, ${error.message}`);
            break;
        }
        default:
            HUD.hudShowError(`ImageFilePicker: ${error.code}, ${error.message}`);
    }
}
} Copy
```

## Method

```javascript
selectDocument(maxFileSizeInKiloBytes: number, supportedTypes: [DocumentTypeString]): Promise<DocumentPickerResult> Copy
```

## Description

Triggers the native Document Picker UI. Currently only supports picking only one document.

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|maxFileSizeInKiloBytes|Yes|number|Max file size for the document selected|
|supportedType|Yes|DocumentTypeString|List of supported documents types to allow selecting|

## Sample

```javascript
import { ImagePickerError, DocumentPickerErrorCodes } from '@seatalk-rn/sdk-widgets'

// TRIGGER TO INITIATE DOCUMENT PICKING SEQUENCE
async onPressDocumentPicker(): Promise < void> {
    try {
        const result = await (await sdkClient).picker.selectDocument(2048, ["PDF"])


if(!result.wasCancelled) {
        // Insert custom logic to use result.documents[0]
    } else {
        HUD.hudShowError('Cancelled')
    }
} catch (error) {
    logger.error(error)
    switch (error.code) {
        case DocumentPickerErrorCodes.SDK_ERROR: {
            HUD.hudShowError(`DocPicker: SDK_ERROR, ${error.message}`)
            break
        }
        case DocumentPickerErrorCodes.MAX_SIZE_EXCEEDED: {
            HUD.hudShowError(`DocPicker: MAX_SIZE_EXCEEDED, ${error.message}`)
            break
        }
        default:
            HUD.hudShowError(`DocPicker: ${error.code}, ${error.message}`)
    }
}
} Copy
```

## Method

```javascript
captureImage(maxFileSizeInKiloBytes: number): Promise<ImagePickerFileResult> Copy
```

## Description

Triggers native Camera UI. Currently supports capturing one image only.

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|maxFileSizeInKiloBytes|Yes|number|Max file size for the image taken|

## Sample

```javascript
import { ImagePickerError, DocumentPickerErrorCodes } from '@seatalk-rn/sdk-widgets'

// TRIGGER TO INITIATE IMAGE CAPTURE SEQUENCE
async onPressImageCapture(): Promise < void> {
    try {
        const result = await (await sdkClient).picker.captureImage(2048)
        if(!result.wasCancelled) {
                if(!result.images[0]) {
                HUD.hudShowError('No image found')
            } else {
                // Insert custom logic to use result.images[0]
            }
        } else {
            HUD.hudShowError('Cancelled')
        }
    } catch (error) {
        logger.error(error)
        switch (error.code) {
            case ImagePickerError.SDK_ERROR: {
                HUD.hudShowError(`ImagePicker: SDK_ERROR, ${error.message}`)
                break
            }
            case ImagePickerError.NO_PERMISSION: {
                HUD.hudShowError(`ImagePicker: NO_PERMISSION, ${error.message}`)
                break
            }
            case ImagePickerError.MAX_FILE_SIZE_EXCEEDED: {
                HUD.hudShowError(`ImagePicker: MAX_FILE_SIZE_EXCEEDED, ${error.message}`)
                break
            }
            default:
                HUD.hudShowError(`ImagePicker: ${error.code}, ${error.message}`)
        }
    }
}
 Copy
```

# class MediaClient

This client manages APIs to access the media system of SeaTalk.

## Method saveImageToPhotosAlbum()

```javascript
saveImageToPhotosAlbum(option: IOption) => Promise<IResolveData | IRejectData> Copy
```

## interface IOption

|Name|Type|Description|Required RN SDK Version|
|---|---|---|---|
|filepath|string|Path of the image, only support local image under current RN App|0.7.0 +|

## Promise

Return different status based on save status

### Resolve: interface IResolveData

|Name|Type|Description|Required RN SDK Version|
|---|---|---|---|
|success|Boolean|Whether or not the save is successful. default will return True|0.7.0 +|

### Reject: interface IRejectData

|Name|Type|Description|Required RN SDK Version|
|---|---|---|---|
|code|Number|1: filepath is illegal or not a locally cached file 2: RN app don't have access to save an image to local album 3. SeaTalk don't have system access to save an image to local album 4. Other errors|0.7.0 +|
|message|String|1: saveImageToPhotosAlbum:fail File path is invalid 2: saveImageToPhotosAlbum:fail No permission for app 3: saveImageToPhotosAlbum:fail No permission for seatalk 4: saveImageToPhotosAlbum:fail Token is invalid 4: saveImageToPhotosAlbum:fail Can not save image to album|0.7.0 +|

## Sample

```javascript
// Here is an example of saving a remote image to album.import { FileInfo } from '@seatalk-rn/sdk-filesystem';
import { client } from '../client';

let url =
    'https://cdn.jsdelivr.net/gh/warpprism/cdn@1.5.0/autopiano/static/images/bg_gz.png';

let fileName = 'bg_gz.png';

let file: FileInfo = {
    type: 'cache',
    path: fileName,
};

// First Step: download image to local filesystem.let code = await client.fileSystem.fileManager.downloadFile(
url,
    file,
    undefined
);

if (code === 200) {
    // Second Step: get full uri of the image.let filePath = await client.fileSystem.fileManager.getFullURI(file);
    // Third Step: save image to photo album by local file path.
    client.media.saveImageToPhotosAlbum({
        filePath,
    })
        .then((res: Record<string, any>) => {
            if (res && res.success) {
                console.log('Save Image To Photo Album Success!');
            }
        })
        .catch((error) => {
            console.log('Code: ', error.code);
            console.log('Reason: ', error.message);
        });
} else {
    console.log('Download Image Failed.');
} Copy
```

Was this document helpful?

No

Yes