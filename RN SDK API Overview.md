# RN SDK API Overview

Before starting to develop React Native apps using the SeaTalk RN SDK, you are encouraged to go through the APIs provided in this document and its siblings. They will help illustrate the capabilities provided by the SDK, as well as how to use them.

A good place to start would the [SDK-Client](/docs/rn-sdk-apis_sdk-client)package, which provides a lot of the basics required to get your app up and running.

# Package Descriptions

This page list all public SDK packages and their responsibility for your reference. For detailed API specs please refer to the corresponding sections.

|Package Name|Latest Release|Description|
|---|---|---|
|@seatalk-rn/sdk-client|0.1.1|Provides the SDKClient class to access the SeaTalk RN SDK APIs. This is a core component for building RN Apps using SeaTalk RN SDK, you are strongly advised to familiarize yourself with it|
|@seatalk-rn/sdk-application|0.1.1|Provides abstraction and an app registry for RN applications|
|@seatalk-rn/sdk-open-platform|0.1.1|Provides API for interaction with the Open Platform system. For example, your app can get authenticated to interact with SeaTalk open platform servers through an auth token from this package.|
|@seatalk-rn/sdk-logger|0.1.1|Logging module. Currently it's console.log only. We will be integrating with the native app's logging and bug reporting utility in the future.|
|@seatalk-rn/sdk-navigator|0.1.1|Provides basic navigating functionality like push and pops. Refer to RNNavigator for details.|
|@seatalk-rn/sdk-components|0.1.1|Provides base classes for some of the commonly used components, e.g. PageComponent, BaseComponent, SafeAreaView, etc.|
|@seatalk-rn/sdk-widgets|0.1.1|Provides SeaTalk style UI widgets that are consistent with the rest of the SeaTalk user experience. e.g. HUD, Alert, SolidButton, BorderButton, etc.|
|@seatalk-rn/sdk-lang|0.1.1|Provides a utility function TXT to enable localisation. If your RN app needs to be localised according to the native app's selected language, can consider using this utility.|
|@seatalk-rn/sdk-config|0.1.1|Exposes the current configuration and environment of the native app, including such information as server environment (live or test), current language code, device identifier, deviceModel etc.|
|@seatalk-rn/sdk-storage|0.1.1|Provides API to access key-value storage from React Native|
|@seatalk-rn/sdk-user|0.1.1|Provides API to navigate to user profile in SeaTalk|
|@seatalk-rn/sdk-share|0.1.1|Provides API to share content to SeaTalk chat as message|
|@seatalk-rn/sdk-scanner|0.1.1|Provides API to open the QR code scanner to scan for the information needed|
|@seatalk-rn/sdk-filesystem|0.1.1|Provides API to access the File System from React Native|
|@seatalk-rn/sdk-location|0.1.1|Provides API to access device location|

Was this document helpful?

No

Yes