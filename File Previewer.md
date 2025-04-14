# File Previewer

## Image Preview API

This API allows you to use standard SeaTalk Image Preview component to view an image from your RN App

## Method previewImages

```javascript
previewImages(images: FileInfo[], selectedIndex: number, previewConfig: PreviewConfig): Promise<void> Copy
```

# Description

Used to call up the image preview component in RN app

|SDK Version Requirement|Supporting Promise|
|---|---|
|0.2.0|Yes|

# Request Parameters

|Name|Required|Type|Description|SDK Version Requirement|
|---|---|---|---|---|
|images|Yes|FileInfo\[\]|A list of Images to be displayed. Images must follow FileInfo format|0.2.0|
|selectedIndex|Yes|Number|The index of the image being displayed|0.2.0|
|previewConfig|Yes|PreviewConfig|Preview setting|0.2.0|

# PreviewConfig

|Name|Required|Type|Description|SDK Version Requirement|
|---|---|---|---|---|
|showMenu|Yes|Boolean|Whether or not allow user to call up image action menu. default is true|0.2.0|
|enableQR|Yes|Boolean|Whether or not allow user to scan QR code in the message. default is false|0.8.0|

# Response

**res: Promise<void>**

# Example

```javascript
const images = [
    { type: 'cache', path: 'https: //a.com/1.jpg' },
    { type: 'cache', path: 'https: //a.com/2.jpg' },
    { type: 'cache', path: 'https: //a.com/3.jpg' },
];  
    
const FilePreviewer = await sdkClient.then(
    (client) => client.filePreview.filePreviewer
);
    
await FilePreviewer.previewImages(images,0,{
    showMenu: true,
}); Copy
```

Was this document helpful?

No

Yes