# Show Images

Show image(s) in an image viewer provided by the SeaTalk app.

# Support

|App Capability|Android|iOS|PC|
|---|---|---|---|
|Web|✅|✅|✅|

# Parameters

## Input(Object object)

|Name|Type|Required|Default|Description|
|---|---|---|---|---|
|urls|string\[\]|Yes|NA|An array of image URLs|
|selectedIndex|number|No|NA|The index of the element in the urls string array that refers to the image checked by the user|

## Output

None.

# Example

```javascript
import { showImages } from '@seatalk/web-app-sdk';

showImages({
    urls: [
        'https://picsum.photos/600?id=0',
        'https://picsum.photos/600?id=1',
        'https://picsum.photos/600?id=2',
    ],
    selectedIndex: 2,
})
    .then(() => {
        console.log('showImages:ok');
    })
    .catch((err) => {
        console.log(err);
    }); Copy
```

Was this document helpful?

No

Yes