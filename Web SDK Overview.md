# Web SDK Overview

Web SDK provides a package of essential and value-add functions for your web app to deliver a better user experience. Here, you can find the following three sub-sections:

1. **Get Started**: a guide to adding Web SDK into your web app
2. **Functions**: the available web SDK functions your app can tap into
3. **Web SDK Error Code**: the information you need for troubleshooting

# How to Use Web SDK

We suggest you look through the functions provided by SeaTalk Open Platform to understand what capabilities might be needed for your app. Then, to use Web SDK, there are two steps that need to be done: installation of Web SDK and actual usage of functions.

## Install Web SDK npm Package

[@seatalk/web-app-sdk](https://www.npmjs.com/package/@seatalk/web-app-sdk) provides all the functions that your web app needs to interact with SeaTalk. Run the following command to install the Web SDK npm package:

```bash
npm install @seatalk/web-app-sdk Copy
```

## Call Function

You need a bundler such as Webpack or Parcel to import`@seatalk/web-app-sdk`as a module in your web app. Once the module is imported, you can call the functions your web app needs.

For example, the following code snippet shows the how the Toast function is used:

```javascript
import { toast } from '@seatalk/web-app-sdk';

toast({ message: 'hello world' }); Copy
```

Note:

* `@seatalk/web-app-sdk`comes with type definitions (TypeScript).

# List of Web SDK Functions

|Category|Function|Description|Supported on Android?|Supported on iOS?|Supported on PC?|
|---|---|---|---|---|---|
|Event|Emit|Trigger an event|✅|✅|❌|
||Listen|Listen on an event|✅|✅|❌|
|Device|Get System info|Get a user's SeaTalk setting and device settings|✅|✅|✅|
|Media|Show Image|Show image(s) in an image viewer provided by the SeaTalk app|✅|✅|✅|
||Pick Images|Select images|✅|✅|✅|
||Fetch Image|Fetch an image|✅|✅|✅|
|Navigation|Navigate Back|Close the current page to return to a previous page|✅|✅|❌|
|Share|Share App|Share an app page in a chatroom|✅|✅|✅|
|User|Get SSO Token|Get a Single-Sign-On (SSO) token of a user's SeaTalk account|✅|✅|✅|
||Open User Profile|Open a user's profile page or profile card|✅|✅|✅|
|View|Show Loading|Show the loading prompt box|✅|✅|❌|
||Hide Loading|Hide the loading prompt box|✅|✅|❌|
||Toast|Display a toast message to users|✅|✅|✅|
||Show Dialog|Show a dialog to users|✅|✅|✅|

Was this document helpful?

No

Yes