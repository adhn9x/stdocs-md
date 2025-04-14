# Open User Profile

Open a user's profile page or profile card.Different clients behave differently for this API:

* On mobile: Jump directly to the user's profile page, which is standalone.
* On desktop: Open the UserProfileCard at a specific location inside the WebApp.

# Support

|App Capability|Android|iOS|PC|
|---|---|---|---|
|Web|✅|✅|✅|

# Parameters

## Input(Object object)

|Name|Type|Required|Default|Description|
|---|---|---|---|---|
|id|string|Yes|NA|The user ID|
|idType|string|Yes|NA|- The type of user ID - Must be "employee\_code"|
|targetRect|DOMRect|No|NA|The coordinates, width, and height information of the target DOM element, which is supported on desktop|

## Output

None.

# Example

```javascript
import { openUserProfile } from '@seatalk/web-app-sdk';

const btn = document.querySelector('#open-user-profile-btn');
const btnRect = btn.getBoundingClientRect();

openUserProfile({
  id: 12345,
  idType: 'employee_code',
  targetRect: btnRect
})
  .then(() => {
    console.log('openUserProfile:ok');
  })
  .catch((err) => {
    console.log(err);
  });
 Copy
```

Was this document helpful?

No

Yes