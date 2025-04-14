# Location

## Location

This package provides APIs to access the user's last known location while requesting the proper permissions.

function getLastKnownLocation

```javascript
getLastKnownLocation(): Promise<Location> Copy
```

#### Description

The function that allows developer to get the last known/most current**precise**location of the user. It handles permission requests automatically.

The returned`Promise`will be rejected with`LocationError`when the last known location was failed to get.

interface Location

```javascript
interface Location {
    latitude: number;
    longitude: number;
} Copy
```

#### Properties

|Name|Required|Type|Description|
|---|---|---|---|
|latitude|Yes|number|The latitude of the location|
|longitude|Yes|number|The longitude of the location|

interface LocationError

```javascript
interface ShareAppLinkError {
    code: string;
    message?: string | null;
} Copy
```

#### Properties

|Name|Required|Type|Description|
|---|---|---|---|
|code|Yes|string|Error code. Should be one of LocationErrorCodes.SDK\_ERROR , LocationErrorCodes.NO\_PERMISSION or LocationErrorCodes.GET\_LOCATION\_TIMEOUT|
|message|No|string \| null \| undefined|Message describing this error|

object LocationErrorCodes

```javascript
const LocationErrorCodes = {
    SDK_ERROR: '1',
    NO_PERMISSION: '2',
    GET_LOCATION_TIMEOUT: '3',
}; Copy
```

#### Properties

|Name|Value|Description|
|---|---|---|
|SDK\_ERROR|1|Error code meaning there is something wrong with the SDK or the native side.|
|NO\_PERMISSION|2|Error code meaning that the user has denied the location permission request. If the user has disabled location request from the system settings ("Always deny"/"Don't ask again"), this error code will still be returned and native side will prompt the user to change that setting.|
|GET\_LOCATION\_TIMEOUT|3|Error code meaning it took too long to get the location. Current timeout threshold is 2 seconds|

Samples

#### GetLaskKnownLocation

```javascript
import { getLastKnownLocation, LocationErrorCodes} from '@seatalk-rn/sdk-location'


async onPressGetLastKnownLocationTest() {
    try {
        const location = await getLastKnownLocation()
        // use `location.latitude` and `location.longitude`
    } catch (error) {
        switch (error.code) {
            case LocationErrorCodes.SDK_ERROR:
                HUD.hudShowError(`GetLastKnownLocation: SDK_ERROR, ${error.message}`)
                break
            case LocationErrorCodes.NO_PERMISSION:
                HUD.hudShowError(`GetLastKnownLocation: NO_PERMISSION, ${error.message}`)
                break
            case LocationErrorCodes.GET_LOCATION_TIMEOUT:
                HUD.hudShowError(`GetLastKnownLocation: GET_LOCATION_TIMEOUT, ${error.message}`)
                break
            default:
                HUD.hudShowError(`GetLastKnownLocation: ${error.code}, ${error.message}`)
        }
    }
} Copy
```

Was this document helpful?

No

Yes