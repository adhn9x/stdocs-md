# Emit

Trigger an event.

# Support

|App Capability|Android|iOS|PC|
|---|---|---|---|
|Web|✅|✅|❌|

# Parameters

## Input(Object object)

|Name|Type|Required|Default|Description|
|---|---|---|---|---|
|event|string|Yes|NA|The event name|
|source|string|Yes|NA|The app ID of the event sender|
|target|string\[\]|Yes|NA|An array of app IDs of the event receivers|
|data|string|Yes|NA|The data to be sent in the event, which is a serialised JSON string|

## Output

None.

# Example

```javascript
import { emit } from '@seatalk/web-app-sdk';

emit({
  event: 'My Event',
  source: 'SOURCE_APPID',
  target: ['TARGET_APPID'],
  data: JSON.stringify({
    id: 1,
    message: 'This is a message from Web App'
  })
})
  .then(() => {
    console.log('emit:ok');
  })
  .catch((err) => {
    console.log(err);
  });
import { emit } from '@seatalk/web-app-sdk';

emit({
  event: 'My Event',
  source: 'SOURCE_APPID',
  target: ['TARGET_APPID'],
  data: JSON.stringify({
    id: 1,
    message: 'This is a message from Web App'
  })
})
  .then(() => {
    console.log('emit:ok');
  })
  .catch((err) => {
    console.log(err);
  });
 Copy
```

Was this document helpful?

No

Yes