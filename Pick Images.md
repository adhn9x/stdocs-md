# Pick Images

Select images.

# Support

|App Capability|Android|iOS|PC|
|---|:---|:---|:---|
|Web|✅|✅|✅|

# Parameters

## Input(Object object)

|Name|Type|Required|Default|Description|
|---|---|---|---|---|
|maxSelect|number|No|NA|The maximum number of images the user is allowed to select|

## Output(Array images)

|Name|Type|Description|
|---|---|---|
|images|object\[\]|An array of selected images|
|∟url|string|The internal image URL|
|∟width|number|The width of the image|
|∟height|number|The height of the image|

# Example

```javascript
import { pickImages } from '@seatalk/web-app-sdk';

pickImages({
  maxSelect: 10
})
  .then((images) => {
    images.forEach((image) => {
      console.log(image);
    });
  })
  .catch((err) => {
    console.log(err);
  });
 Copy
```

Was this document helpful?

No

Yes