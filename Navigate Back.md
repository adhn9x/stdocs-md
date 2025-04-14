# Navigate Back

Close the current page to return to a previous page.

# Support

|App Capability|Android|iOS|PC|
|---|:---:|:---:|:---:|
|Web|✅|✅|❌|

# Parameters

## Input(Object object)

|Name|Type|Required|Default|Description|
|---|---|---|---|---|
|data|string|Yes|""|The data string|
|delta|string|Yes|1|- The number of pages to pop - If delta is larger than the number of items in the current app's page stack, it will exit the current app and return to the last page before the current app.|

## Output

None.

# Example

```javascript
import { navigateBack } from '@seatalk/web-app-sdk';

navigateBack({
  data: 'Data from Web App',
  delta: 2
})
  .then(() => {
    console.log('navigateBack:ok');
  })
  .catch((err) => {
    console.log(err);
  });
 Copy
```

Was this document helpful?

No

Yes