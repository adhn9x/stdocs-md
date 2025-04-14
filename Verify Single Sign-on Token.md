# Verify Single Sign-on Token

# API Description

Single Sign-On (SSO) provides a seamless way for your app to authenticate the identity of an end-user. Using this API, your app can use the temporary Single Sign-On token to request the basic info of a user.

Note:

* This API requires the relevant**Service Scope**.

**Request Method**: `POST`

**End Point**: https://openapi.seatalk.io/sso/v2/verify

# Request Parameter

**Header**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|Authorization|string|Yes|Obtained through the Get App Access Token API|N/A|Bearer c8bda0f77ef940c5bea9f23b2d7fc0d8|
|Content-Type|string|Yes|Request header format|N/A|application/json|

**Body**

|Parameter|Type|Mandatory|Description|Default|Sample|
|---|---|---|---|---|---|
|token|string|Yes|The single sign-on token|N/A|123|

**Request Sample**

```json
{
    "token": "123456789"
} Copy
```

# Response Parameter

**Result Fields**

|Parameters|Type|Description|
|---|---|---|
|code|int|Refer to Error Code for explanations|
|profile|object|The user profile object|
|∟employee\_code|string|employee\_code of the current employee|
|∟name|string|The name of the employee|
|∟email|string|The email of the employee|

**Response Sample**

```json
{
    "code": 0,
    "profile": {
        "employee_code": "123",
        "name": "Peter Wilson",
        "email": "peterwilson@example.email.com"
    }
} Copy
```

Was this document helpful?

No

Yes