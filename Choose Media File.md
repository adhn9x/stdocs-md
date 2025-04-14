# Choose Media File

# chooseMedia

Take or select pictures or videos from your phone album.

## Support

|Application|Android|iOS|PC|SDK Version|
|---|---|---|---|---|
|RN|3.22.0|3.22.0|❌|0.15.0|

## Parameters

# **Input(Object object)**

|Name|Type|Default|Required|Description|Minimum SDK Version|
|---|---|---|---|---|---|
|source|string\[\]|\["album", "camera"\]|no|Source of pictures and videos selected||
|albumMediaType|string\[\]|\["image", "video"\]|no|File type selected from album. Only in source for "album"||
|maxMediaNumber|number|1|no|Maximum number of medias to select from an album||
|cameraMediaType|string\[\]|\["image", "video"\]|no|File type selected from camera. Only in source for "camera"||
|cameraDevice|string|'back'|no|Use the default camera to shoot with the camera. Only in source for "camera"||
|saveToAlbum|boolean|true|no|Whether to save the picture to the album after shooting with the camera. Only in source for "album"||
|maxMediaDuration|number|60|no|Maximum shooting time per second. The time frame is 3 seconds to 60 seconds Between. Only in source for "camera"||

# Output(Object object)

### success return parameters

|Name|Type|Description|Minimum version|
|---|---|---|---|
|errCode|number|Error code||
|errMsg|string|Error Message||
|mediaFiles|object|Local temporary file list||

**mediaFiles**

|Name|Type|Description|Minimum version|
|---|---|---|---|
|filePath|string|File address||
|fileType|string|File type||
|duration|number|Video duration. Only in mediaType for "video"||
|width|number|File width||
|height|number|File height||

# Example

```javascript
import {
	sdkClient
} from 'client'

const option = {
	source: ['camera'],
	albumMediaType: ['video'],
	maxMediaNumber: 3, // 1~9
	cameraMediaType: ['image'],
	cameraDevice: 'front',
	saveToAlbum: false,
	maxVideoDuration: 50
}

// default option
option = {
	source: ['album', 'camera'],
	albumMediaType: ['image', 'video'],
	maxMediaNum: 1,
	cameraMediaType: ['image', 'video'],
	cameraDevice: 'back',
	saveToAlbum: true,
	maxVideoDuration: 60
}

// if you want to use default option
// you can use like this
const result = (await sdkClient).media.chooseMedia();
console.log(result)


// if you want to use custom option
// you can use like this
const result = (await sdkClient).media.chooseMedia(option);
console.log(result) Copy
```

Was this document helpful?

No

Yes