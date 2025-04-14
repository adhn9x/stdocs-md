# Share App

Share an app page in a chatroom.

# Support

|App Capability|Android|iOS|PC|
|---|---|---|---|
|Web|✅|✅|✅|

# Parameters

## Input(Object object)

|Name|Type|Required|Default|Description|
|---|---|---|---|---|
|title|string|No|The title of the webpage ( document.title )|- The title shown in the shared app page message - M aximum length limit is 60|
|subtitle|string|No|The description of the webpage ( <meta name="description" /> )|- The subtitle shown in the shared app page message - M aximum length limit is 200|
|imageUri|string|No|The favicon of the webpage ( <link rel="icon"> )|- The remote URL of the image preview shown in the shared app page message - M aximum length limit is 500|
|mobileLink|object|No|NA|The destination when the shared app page message is clicked on the mobile client|
|∟ type|string|Yes|NA|- The app type of the link - Must be rn or web|
|∟ path|string|Yes|NA|The absolute URL of the link|
|∟ params|object|Yes|NA|The parameters of the link|
|desktopLink|object|No|NA|The destination when the shared app page message is clicked on the desktop client|
|∟ type|string|Yes|NA|- The app type of the link - Must be web|
|∟ path|string|Yes|NA|The absolute URL of the link|
|∟ params|object|Yes|NA|The parameters of the link|

Note:At least one of the mobileLink or desktopLink should be filled in.

## Output(Object object)

|Name|Type|Description|
|---|---|---|
|confirm|boolean|Whether the confirmation button is clicked|
|cancel|boolean|Whether the cancellation button is clicked|

# Example

```javascript
import { shareApp } from '@seatalk/web-app-sdk';


shareApp({
    title: 'Web App',
    subtitle: 'This is a shared message from Web App',
    imageUri: 'https://seatalk.io/img/seatalk-web-logo.png',
    mobileLink: {
        type: 'web',
        path: encodeURI('https://seatalk.io/'),
        params: {
            name: encodeURI('Share'),
        },
    },
})
    .then((res) => {
        if (res.confirm) {
            console.log('shareApp:confirm');
        } else {
            console.log('shareApp:cancel');
        };
    })
    .catch((err) => {
        console.log(err);
    }); Copy
```

# Note

1. The shared content must come from the current app and the web page needs to be working in order to be opened properly
2. In the shared link, if there is any special character (see the doc [here](https://zhuanlan.zhihu.com/p/37060051)for examples) please use 'encodeURI' to code. Otherwise, an error will occur
3. The latest version of this function was supported from SeaTalk 3.11.0 onwards, while the old Share function is still supported

Was this document helpful?

No

Yes