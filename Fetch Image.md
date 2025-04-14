# Fetch Image

Fetch an image.

# Support

|App Capability|Android|iOS|PC|
|---|---|---|---|
|Web|✅|✅|✅|

# Parameters

## Input(Object object)

|Name|Type|Required|Default|Description|
|---|---|---|---|---|
|url|string|Yes|NA|The internal image URL acquired by pickImages|

## Output(Blob blob)

|Name|Type|Description|
|---|---|---|
|blob|Blob|The image content in Blob format|

# Example

```javascript
import { fetchImage } from '@seatalk/web-app-sdk';

fetchImage({
  url: 'INTERNAL_IMAGE_URL'
})
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
 Copy
```

Was this document helpful?

No

Yes