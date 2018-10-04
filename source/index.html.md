---
title: Sencrop API
language_tabs:
  - shell: curl
toc_footers: []
includes: []
search: false
highlight_theme: darkula
headingLevel: 2

---

<h1 id="Sencrop-API">Sencrop API v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

API to consume Sencrop data

Base URLs:

* <a href="https://api.sencrop.com/v1">https://api.sencrop.com/v1</a>

# Authentication

- HTTP Authentication, scheme: basic 

<h1 id="Sencrop-API-Default">Default</h1>

## Get a user's hourly data for a given geo location.

<a id="opIdgetUserHourlyData"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/data/hourly?latitude=-90&longitude=-180&beforeDate=2018-10-04T08%3A48%3A46Z&days=1&measures=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/data/hourly`

<h3 id="get-a-user's-hourly-data-for-a-given-geo-location.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|latitude|query|number|true|The latitude of the data|
|longitude|query|number|true|The longitude of the data|
|beforeDate|query|string(date-time)|true|The date before which the data starts being retrieved|
|days|query|number|true|The number of days to retrieve|
|measures|query|array[string]|true|The measures to read|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|days|1|
|days|2|
|days|7|
|days|20|
|days|31|
|measures|RELATIVE_HUMIDITY|
|measures|RELATIVE_HUMIDITY_MIN|
|measures|RELATIVE_HUMIDITY_MAX|
|measures|TEMPERATURE|
|measures|TEMPERATURE_MIN|
|measures|TEMPERATURE_MAX|
|measures|WET_TEMPERATURE|
|measures|WET_TEMPERATURE_MIN|
|measures|WET_TEMPERATURE_MAX|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|LEAF_SENSOR_CONDUCTIVITY_MIN|
|measures|LEAF_SENSOR_CONDUCTIVITY_MAX|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_WETNESS|
|measures|LEAF_WETNESS_MEDIUM|
|measures|LEAF_WETNESS_HIGH|
|measures|RH_AIR_H1|
|measures|RH_AIR_H1_MIN|
|measures|RH_AIR_H1_MAX|
|measures|TEMP_AIR_H1|
|measures|TEMP_AIR_H1_MIN|
|measures|TEMP_AIR_H1_MAX|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "measures": [
    {
      "key": 0,
      "docCount": 0
    }
  ]
}
```

<h3 id="get-a-user's-hourly-data-for-a-given-geo-location.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's statistics|[DeviceStatistics](#schemadevicestatistics)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's preferences.

<a id="opIdgetUserPreferences"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/preferences \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/preferences`

<h3 id="get-a-user's-preferences.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "areasUnit": "HA",
  "locale": "strin",
  "precipitationsUnit": "MM",
  "smallVolumesUnit": "L",
  "speedsUnit": "KPH",
  "temperaturesUnit": "C",
  "volumesUnit": "M3",
  "weightsUnit": "T",
  "optionalMeasures": [
    "WET_TEMPERATURE"
  ]
}
```

<h3 id="get-a-user's-preferences.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user preferences|[UserPreferences](#schemauserpreferences)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a user's preferences.

<a id="opIdputUserPreferences"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId}/preferences \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}/preferences`

> Body parameter

```json
{
  "areasUnit": "HA",
  "locale": "strin",
  "precipitationsUnit": "MM",
  "smallVolumesUnit": "L",
  "speedsUnit": "KPH",
  "temperaturesUnit": "C",
  "volumesUnit": "M3",
  "weightsUnit": "T",
  "optionalMeasures": [
    "WET_TEMPERATURE"
  ]
}
```

<h3 id="update-a-user's-preferences.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[UserPreferences](#schemauserpreferences)|true|The new user preferences|

> Example responses

> 201 Response

```json
{
  "areasUnit": "HA",
  "locale": "strin",
  "precipitationsUnit": "MM",
  "smallVolumesUnit": "L",
  "speedsUnit": "KPH",
  "temperaturesUnit": "C",
  "volumesUnit": "M3",
  "weightsUnit": "T",
  "optionalMeasures": [
    "WET_TEMPERATURE"
  ]
}
```

<h3 id="update-a-user's-preferences.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user preferences were created/updated|[UserPreferences](#schemauserpreferences)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-system">system</h1>

## Checks API's availability.

<a id="opIdgetPing"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/ping \
  -H 'Accept: application/json'

```

`GET /ping`

> Example responses

> 200 Response

```json
{
  "pong": "pong"
}
```

<h3 id="checks-api's-availability.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Pong|Inline|

<h3 id="checks-api's-availability.-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» pong|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|pong|pong|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Sencrop-API-miscellaneous">miscellaneous</h1>

## Get the crops

<a id="opIdgetCrops"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/crops \
  -H 'Accept: application/json'

```

`GET /crops`

> Example responses

> 200 Response

```json
{
  "crops": {},
  "items": [
    0
  ]
}
```

<h3 id="get-the-crops-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of the crops|[CropsItems](#schemacropsitems)|

<aside class="success">
This operation does not require authentication
</aside>

## Hit the server to check the email can be used to signup.

<a id="opIdpostSignupCheck"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/utils/checkSignup \
  -H 'Content-Type: application/json' \
  -H 'Authorization: string'

```

`POST /utils/checkSignup`

> Body parameter

```json
{
  "email": "user@example.com"
}
```

<h3 id="hit-the-server-to-check-the-email-can-be-used-to-signup.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|Authorization|header|string|false|Authorization with Bearer mecanism|
|body|body|object|true|The email to check|
|» email|body|string(email)|true|none|

<h3 id="hit-the-server-to-check-the-email-can-be-used-to-signup.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Email can be used.|None|

<aside class="success">
This operation does not require authentication
</aside>

## Request a password change e-mail.

<a id="opIdpostLostPassword"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/password/lost \
  -H 'Content-Type: application/json'

```

`POST /password/lost`

> Body parameter

```json
{
  "email": "user@example.com",
  "callbackPath": "string"
}
```

<h3 id="request-a-password-change-e-mail.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|The infos to send the mail|
|» email|body|string(email)|true|none|
|» callbackPath|body|string|false|none|

<h3 id="request-a-password-change-e-mail.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Password change email sent|None|

<aside class="success">
This operation does not require authentication
</aside>

## Change a user password

<a id="opIdputPassword"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/password \
  -H 'Content-Type: application/json'

```

`PUT /password`

> Body parameter

```json
{
  "lostToken": "string",
  "newPassword": "string"
}
```

<h3 id="change-a-user-password-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|The infos to change the password|
|» lostToken|body|string|true|none|
|» newPassword|body|string|true|none|

<h3 id="change-a-user-password-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Password changed|None|

<aside class="success">
This operation does not require authentication
</aside>

## Log a user in

<a id="opIdpostLogin"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/sign_in \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

`POST /users/sign_in`

> Body parameter

```json
{
  "email": "string",
  "password": "string"
}
```

<h3 id="log-a-user-in-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|The infos to log in|
|» email|body|string|true|none|
|» password|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "token": "string",
  "expirationDate": "2018-10-04T08:48:46Z",
  "userId": 1,
  "organisationId": 1,
  "organisationsIds": [
    1
  ]
}
```

<h3 id="log-a-user-in-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User logged in|[Session](#schemasession)|

<aside class="success">
This operation does not require authentication
</aside>

## Verify a user

<a id="opIdpostVerify"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/verify \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

`POST /users/verify`

> Body parameter

```json
{
  "email": "string",
  "verify": "string"
}
```

<h3 id="verify-a-user-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|Verify the user|
|» email|body|string|true|none|
|» verify|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "token": "string",
  "expirationDate": "2018-10-04T08:48:46Z",
  "userId": 1,
  "organisationId": 1,
  "organisationsIds": [
    1
  ]
}
```

<h3 id="verify-a-user-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User verified|[Session](#schemasession)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Sencrop-API-modules">modules</h1>

## Get the modules

<a id="opIdgetModules"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/modules \
  -H 'Accept: application/json'

```

`GET /modules`

> Example responses

> 200 Response

```json
{
  "items": [
    1
  ],
  "modules": {}
}
```

<h3 id="get-the-modules-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of the modules|[ModuleItems](#schemamoduleitems)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Sencrop-API-partners">partners</h1>

## Request a user token

<a id="opIdpostPartnerTokenRequest"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/partners/{partnerId}/tokenRequests \
  -H 'Content-Type: application/json' \
  -H 'Authorization: string'

```

`POST /partners/{partnerId}/tokenRequests`

> Body parameter

```json
{
  "email": "user@example.com"
}
```

<h3 id="request-a-user-token-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|partnerId|path|number|true|The partner organisation id|
|Authorization|header|string|true|Authorization with Basic mecanism|
|body|body|object|true|Request a user token|
|» email|body|string(email)|true|none|

<h3 id="request-a-user-token-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User token requested|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth ( Scopes: ROLE_PARTNER )
</aside>

## Create a user token

<a id="opIdpostPartnerToken"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/partners/{partnerId}/tokens \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /partners/{partnerId}/tokens`

> Body parameter

```json
{
  "email": "string",
  "code": "string"
}
```

<h3 id="create-a-user-token-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|partnerId|path|number|true|The partner organisation id|
|Authorization|header|string|true|Authorization with Basic mecanism|
|body|body|object|true|Create a user token|
|» email|body|string|true|none|
|» code|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "token": "string",
  "expirationDate": "2018-10-04T08:48:46Z",
  "userId": 1,
  "organisationId": 1,
  "organisationsIds": [
    1
  ]
}
```

<h3 id="create-a-user-token-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User token created|[Session](#schemasession)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basicAuth ( Scopes: ROLE_PARTNER )
</aside>

## Retrieves the devices a partner has access to.

<a id="opIdgetPartnerDevices"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/partners/{partnerId}/devices?limit=10&start=0 \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /partners/{partnerId}/devices`

<h3 id="retrieves-the-devices-a-partner-has-access-to.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|partnerId|path|number|true|The partner organisation id|
|limit|query|number|true|The number of items to retrieve|
|start|query|number|true|The index in results|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|limit|10|
|limit|50|
|limit|100|

> Example responses

> 200 Response

```json
{
  "items": [
    1
  ],
  "total": 0,
  "models": {},
  "devicesStatuses": {},
  "devices": {},
  "users": {},
  "organisations": {}
}
```

<h3 id="retrieves-the-devices-a-partner-has-access-to.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The devices collection|[PartnerDevicesItems](#schemapartnerdevicesitems)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_PARTNER )
</aside>

## Update an partner module parameters

<a id="opIdputPartnerModuleParameters"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/partners/{partnerId}/users/{partnerUserId}/devices/{deviceId}/modules/{moduleId}/parameters \
  -H 'Content-Type: application/json' \
  -H 'Authorization: string'

```

`PUT /partners/{partnerId}/users/{partnerUserId}/devices/{deviceId}/modules/{moduleId}/parameters`

> Body parameter

```json
{
  "enabled": true
}
```

<h3 id="update-an-partner-module-parameters-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|partnerId|path|number|true|The partner organisation id|
|partnerUserId|path|number|true|The partner user id|
|deviceId|path|number|true|The device id|
|moduleId|path|number|true|The module id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|object|true|The module parameters|
|» enabled|body|boolean|false|none|

<h3 id="update-an-partner-module-parameters-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Module sucessfully updated on the user device|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_PARTNER )
</aside>

<h1 id="Sencrop-API-users">users</h1>

## Create a new user.

<a id="opIdpostUser"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

`POST /users`

> Body parameter

```json
{
  "id": 1,
  "locale": "strin",
  "timeZone": "string",
  "signupType": "form",
  "emailVerified": true,
  "organisationsIds": [
    1
  ],
  "roles": [
    "ROLE_USER"
  ],
  "contents": {
    "email": "user@example.com",
    "phone": "string",
    "firstname": "string",
    "lastname": "string",
    "address": "string",
    "zipcode": "string",
    "city": "string",
    "country": "string",
    "birthDate": "2018-10-04",
    "gender": "string"
  },
  "password": "stringst",
  "callbackPath": "string"
}
```

<h3 id="create-a-new-user.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[NewUser](#schemanewuser)|true|The new user|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "users": {}
}
```

<h3 id="create-a-new-user.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user were successfully created|[UserItem](#schemauseritem)|

<aside class="success">
This operation does not require authentication
</aside>

## Create a new user with simplified information (for meeting/showroom/...), add a demo device and connect it. Need a special code.

<a id="opIdpostUserSimplified"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/simplified \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

`POST /users/simplified`

> Body parameter

```json
{
  "id": 1,
  "locale": "strin",
  "timeZone": "string",
  "password": "stringst",
  "simplifiedCode": "string",
  "callbackPath": "string",
  "contents": {
    "email": "user@example.com",
    "phone": "string"
  }
}
```

<h3 id="create-a-new-user-with-simplified-information-(for-meeting/showroom/...),-add-a-demo-device-and-connect-it.-need-a-special-code.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[NewUserSimplified](#schemanewusersimplified)|true|The new user (simplified) and the special code|

> Example responses

> 200 Response

```json
{
  "item": 1,
  "users": {}
}
```

<h3 id="create-a-new-user-with-simplified-information-(for-meeting/showroom/...),-add-a-demo-device-and-connect-it.-need-a-special-code.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The user were successfully created and a new token.|[UserItem](#schemauseritem)|

<aside class="success">
This operation does not require authentication
</aside>

## Get a user's profile.

<a id="opIdgetUser"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId} \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}`

<h3 id="get-a-user's-profile.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "item": 1,
  "users": {}
}
```

<h3 id="get-a-user's-profile.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user|[UserItem](#schemauseritem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a user's profile.

<a id="opIdputUser"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}`

> Body parameter

```json
{
  "id": 1,
  "locale": "strin",
  "timeZone": "string",
  "signupType": "form",
  "emailVerified": true,
  "organisationsIds": [
    1
  ],
  "roles": [
    "ROLE_USER"
  ],
  "contents": {
    "email": "user@example.com",
    "phone": "string",
    "firstname": "string",
    "lastname": "string",
    "address": "string",
    "zipcode": "string",
    "city": "string",
    "country": "string",
    "birthDate": "2018-10-04",
    "gender": "string"
  }
}
```

<h3 id="update-a-user's-profile.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[User](#schemauser)|true|The new user|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "users": {}
}
```

<h3 id="update-a-user's-profile.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user were created/updated|[UserItem](#schemauseritem)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's guests.

<a id="opIdgetUserGuests"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/guests \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/guests`

<h3 id="get-a-user's-guests.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "users": {},
  "devices": {},
  "guests": {},
  "items": [
    0
  ]
}
```

<h3 id="get-a-user's-guests.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user's guests|[GuestsCollection](#schemaguestscollection)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Create a user's guest.

<a id="opIdpostUserGuest"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/{userId}/guests \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /users/{userId}/guests`

> Body parameter

```json
{
  "id": 0,
  "contents": {
    "guestUserId": 1,
    "sharedDevicesIds": [
      1
    ]
  }
}
```

<h3 id="create-a-user's-guest.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|organisationIdTarget|query|number|false|The organisation id to add the collaborator to|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|any|true|The user's guest|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "contents": {
    "guestUserId": 1,
    "sharedDevicesIds": [
      1
    ]
  }
}
```

<h3 id="create-a-user's-guest.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The created user's guest|[GuestItem](#schemaguestitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a user's guest.

<a id="opIdputUserGuest"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId}/guests/{guestId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}/guests/{guestId}`

> Body parameter

```json
{
  "id": 0,
  "contents": {
    "guestUserId": 1,
    "sharedDevicesIds": [
      1
    ]
  }
}
```

<h3 id="update-a-user's-guest.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|guestId|path|number|true|The guest id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[GuestItem](#schemaguestitem)|true|The user's guest|

> Example responses

> 201 Response

```json
{
  "users": {},
  "devices": {},
  "guests": {},
  "item": 0,
  "entry": 0
}
```

<h3 id="update-a-user's-guest.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user's guest updated|[GuestEntry](#schemaguestentry)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Delete a user's guest.

<a id="opIddeleteUserGuest"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.sencrop.com/v1/users/{userId}/guests/{guestId} \
  -H 'Authorization: string'

```

`DELETE /users/{userId}/guests/{guestId}`

<h3 id="delete-a-user's-guest.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|organisationIdTarget|query|number|false|The organisation id to remove the collaborator to|
|guestId|path|number|true|The guest id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

<h3 id="delete-a-user's-guest.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|The user's guest were successfully deleted.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's collaborators.

<a id="opIdgetUserCollaborators"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/collaborators \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/collaborators`

<h3 id="get-a-user's-collaborators.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "users": {},
  "devices": {},
  "collaborators": {},
  "items": [
    0
  ]
}
```

<h3 id="get-a-user's-collaborators.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user's collaborators|[CollaboratorsCollection](#schemacollaboratorscollection)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Create a user's collaborator.

<a id="opIdpostUserCollaborator"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/{userId}/collaborators \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /users/{userId}/collaborators`

> Body parameter

```json
{
  "id": 0,
  "contents": {
    "collaboratorUserId": 1,
    "sharedDevicesIds": [
      1
    ]
  }
}
```

<h3 id="create-a-user's-collaborator.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|organisationIdTarget|query|number|false|The organisation id to add the collaborator to|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|any|true|The user's collaborator|

> Example responses

> 200 Response

```json
{
  "users": {},
  "devices": {},
  "collaborators": {},
  "item": 0,
  "entry": 0
}
```

<h3 id="create-a-user's-collaborator.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The created user's collaborator|[CollaboratorEntry](#schemacollaboratorentry)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a user's collaborator.

<a id="opIdputUserCollaborator"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId}/collaborators/{collaboratorId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}/collaborators/{collaboratorId}`

> Body parameter

```json
{
  "id": 0,
  "contents": {
    "collaboratorUserId": 1,
    "sharedDevicesIds": [
      1
    ]
  }
}
```

<h3 id="update-a-user's-collaborator.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|collaboratorId|path|string|true|The collaborator id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[CollaboratorItem](#schemacollaboratoritem)|true|The user's collaborator|

> Example responses

> 201 Response

```json
{
  "users": {},
  "devices": {},
  "collaborators": {},
  "item": 0,
  "entry": 0
}
```

<h3 id="update-a-user's-collaborator.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user's collaborator updated|[CollaboratorEntry](#schemacollaboratorentry)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Delete a user's collaborator.

<a id="opIddeleteUserCollaborator"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.sencrop.com/v1/users/{userId}/collaborators/{collaboratorId} \
  -H 'Authorization: string'

```

`DELETE /users/{userId}/collaborators/{collaboratorId}`

<h3 id="delete-a-user's-collaborator.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|organisationIdTarget|query|number|false|The organisation id to remove the collaborator to|
|collaboratorId|path|number|true|The collaborator id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

<h3 id="delete-a-user's-collaborator.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|The user's collaborator were successfully deleted.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-aggregations">aggregations</h1>

## Get a user's aggregations.

<a id="opIdgetUserAggregations"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/aggregations \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/aggregations`

<h3 id="get-a-user's-aggregations.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|compute|query|boolean|false|Wether the aggregations should be computed|
|patched|query|boolean|false|Wether you want to get only original data or eventually patched ones to avoid holes.|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "aggregations": {},
  "aggregationsResults": {},
  "items": [
    1
  ]
}
```

<h3 id="get-a-user's-aggregations.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user's aggregations|[AggregationItems](#schemaaggregationitems)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Create a user's aggregation.

<a id="opIdpostUserAggregation"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/{userId}/aggregations \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /users/{userId}/aggregations`

> Body parameter

```json
{
  "id": 1,
  "contents": {
    "type": "DEGREE_DAY",
    "name": "string",
    "from": "2018-10-04T08:48:46Z",
    "to": "2018-10-04T08:48:46Z",
    "span": 1,
    "base": 0,
    "devicesIds": [
      1
    ]
  }
}
```

<h3 id="create-a-user's-aggregation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Aggregation](#schemaaggregation)|true|The user's aggregation|

> Example responses

> 200 Response

```json
{
  "item": 1,
  "entry": 1,
  "aggregations": {}
}
```

<h3 id="create-a-user's-aggregation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The created user's aggregation|[AggregationItem](#schemaaggregationitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a single user aggregation with statistics for graphs

<a id="opIdgetUserAggregation"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/aggregations/{aggregationId} \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/aggregations/{aggregationId}`

<h3 id="get-a-single-user-aggregation-with-statistics-for-graphs-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|aggregationId|path|number|true|The aggregation id|
|patched|query|boolean|false|Wether you want to get only original data or eventually patched ones to avoid holes.|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "entry": 1,
  "aggregations": {}
}
```

<h3 id="get-a-single-user-aggregation-with-statistics-for-graphs-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user's aggregation updated|[AggregationItem](#schemaaggregationitem)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a user's aggregation.

<a id="opIdputUserAggregation"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId}/aggregations/{aggregationId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}/aggregations/{aggregationId}`

> Body parameter

```json
{
  "id": 1,
  "contents": {
    "type": "DEGREE_DAY",
    "name": "string",
    "from": "2018-10-04T08:48:46Z",
    "to": "2018-10-04T08:48:46Z",
    "span": 1,
    "base": 0,
    "devicesIds": [
      1
    ]
  }
}
```

<h3 id="update-a-user's-aggregation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|aggregationId|path|number|true|The aggregation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Aggregation](#schemaaggregation)|true|The user's aggregation|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "entry": 1,
  "aggregations": {}
}
```

<h3 id="update-a-user's-aggregation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user's aggregation updated|[AggregationItem](#schemaaggregationitem)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Delete a user's aggregation.

<a id="opIddeleteUserAggregation"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.sencrop.com/v1/users/{userId}/aggregations/{aggregationId} \
  -H 'Authorization: string'

```

`DELETE /users/{userId}/aggregations/{aggregationId}`

<h3 id="delete-a-user's-aggregation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|aggregationId|path|number|true|The aggregation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

<h3 id="delete-a-user's-aggregation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|The user's aggregation were successfully deleted.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-devices">devices</h1>

## Get a user's devices.

<a id="opIdgetUserDevices"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices`

<h3 id="get-a-user's-devices.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|date|query|string(date-time)|false|The status date|
|measures|query|array[string]|false|The measures to read|
|patched|query|boolean|false|Wether you want to get only original data or eventually patched ones to avoid holes.|
|limit|query|number|false|The number of items to retrieve|
|start|query|number|false|The index in results|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|measures|RELATIVE_HUMIDITY|
|measures|TEMPERATURE|
|measures|WET_TEMPERATURE|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|RH_AIR_H1|
|measures|TEMP_AIR_H1|
|measures|null|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|
|limit|10|
|limit|50|
|limit|100|

> Example responses

> 200 Response

```json
{
  "items": [
    1
  ],
  "total": 0,
  "models": {},
  "devicesStatuses": {},
  "devicesSummaries": {},
  "devices": {}
}
```

<h3 id="get-a-user's-devices.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user's devices|[DevicesItems](#schemadevicesitems)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Setup a user's device.

<a id="opIdpostUserDevice"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/{userId}/devices \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /users/{userId}/devices`

> Body parameter

```json
{
  "identification": "string",
  "activationCode": "string"
}
```

<h3 id="setup-a-user's-device.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|object|true|The user device activation couple|
|» identification|body|string|false|none|
|» activationCode|body|string|false|none|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "entry": 1,
  "models": {},
  "devicesStatuses": {},
  "devices": {}
}
```

<h3 id="setup-a-user's-device.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user's device created|[DeviceItem](#schemadeviceitem)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device geographic positions historic.

<a id="opIdgetUserDevicePositions"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/positions \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/positions`

<h3 id="get-a-user's-device-geographic-positions-historic.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
[
  {
    "locationDate": "2018-10-04T08:48:46Z",
    "latitude": -90,
    "longitude": -180,
    "altitude": 0
  }
]
```

<h3 id="get-a-user's-device-geographic-positions-historic.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user's device positions history|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<h3 id="get-a-user's-device-geographic-positions-historic.-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» locationDate|string(date-time)|false|none|none|
|» latitude|number|false|none|none|
|» longitude|number|false|none|none|
|» altitude|number|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device.

<a id="opIdgetUserDevice"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId} \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}`

<h3 id="get-a-user's-device.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "item": 1,
  "entry": 1,
  "models": {},
  "devicesStatuses": {},
  "devices": {}
}
```

<h3 id="get-a-user's-device.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user's device|[DeviceItem](#schemadeviceitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a user's device.

<a id="opIdputUserDevice"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId}/devices/{deviceId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}/devices/{deviceId}`

> Body parameter

```json
{
  "id": 0,
  "contents": {
    "name": "string"
  },
  "accessPeriods": [
    {
      "deviceId": 1,
      "userId": 1,
      "moduleId": 1,
      "delegatorId": 1,
      "parameters": {},
      "name": "string",
      "type": "owner",
      "situation": "unknown",
      "startDate": "2018-10-04T08:48:46Z",
      "endDate": "2018-10-04T08:48:46Z",
      "deletionDate": "2018-10-04T08:48:46Z"
    }
  ],
  "identification": "string",
  "serial": "string",
  "modelId": 1,
  "userId": 1,
  "organisationId": 1
}
```

<h3 id="update-a-user's-device.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Device](#schemadevice)|true|The user device|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "entry": 1,
  "models": {},
  "devicesStatuses": {},
  "devices": {}
}
```

<h3 id="update-a-user's-device.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user's device updated|[DeviceItem](#schemadeviceitem)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Delete a user's device access.

<a id="opIddeleteUserDevice"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.sencrop.com/v1/users/{userId}/devices/{deviceId} \
  -H 'Authorization: string'

```

`DELETE /users/{userId}/devices/{deviceId}`

<h3 id="delete-a-user's-device-access.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

<h3 id="delete-a-user's-device-access.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|The user's device access was successfully deleted.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get the modules a user activated on its device

<a id="opIdgetUserDeviceModules"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/modules \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/modules`

<h3 id="get-the-modules-a-user-activated-on-its-device-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "items": [
    1
  ],
  "modules": {}
}
```

<h3 id="get-the-modules-a-user-activated-on-its-device-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of the modules activated on the given user device|[ModuleItems](#schemamoduleitems)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Add a module to a user's device

<a id="opIdputUserDeviceModule"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/modules/{moduleId} \
  -H 'Content-Type: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}/devices/{deviceId}/modules/{moduleId}`

> Body parameter

```json
{
  "code": "mileos",
  "id": 0
}
```

<h3 id="add-a-module-to-a-user's-device-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|moduleId|path|number|true|The module id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|any|true|The module settings|

<h3 id="add-a-module-to-a-user's-device-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Module sucessfully activated on the user device|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Disable a module for a user's device

<a id="opIddeleteUserDeviceModule"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/modules/{moduleId} \
  -H 'Authorization: string'

```

`DELETE /users/{userId}/devices/{deviceId}/modules/{moduleId}`

<h3 id="disable-a-module-for-a-user's-device-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|moduleId|path|number|true|The module id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

<h3 id="disable-a-module-for-a-user's-device-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Module sucessfully disabled for the user device|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a user's device shares.

<a id="opIdputUserDeviceShares"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/shares/{sharesType} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}/devices/{deviceId}/shares/{sharesType}`

> Body parameter

```json
[
  0
]
```

<h3 id="update-a-user's-device-shares.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|sharesType|path|string|true|The shares type|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|array[number]|true|The users concerned by the user's device share|

> Example responses

> 201 Response

```json
[
  0
]
```

<h3 id="update-a-user's-device-shares.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|User's device shares updated|Inline|

<h3 id="update-a-user's-device-shares.-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device's device's statistics.

<a id="opIdgetUserDeviceStatistics"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/statistics?startDate=2018-10-04T08%3A48%3A46Z&endDate=2018-10-04T08%3A48%3A46Z&measures=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/statistics`

<h3 id="get-a-user's-device's-device's-statistics.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|startDate|query|string(date-time)|true|The statistics start date|
|endDate|query|string(date-time)|true|The statistics end date|
|measures|query|array[string]|true|The measures to read|
|patched|query|boolean|false|Wether you want to get only original data or eventually patched ones to avoid holes.|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|measures|RELATIVE_HUMIDITY|
|measures|RELATIVE_HUMIDITY_MIN|
|measures|RELATIVE_HUMIDITY_MAX|
|measures|TEMPERATURE|
|measures|TEMPERATURE_MIN|
|measures|TEMPERATURE_MAX|
|measures|WET_TEMPERATURE|
|measures|WET_TEMPERATURE_MIN|
|measures|WET_TEMPERATURE_MAX|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|LEAF_SENSOR_CONDUCTIVITY_MIN|
|measures|LEAF_SENSOR_CONDUCTIVITY_MAX|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_WETNESS|
|measures|LEAF_WETNESS_MEDIUM|
|measures|LEAF_WETNESS_HIGH|
|measures|RH_AIR_H1|
|measures|RH_AIR_H1_MIN|
|measures|RH_AIR_H1_MAX|
|measures|TEMP_AIR_H1|
|measures|TEMP_AIR_H1_MIN|
|measures|TEMP_AIR_H1_MAX|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "measures": [
    {
      "key": 0,
      "docCount": 0
    }
  ]
}
```

<h3 id="get-a-user's-device's-device's-statistics.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's statistics|[DeviceStatistics](#schemadevicestatistics)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device's raw data.

<a id="opIdgetUserDeviceRawData"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/data/raw?beforeDate=2018-10-04T08%3A48%3A46Z&size=10&measures=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/data/raw`

<h3 id="get-a-user's-device's-raw-data.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|beforeDate|query|string(date-time)|true|The date before which the data starts being retrieved|
|size|query|number|true|The number of measures to retrieve|
|measures|query|array[string]|true|The measures to read|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|size|10|
|size|50|
|size|100|
|size|500|
|size|1000|
|measures|RELATIVE_HUMIDITY|
|measures|TEMPERATURE|
|measures|WET_TEMPERATURE|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|RH_AIR_H1|
|measures|TEMP_AIR_H1|
|measures|null|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|

> Example responses

> 200 Response

```json
[
  {
    "date": "2018-10-04T08:48:46Z",
    "type": "RELATIVE_HUMIDITY",
    "value": 0
  }
]
```

<h3 id="get-a-user's-device's-raw-data.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's data|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<h3 id="get-a-user's-device's-raw-data.-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» date|string(date-time)|false|none|none|
|» type|string|false|none|none|
|» value|number|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|RELATIVE_HUMIDITY|
|type|TEMPERATURE|
|type|WET_TEMPERATURE|
|type|RAIN_FALL|
|type|WIND_SPEED|
|type|WIND_GUST|
|type|WIND_DIRECTION|
|type|MOVE|
|type|LEAF_SENSOR_CONDUCTIVITY|
|type|RH_AIR_H1|
|type|TEMP_AIR_H1|
|type|null|
|type|RAIN_TIC|
|type|WIND_MEAN|
|type|WIND_MAX|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device's hourly data.

<a id="opIdgetUserDeviceHourlyData"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/data/hourly?beforeDate=2018-10-04T08%3A48%3A46Z&days=1&measures=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/data/hourly`

<h3 id="get-a-user's-device's-hourly-data.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|beforeDate|query|string(date-time)|true|The date before which the data starts being retrieved|
|days|query|number|true|The number of days to retrieve|
|measures|query|array[string]|true|The measures to read|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|days|1|
|days|2|
|days|7|
|days|20|
|days|31|
|measures|RELATIVE_HUMIDITY|
|measures|RELATIVE_HUMIDITY_MIN|
|measures|RELATIVE_HUMIDITY_MAX|
|measures|TEMPERATURE|
|measures|TEMPERATURE_MIN|
|measures|TEMPERATURE_MAX|
|measures|WET_TEMPERATURE|
|measures|WET_TEMPERATURE_MIN|
|measures|WET_TEMPERATURE_MAX|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|LEAF_SENSOR_CONDUCTIVITY_MIN|
|measures|LEAF_SENSOR_CONDUCTIVITY_MAX|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_WETNESS|
|measures|LEAF_WETNESS_MEDIUM|
|measures|LEAF_WETNESS_HIGH|
|measures|RH_AIR_H1|
|measures|RH_AIR_H1_MIN|
|measures|RH_AIR_H1_MAX|
|measures|TEMP_AIR_H1|
|measures|TEMP_AIR_H1_MIN|
|measures|TEMP_AIR_H1_MAX|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "measures": [
    {
      "key": 0,
      "docCount": 0
    }
  ]
}
```

<h3 id="get-a-user's-device's-hourly-data.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's statistics|[DeviceStatistics](#schemadevicestatistics)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device's daily data.

<a id="opIdgetUserDeviceDailyData"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/data/daily?beforeDate=2018-10-04T08%3A48%3A46Z&days=7&measures=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/data/daily`

<h3 id="get-a-user's-device's-daily-data.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|beforeDate|query|string(date-time)|true|The date before which the data starts being retrieved|
|days|query|number|true|The number of days to retrieve|
|measures|query|array[string]|true|The measures to read|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|days|7|
|days|30|
|days|60|
|days|90|
|measures|RELATIVE_HUMIDITY|
|measures|RELATIVE_HUMIDITY_MIN|
|measures|RELATIVE_HUMIDITY_MAX|
|measures|TEMPERATURE|
|measures|TEMPERATURE_MIN|
|measures|TEMPERATURE_MAX|
|measures|WET_TEMPERATURE|
|measures|WET_TEMPERATURE_MIN|
|measures|WET_TEMPERATURE_MAX|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|LEAF_SENSOR_CONDUCTIVITY_MIN|
|measures|LEAF_SENSOR_CONDUCTIVITY_MAX|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_WETNESS|
|measures|LEAF_WETNESS_MEDIUM|
|measures|LEAF_WETNESS_HIGH|
|measures|RH_AIR_H1|
|measures|RH_AIR_H1_MIN|
|measures|RH_AIR_H1_MAX|
|measures|TEMP_AIR_H1|
|measures|TEMP_AIR_H1_MIN|
|measures|TEMP_AIR_H1_MAX|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "measures": [
    {
      "key": 0,
      "docCount": 0
    }
  ]
}
```

<h3 id="get-a-user's-device's-daily-data.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's data|[DeviceStatistics](#schemadevicestatistics)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device's continuous device's statistics.

<a id="opIdgetUserDeviceContinuousStatistics"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/countinuousStatistics?startDate=2018-10-04T08%3A48%3A46Z&endDate=2018-10-04T08%3A48%3A46Z&measures=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/countinuousStatistics`

<h3 id="get-a-user's-device's-continuous-device's-statistics.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|startDate|query|string(date-time)|true|The statistics start date|
|endDate|query|string(date-time)|true|The statistics end date|
|measures|query|array[string]|true|The measures to read|
|patched|query|boolean|false|Wether you want to get only original data or eventually patched ones to avoid holes.|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|measures|RELATIVE_HUMIDITY|
|measures|RELATIVE_HUMIDITY_MIN|
|measures|RELATIVE_HUMIDITY_MAX|
|measures|TEMPERATURE|
|measures|TEMPERATURE_MIN|
|measures|TEMPERATURE_MAX|
|measures|WET_TEMPERATURE|
|measures|WET_TEMPERATURE_MIN|
|measures|WET_TEMPERATURE_MAX|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|LEAF_SENSOR_CONDUCTIVITY_MIN|
|measures|LEAF_SENSOR_CONDUCTIVITY_MAX|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_WETNESS|
|measures|LEAF_WETNESS_MEDIUM|
|measures|LEAF_WETNESS_HIGH|
|measures|RH_AIR_H1|
|measures|RH_AIR_H1_MIN|
|measures|RH_AIR_H1_MAX|
|measures|TEMP_AIR_H1|
|measures|TEMP_AIR_H1_MIN|
|measures|TEMP_AIR_H1_MAX|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "measures": [
    {
      "key": 0,
      "docCount": 0
    }
  ]
}
```

<h3 id="get-a-user's-device's-continuous-device's-statistics.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's statistics|[DeviceStatistics](#schemadevicestatistics)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device's summary at a given date.

<a id="opIdgetUserDeviceSummary"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/summaries/{date}?measures=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/summaries/{date}`

<h3 id="get-a-user's-device's-summary-at-a-given-date.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|date|path|string(date-time)|true|The summary date|
|measures|query|array[string]|true|The measures to read|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|measures|RELATIVE_HUMIDITY|
|measures|TEMPERATURE|
|measures|WET_TEMPERATURE|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|RH_AIR_H1|
|measures|TEMP_AIR_H1|
|measures|null|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "devicesSummaries": {},
  "item": "string",
  "entry": "string"
}
```

<h3 id="get-a-user's-device's-summary-at-a-given-date.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's summary|[DeviceSummaryEntry](#schemadevicesummaryentry)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get a user's device's forecasts.

<a id="opIdgetUserDeviceForecasts"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/devices/{deviceId}/forecasts?date=2018-10-04T08%3A48%3A46Z \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/devices/{deviceId}/forecasts`

<h3 id="get-a-user's-device's-forecasts.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|deviceId|path|number|true|The device id|
|date|query|string(date-time)|true|Date of the forecasts|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "forecasts": {}
}
```

<h3 id="get-a-user's-device's-forecasts.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's forecasts|[DeviceForecasts](#schemadeviceforecasts)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-forecasts">forecasts</h1>

## Get a user's forecasts.

<a id="opIdgetUserForecasts"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/forecasts?latitude=-90&longitude=-180 \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/forecasts`

<h3 id="get-a-user's-forecasts.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|latitude|query|number|true|The latitude of the data|
|longitude|query|number|true|The longitude of the data|
|date|query|string(date-time)|false|Date of the forecasts|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "forecasts": {}
}
```

<h3 id="get-a-user's-forecasts.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's forecasts|[DeviceForecasts](#schemadeviceforecasts)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-partnerAccess">partnerAccess</h1>

## Get a user's daily data for a given geo location.

<a id="opIdgetUserDailyData"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/data/daily?latitude=-90&longitude=-180&beforeDate=2018-10-04T08%3A48%3A46Z&days=7&measures=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/data/daily`

<h3 id="get-a-user's-daily-data-for-a-given-geo-location.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|latitude|query|number|true|The latitude of the data|
|longitude|query|number|true|The longitude of the data|
|beforeDate|query|string(date-time)|true|The date before which the data starts being retrieved|
|days|query|number|true|The number of days to retrieve|
|measures|query|array[string]|true|The measures to read|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|days|7|
|days|30|
|days|60|
|days|90|
|measures|RELATIVE_HUMIDITY|
|measures|RELATIVE_HUMIDITY_MIN|
|measures|RELATIVE_HUMIDITY_MAX|
|measures|TEMPERATURE|
|measures|TEMPERATURE_MIN|
|measures|TEMPERATURE_MAX|
|measures|WET_TEMPERATURE|
|measures|WET_TEMPERATURE_MIN|
|measures|WET_TEMPERATURE_MAX|
|measures|LEAF_SENSOR_CONDUCTIVITY|
|measures|LEAF_SENSOR_CONDUCTIVITY_MIN|
|measures|LEAF_SENSOR_CONDUCTIVITY_MAX|
|measures|RAIN_FALL|
|measures|WIND_SPEED|
|measures|WIND_GUST|
|measures|WIND_DIRECTION|
|measures|MOVE|
|measures|LEAF_WETNESS|
|measures|LEAF_WETNESS_MEDIUM|
|measures|LEAF_WETNESS_HIGH|
|measures|RH_AIR_H1|
|measures|RH_AIR_H1_MIN|
|measures|RH_AIR_H1_MAX|
|measures|TEMP_AIR_H1|
|measures|TEMP_AIR_H1_MIN|
|measures|TEMP_AIR_H1_MAX|
|measures|RAIN_TIC|
|measures|WIND_MEAN|
|measures|WIND_MAX|

> Example responses

> 200 Response

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "measures": [
    {
      "key": 0,
      "docCount": 0
    }
  ]
}
```

<h3 id="get-a-user's-daily-data-for-a-given-geo-location.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested device's statistics|[DeviceStatistics](#schemadevicestatistics)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User/device does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-operations">operations</h1>

## Get a organisation's operations.

<a id="opIdgetOrganisationOperations"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/organisations/{organisationId}/operations \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /organisations/{organisationId}/operations`

<h3 id="get-a-organisation's-operations.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "items": [
    1
  ],
  "operations": {}
}
```

<h3 id="get-a-organisation's-operations.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested organisation's operations|[OperationsItems](#schemaoperationsitems)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Organisation does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Create an organisation's operation.

<a id="opIdpostOrganisationOperation"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/organisations/{organisationId}/operations \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /organisations/{organisationId}/operations`

> Body parameter

```json
{
  "id": 0,
  "contents": {
    "name": "string",
    "type": "irrigation",
    "devicesIds": [
      1
    ],
    "startDate": "2018-10-04T08:48:46Z",
    "endDate": "2018-10-04T08:48:46Z",
    "details": {}
  }
}
```

<h3 id="create-an-organisation's-operation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Operation](#schemaoperation)|true|The operation to add|

> Example responses

> 200 Response

```json
{
  "item": 1,
  "entry": 1,
  "operations": {}
}
```

<h3 id="create-an-organisation's-operation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The newly created organisation's operation|[OperationItem](#schemaoperationitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Organisation does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Retrieve an organisation's operation.

<a id="opIdgetOrganisationOperation"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/organisations/{organisationId}/operations/{operationId} \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /organisations/{organisationId}/operations/{operationId}`

<h3 id="retrieve-an-organisation's-operation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|operationId|path|number|true|The operation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{
  "item": 1,
  "entry": 1,
  "operations": {}
}
```

<h3 id="retrieve-an-organisation's-operation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The organisation's operation|[OperationItem](#schemaoperationitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Organisation or operation does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update an organisation's operation.

<a id="opIdputOrganisationOperation"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/organisations/{organisationId}/operations/{operationId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /organisations/{organisationId}/operations/{operationId}`

> Body parameter

```json
{
  "id": 0,
  "contents": {
    "name": "string",
    "type": "irrigation",
    "devicesIds": [
      1
    ],
    "startDate": "2018-10-04T08:48:46Z",
    "endDate": "2018-10-04T08:48:46Z",
    "details": {}
  }
}
```

<h3 id="update-an-organisation's-operation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|operationId|path|number|true|The operation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Operation](#schemaoperation)|true|The operation to update|

> Example responses

> 200 Response

```json
{
  "item": 1,
  "entry": 1,
  "operations": {}
}
```

<h3 id="update-an-organisation's-operation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The modified organisation's operation|[OperationItem](#schemaoperationitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Organisation does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Delete an organisation's operation.

<a id="opIddeleteOrganisationOperation"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.sencrop.com/v1/organisations/{organisationId}/operations/{operationId} \
  -H 'Authorization: string'

```

`DELETE /organisations/{organisationId}/operations/{operationId}`

<h3 id="delete-an-organisation's-operation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|operationId|path|number|true|The operation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

<h3 id="delete-an-organisation's-operation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|The organisation's operation does not exist anymore|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-alerts">alerts</h1>

## Get a user's alerts.

<a id="opIdgetUserAlerts"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/users/{userId}/alerts \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /users/{userId}/alerts`

<h3 id="get-a-user's-alerts.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 200 Response

```json
{}
```

<h3 id="get-a-user's-alerts.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The requested user's alerts|[AlertsItems](#schemaalertsitems)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|User does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Create a user's alert.

<a id="opIdpostUserAlert"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/{userId}/alerts \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /users/{userId}/alerts`

> Body parameter

```json
{
  "id": 1,
  "userId": 1,
  "lastTriggerDate": "2018-10-04T08:48:46Z",
  "activationDate": "2018-10-04T08:48:46Z",
  "contents": {
    "name": "string",
    "active": true,
    "devicesIds": [
      1
    ],
    "notification": 0,
    "notificationList": [
      "email"
    ],
    "alertParameters": [
      {
        "active": true,
        "min": 0,
        "max": 0,
        "span": 0,
        "from": "2018-10-04T08:48:46Z",
        "to": "2018-10-04T08:48:46Z",
        "base": 0,
        "type": "pluviometry",
        "invitedUsersEmails": [
          "string"
        ],
        "clock": {
          "active": true,
          "start": 0,
          "stop": 0
        }
      }
    ]
  }
}
```

<h3 id="create-a-user's-alert.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Alert](#schemaalert)|true|The user's alert|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "entry": 1,
  "alerts": {}
}
```

<h3 id="create-a-user's-alert.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user's alert created|[AlertItem](#schemaalertitem)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a user's alert.

<a id="opIdputUserAlert"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/users/{userId}/alerts/{alertId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /users/{userId}/alerts/{alertId}`

> Body parameter

```json
{
  "id": 1,
  "userId": 1,
  "lastTriggerDate": "2018-10-04T08:48:46Z",
  "activationDate": "2018-10-04T08:48:46Z",
  "contents": {
    "name": "string",
    "active": true,
    "devicesIds": [
      1
    ],
    "notification": 0,
    "notificationList": [
      "email"
    ],
    "alertParameters": [
      {
        "active": true,
        "min": 0,
        "max": 0,
        "span": 0,
        "from": "2018-10-04T08:48:46Z",
        "to": "2018-10-04T08:48:46Z",
        "base": 0,
        "type": "pluviometry",
        "invitedUsersEmails": [
          "string"
        ],
        "clock": {
          "active": true,
          "start": 0,
          "stop": 0
        }
      }
    ]
  }
}
```

<h3 id="update-a-user's-alert.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|alertId|path|number|true|The alert id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Alert](#schemaalert)|true|The user's alert|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "entry": 1,
  "alerts": {}
}
```

<h3 id="update-a-user's-alert.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user's alert updated|[AlertItem](#schemaalertitem)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Delete a user's alert.

<a id="opIddeleteUserAlert"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.sencrop.com/v1/users/{userId}/alerts/{alertId} \
  -H 'Authorization: string'

```

`DELETE /users/{userId}/alerts/{alertId}`

<h3 id="delete-a-user's-alert.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|alertId|path|number|true|The alert id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

<h3 id="delete-a-user's-alert.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|The user's alert were successfully deleted.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-deprecated">deprecated</h1>

## Creates a new organisation. Highly Deprecated, will be moved soon.

<a id="opIdpostOrganisationDeprecated"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/organisations \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

`POST /organisations`

> Body parameter

```json
{
  "firstname": "string",
  "lastname": "string",
  "birthDate": "2018-10-04",
  "password": "string",
  "email": "user@example.com",
  "locale": "strin",
  "timeZone": "string",
  "phone": "string",
  "address": "string",
  "zipcode": "string",
  "city": "string",
  "country": "string",
  "company": {
    "name": "string",
    "area": 0,
    "crops": [
      "string"
    ],
    "irrigation": true
  },
  "callbackPath": "string",
  "verifyToken": "string"
}
```

<h3 id="creates-a-new-organisation.-highly-deprecated,-will-be-moved-soon.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|The necessary contents to create a new organisation|
|» firstname|body|string|true|none|
|» lastname|body|string|true|none|
|» birthDate|body|string(date)|false|none|
|» password|body|string|true|none|
|» email|body|string(email)|true|none|
|» locale|body|string|true|none|
|» timeZone|body|string|false|none|
|» phone|body|string|true|none|
|» address|body|string|true|none|
|» zipcode|body|string|true|none|
|» city|body|string|true|none|
|» country|body|string|true|none|
|» company|body|object|true|none|
|»» name|body|string|false|none|
|»» area|body|number|false|none|
|»» crops|body|[string]|false|none|
|»» irrigation|body|boolean|false|none|
|» callbackPath|body|string|false|none|
|» verifyToken|body|string|false|none|

> Example responses

> 201 Response

```json
{
  "id": 0,
  "type": "farm",
  "ownersIds": [
    1
  ],
  "contents": {
    "name": "string",
    "locale": "strin",
    "timeZone": "string",
    "identification": "string",
    "typeFarm": [
      "agricultural"
    ]
  }
}
```

<h3 id="creates-a-new-organisation.-highly-deprecated,-will-be-moved-soon.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The organisation were created|[Organisation](#schemaorganisation)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Sencrop-API-organisations">organisations</h1>

## Creates a new organisation.

<a id="opIdpostOrganisation"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/users/{userId}/organisations \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /users/{userId}/organisations`

> Body parameter

```json
{
  "id": 0,
  "type": "farm",
  "ownersIds": [
    1
  ],
  "contents": {
    "name": "string",
    "locale": "strin",
    "timeZone": "string",
    "identification": "string",
    "typeFarm": [
      "agricultural"
    ]
  }
}
```

<h3 id="creates-a-new-organisation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|number|true|The user id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Organisation](#schemaorganisation)|true|The necessary contents to create a new organisation|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "organisations": {}
}
```

<h3 id="creates-a-new-organisation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The organisation were created|[OrganisationItem](#schemaorganisationitem)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Get the organisation.

<a id="opIdgetOrganisation"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/organisations/{organisationId} \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /organisations/{organisationId}`

<h3 id="get-the-organisation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "organisations": {}
}
```

<h3 id="get-the-organisation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The organisation|[OrganisationItem](#schemaorganisationitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Organisation does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update an organisation.

<a id="opIdputOrganisation"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/organisations/{organisationId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /organisations/{organisationId}`

> Body parameter

```json
{
  "id": 0,
  "type": "farm",
  "ownersIds": [
    1
  ],
  "contents": {
    "name": "string",
    "locale": "strin",
    "timeZone": "string",
    "identification": "string",
    "typeFarm": [
      "agricultural"
    ]
  }
}
```

<h3 id="update-an-organisation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Organisation](#schemaorganisation)|true|The modified organisation|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "organisations": {}
}
```

<h3 id="update-an-organisation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The organisation were sucessfully updated|[OrganisationItem](#schemaorganisationitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Organisation does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Endpoint for migration. Don't use it or use with caution !

<a id="opIdpostOrganisationMembersMigration"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/organisations/{organisationId}/membersMigration \
  -H 'Content-Type: application/json' \
  -H 'Authorization: string'

```

`POST /organisations/{organisationId}/membersMigration`

> Body parameter

```json
{
  "collaborators": [
    0
  ],
  "guests": [
    0
  ]
}
```

<h3 id="endpoint-for-migration.-don't-use-it-or-use-with-caution-!-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|object|true|The necessary contents to migrate users|
|» collaborators|body|[number]|true|none|
|» guests|body|[number]|true|none|

<h3 id="endpoint-for-migration.-don't-use-it-or-use-with-caution-!-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Members were migrated|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Add an user to an organisation

<a id="opIdpostOrganisationUser"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/organisations/{organisationId}/users/{targetUserId} \
  -H 'Content-Type: application/json' \
  -H 'Authorization: string'

```

`POST /organisations/{organisationId}/users/{targetUserId}`

> Body parameter

```json
{
  "type": "owner"
}
```

<h3 id="add-an-user-to-an-organisation-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|targetUserId|path|number|true|The user id to add|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[postOrganisationUserBody](#schemapostorganisationuserbody)|true|The type of relation|
|» type|body|string|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|owner|
|» type|administrator|
|» type|collaborator|
|» type|guest|

<h3 id="add-an-user-to-an-organisation-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user was successfully added to the organisation|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Edit or add an user to an organisation

<a id="opIdputOrganisationUser"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/organisations/{organisationId}/users/{targetUserId} \
  -H 'Content-Type: application/json' \
  -H 'Authorization: string'

```

`PUT /organisations/{organisationId}/users/{targetUserId}`

> Body parameter

```json
{
  "type": "owner"
}
```

<h3 id="edit-or-add-an-user-to-an-organisation-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|targetUserId|path|number|true|The user id to add|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[postOrganisationUserBody](#schemapostorganisationuserbody)|true|The type of relation|
|» type|body|string|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|owner|
|» type|administrator|
|» type|collaborator|
|» type|guest|

<h3 id="edit-or-add-an-user-to-an-organisation-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The user was successfully added to the organisation|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Delete an user from an organisation

<a id="opIddeleteOrganisationUser"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.sencrop.com/v1/organisations/{organisationId}/users/{targetUserId} \
  -H 'Authorization: string'

```

`DELETE /organisations/{organisationId}/users/{targetUserId}`

<h3 id="delete-an-user-from-an-organisation-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|targetUserId|path|number|true|The user id to remove|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

<h3 id="delete-an-user-from-an-organisation-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|The user was successfully deleted from the organisation.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Create a new place for an organisation.

<a id="opIdpostOrganisationPlace"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://api.sencrop.com/v1/organisations/{organisationId}/places \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`POST /organisations/{organisationId}/places`

> Body parameter

```json
{
  "id": 0,
  "city": "string",
  "country": "string",
  "contents": {
    "googlePlaceId": "string"
  }
}
```

<h3 id="create-a-new-place-for-an-organisation.-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Place](#schemaplace)|true|The necessary contents to create a new place for an organisation|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "places": {}
}
```

<h3 id="create-a-new-place-for-an-organisation.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The place were created|[PlaceItem](#schemaplaceitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Organisation does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

## Update a place for an organisation

<a id="opIdputOrganisationPlace"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.sencrop.com/v1/organisations/{organisationId}/places/{placeId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`PUT /organisations/{organisationId}/places/{placeId}`

> Body parameter

```json
{
  "id": 0,
  "city": "string",
  "country": "string",
  "contents": {
    "googlePlaceId": "string"
  }
}
```

<h3 id="update-a-place-for-an-organisation-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|organisationId|path|number|true|The organisation id|
|placeId|path|number|true|The place id|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|
|body|body|[Place](#schemaplace)|true|The necessary contents to update a place for an organisation|

> Example responses

> 201 Response

```json
{
  "item": 1,
  "places": {}
}
```

<h3 id="update-a-place-for-an-organisation-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The place were updated|[PlaceItem](#schemaplaceitem)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Place or organisation does not exists|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

<h1 id="Sencrop-API-cache">cache</h1>

## Get last measure (for a specific type) from devices in a given area (1 hour for RAIN_FALL).

<a id="opIdgetWeatherLive"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.sencrop.com/v1/weather/live?geohash=string&measureType=RELATIVE_HUMIDITY \
  -H 'Accept: application/json' \
  -H 'Authorization: string'

```

`GET /weather/live`

<h3 id="get-last-measure-(for-a-specific-type)-from-devices-in-a-given-area-(1-hour-for-rain_fall).-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|geohash|query|string|true|The geohash of the data|
|measureType|query|string|true|The measures to read|
|Authorization|header|string|true|Authorization with Bearer mecanism|
|access_token|query|string|false|Access token in the query string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|measureType|RELATIVE_HUMIDITY|
|measureType|TEMPERATURE|
|measureType|WIND_SPEED|
|measureType|WIND_GUST|
|measureType|WIND_DIRECTION|
|measureType|RAIN_FALL|

> Example responses

> 200 Response

```json
{
  "items": [
    {
      "geohash": "string",
      "lastTemperature": 0,
      "lastRelativeHumidity": 0
    }
  ]
}
```

<h3 id="get-last-measure-(for-a-specific-type)-from-devices-in-a-given-area-(1-hour-for-rain_fall).-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of geohashes (small precision) with last measures|Inline|

<h3 id="get-last-measure-(for-a-specific-type)-from-devices-in-a-given-area-(1-hour-for-rain_fall).-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» items|[object]|false|none|none|
|»» geohash|string|false|none|none|
|»» lastTemperature|number|false|none|none|
|»» lastRelativeHumidity|number|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth ( Scopes: ROLE_USER )
</aside>

# Schemas

<h2 id="tocScropsitems">CropsItems</h2>

<a id="schemacropsitems"></a>

```json
{
  "crops": {},
  "items": [
    0
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|crops|[CropHash](#schemacrophash)|true|none|none|
|items|[number]|true|none|none|

<h2 id="tocScropitem">CropItem</h2>

<a id="schemacropitem"></a>

```json
{
  "item": 1,
  "entry": 1,
  "crops": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|
|crops|[CropHash](#schemacrophash)|true|none|none|

<h2 id="tocScrophash">CropHash</h2>

<a id="schemacrophash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[Crop](#schemacrop)|false|none|none|

<h2 id="tocScrop">Crop</h2>

<a id="schemacrop"></a>

```json
{
  "id": 0,
  "hits": 0,
  "contents": {
    "name": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|hits|number|false|none|none|
|contents|[CropContents](#schemacropcontents)|true|none|none|

<h2 id="tocScropcontents">CropContents</h2>

<a id="schemacropcontents"></a>

```json
{
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|

<h2 id="tocSorganisationhash">OrganisationHash</h2>

<a id="schemaorganisationhash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|undefined|[Organisation](#schemaorganisation)|false|none|none|

<h2 id="tocSorganisation">Organisation</h2>

<a id="schemaorganisation"></a>

```json
{
  "id": 0,
  "type": "farm",
  "ownersIds": [
    1
  ],
  "contents": {
    "name": "string",
    "locale": "strin",
    "timeZone": "string",
    "identification": "string",
    "typeFarm": [
      "agricultural"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|type|string|true|none|none|
|ownersIds|[number]|false|none|none|
|contents|[OrganisationContents](#schemaorganisationcontents)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|farm|
|type|cooperative|
|type|interest_group|
|type|chamber_of_agriculture|
|type|company|
|type|personal|
|type|public_agency|

<h2 id="tocSorganisationitem">OrganisationItem</h2>

<a id="schemaorganisationitem"></a>

```json
{
  "item": 1,
  "organisations": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|organisations|[OrganisationHash](#schemaorganisationhash)|true|none|none|

<h2 id="tocSorganisationcontents">OrganisationContents</h2>

<a id="schemaorganisationcontents"></a>

```json
{
  "name": "string",
  "locale": "strin",
  "timeZone": "string",
  "identification": "string",
  "typeFarm": [
    "agricultural"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|locale|string|true|none|none|
|timeZone|string|true|none|none|
|identification|string|false|none|none|
|typeFarm|[string]|false|none|none|

<h2 id="tocSplace">Place</h2>

<a id="schemaplace"></a>

```json
{
  "id": 0,
  "city": "string",
  "country": "string",
  "contents": {
    "googlePlaceId": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|city|string|false|none|none|
|country|string|false|none|none|
|contents|[PlaceContents](#schemaplacecontents)|true|none|none|

<h2 id="tocSplacecontents">PlaceContents</h2>

<a id="schemaplacecontents"></a>

```json
{
  "googlePlaceId": "string"
}

```

### Properties

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» googlePlaceId|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» googlePlaceId|string|true|none|none|
|» address|string|true|none|none|
|» location|object|true|none|none|
|»» lat|number|true|none|none|
|»» lng|number|true|none|none|
|» googleAddressComponents|[object]|true|none|none|
|»» long_name|string|true|none|none|
|»» short_name|string|true|none|none|
|»» types|[string]|true|none|none|

<h2 id="tocSplacehash">PlaceHash</h2>

<a id="schemaplacehash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|undefined|[Place](#schemaplace)|false|none|none|

<h2 id="tocSplaceitem">PlaceItem</h2>

<a id="schemaplaceitem"></a>

```json
{
  "item": 1,
  "places": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|places|[PlaceHash](#schemaplacehash)|true|none|none|

<h2 id="tocSusercontents">UserContents</h2>

<a id="schemausercontents"></a>

```json
{
  "email": "user@example.com",
  "phone": "string",
  "firstname": "string",
  "lastname": "string",
  "address": "string",
  "zipcode": "string",
  "city": "string",
  "country": "string",
  "birthDate": "2018-10-04",
  "gender": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|email|string(email)|true|none|none|
|phone|string|true|none|none|
|firstname|string|true|none|none|
|lastname|string|true|none|none|
|address|string|true|none|none|
|zipcode|string|true|none|none|
|city|string|true|none|none|
|country|string|true|none|none|
|birthDate|string(date)|false|none|none|
|gender|string|false|none|none|

<h2 id="tocSpartialusercontents">PartialUserContents</h2>

<a id="schemapartialusercontents"></a>

```json
{
  "email": "user@example.com",
  "phone": "string",
  "firstname": "string",
  "lastname": "string",
  "address": "string",
  "zipcode": "string",
  "city": "string",
  "country": "string",
  "birthDate": "2018-10-04",
  "gender": "string"
}

```

*A user that may only have an email*

### Properties

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[UserContents](#schemausercontents)|false|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» email|string(email)|true|none|none|
|» phone|string|false|none|none|
|» firstname|string|false|none|none|
|» lastname|string|false|none|none|
|» address|string|false|none|none|
|» zipcode|string|false|none|none|
|» city|string|false|none|none|
|» country|string|false|none|none|
|» birthDate|string(date)|false|none|none|
|» gender|string|false|none|none|

<h2 id="tocSuser">User</h2>

<a id="schemauser"></a>

```json
{
  "id": 1,
  "locale": "strin",
  "timeZone": "string",
  "signupType": "form",
  "emailVerified": true,
  "organisationsIds": [
    1
  ],
  "roles": [
    "ROLE_USER"
  ],
  "contents": {
    "email": "user@example.com",
    "phone": "string",
    "firstname": "string",
    "lastname": "string",
    "address": "string",
    "zipcode": "string",
    "city": "string",
    "country": "string",
    "birthDate": "2018-10-04",
    "gender": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|locale|string|false|none|none|
|timeZone|string|false|none|none|
|signupType|string|false|none|With which signup method the user has been created|
|emailVerified|boolean|false|none|User email got verified with a link|
|organisationsIds|[number]|false|none|none|
|roles|[string]|false|none|none|
|contents|[UserContents](#schemausercontents)|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|signupType|form|
|signupType|simplified|
|signupType|invitation|
|signupType|unknown|

<h2 id="tocSpartialuser">PartialUser</h2>

<a id="schemapartialuser"></a>

```json
{
  "id": 1,
  "locale": "strin",
  "timeZone": "string",
  "contents": {
    "email": "user@example.com",
    "phone": "string",
    "firstname": "string",
    "lastname": "string",
    "address": "string",
    "zipcode": "string",
    "city": "string",
    "country": "string",
    "birthDate": "2018-10-04",
    "gender": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|locale|string|false|none|none|
|timeZone|string|false|none|none|
|contents|[PartialUserContents](#schemapartialusercontents)|true|none|A user that may only have an email|

<h2 id="tocSnewuser">NewUser</h2>

<a id="schemanewuser"></a>

```json
{
  "id": 1,
  "locale": "strin",
  "timeZone": "string",
  "signupType": "form",
  "emailVerified": true,
  "organisationsIds": [
    1
  ],
  "roles": [
    "ROLE_USER"
  ],
  "contents": {
    "email": "user@example.com",
    "phone": "string",
    "firstname": "string",
    "lastname": "string",
    "address": "string",
    "zipcode": "string",
    "city": "string",
    "country": "string",
    "birthDate": "2018-10-04",
    "gender": "string"
  },
  "password": "stringst",
  "callbackPath": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|locale|string|false|none|none|
|timeZone|string|false|none|none|
|signupType|string|false|none|With which signup method the user has been created|
|emailVerified|boolean|false|none|User email got verified with a link|
|organisationsIds|[number]|false|none|none|
|roles|[string]|false|none|none|
|contents|[UserContents](#schemausercontents)|true|none|none|
|password|string|true|none|none|
|callbackPath|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|signupType|form|
|signupType|simplified|
|signupType|invitation|
|signupType|unknown|

<h2 id="tocSnewusersimplified">NewUserSimplified</h2>

<a id="schemanewusersimplified"></a>

```json
{
  "id": 1,
  "locale": "strin",
  "timeZone": "string",
  "password": "stringst",
  "simplifiedCode": "string",
  "callbackPath": "string",
  "contents": {
    "email": "user@example.com",
    "phone": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|locale|string|false|none|none|
|timeZone|string|false|none|none|
|password|string|true|none|none|
|simplifiedCode|string|true|none|none|
|callbackPath|string|false|none|none|
|contents|object|true|none|none|
|» email|string(email)|true|none|none|
|» phone|string|true|none|none|

<h2 id="tocSuserhash">UserHash</h2>

<a id="schemauserhash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[User](#schemauser)|false|none|none|

<h2 id="tocSpartialuserhash">PartialUserHash</h2>

<a id="schemapartialuserhash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[PartialUser](#schemapartialuser)|false|none|none|

<h2 id="tocSuseritem">UserItem</h2>

<a id="schemauseritem"></a>

```json
{
  "item": 1,
  "users": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|users|[PartialUserHash](#schemapartialuserhash)|true|none|none|

<h2 id="tocSuserpreferences">UserPreferences</h2>

<a id="schemauserpreferences"></a>

```json
{
  "areasUnit": "HA",
  "locale": "strin",
  "precipitationsUnit": "MM",
  "smallVolumesUnit": "L",
  "speedsUnit": "KPH",
  "temperaturesUnit": "C",
  "volumesUnit": "M3",
  "weightsUnit": "T",
  "optionalMeasures": [
    "WET_TEMPERATURE"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|areasUnit|string|true|none|none|
|locale|string|true|none|none|
|precipitationsUnit|string|true|none|none|
|smallVolumesUnit|string|true|none|none|
|speedsUnit|string|true|none|none|
|temperaturesUnit|string|true|none|none|
|volumesUnit|string|true|none|none|
|weightsUnit|string|true|none|none|
|optionalMeasures|[string]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|areasUnit|HA|
|areasUnit|A|
|precipitationsUnit|MM|
|precipitationsUnit|INCH|
|smallVolumesUnit|L|
|smallVolumesUnit|GAL_US|
|speedsUnit|KPH|
|speedsUnit|MPH|
|temperaturesUnit|C|
|temperaturesUnit|F|
|volumesUnit|M3|
|volumesUnit|CU_YD|
|weightsUnit|T|
|weightsUnit|SH_TN|

<h2 id="tocSalertsitems">AlertsItems</h2>

<a id="schemaalertsitems"></a>

```json
{}

```

### Properties

*None*

<h2 id="tocSalerthash">AlertHash</h2>

<a id="schemaalerthash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[Alert](#schemaalert)|false|none|none|

<h2 id="tocSalertitem">AlertItem</h2>

<a id="schemaalertitem"></a>

```json
{
  "item": 1,
  "entry": 1,
  "alerts": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|
|alerts|[AlertHash](#schemaalerthash)|true|none|none|

<h2 id="tocSalert">Alert</h2>

<a id="schemaalert"></a>

```json
{
  "id": 1,
  "userId": 1,
  "lastTriggerDate": "2018-10-04T08:48:46Z",
  "activationDate": "2018-10-04T08:48:46Z",
  "contents": {
    "name": "string",
    "active": true,
    "devicesIds": [
      1
    ],
    "notification": 0,
    "notificationList": [
      "email"
    ],
    "alertParameters": [
      {
        "active": true,
        "min": 0,
        "max": 0,
        "span": 0,
        "from": "2018-10-04T08:48:46Z",
        "to": "2018-10-04T08:48:46Z",
        "base": 0,
        "type": "pluviometry",
        "invitedUsersEmails": [
          "string"
        ],
        "clock": {
          "active": true,
          "start": 0,
          "stop": 0
        }
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|userId|number|false|none|none|
|lastTriggerDate|string(date-time)|false|none|none|
|activationDate|string(date-time)|false|none|none|
|contents|[AlertContents](#schemaalertcontents)|true|none|none|

<h2 id="tocSalertcontents">AlertContents</h2>

<a id="schemaalertcontents"></a>

```json
{
  "name": "string",
  "active": true,
  "devicesIds": [
    1
  ],
  "notification": 0,
  "notificationList": [
    "email"
  ],
  "alertParameters": [
    {
      "active": true,
      "min": 0,
      "max": 0,
      "span": 0,
      "from": "2018-10-04T08:48:46Z",
      "to": "2018-10-04T08:48:46Z",
      "base": 0,
      "type": "pluviometry",
      "invitedUsersEmails": [
        "string"
      ],
      "clock": {
        "active": true,
        "start": 0,
        "stop": 0
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|active|boolean|true|none|none|
|devicesIds|[number]|true|none|none|
|notification|number|false|none|none|
|notificationList|[string]|false|none|none|
|alertParameters|[object]|false|none|none|
|» active|boolean|false|none|none|
|» min|number|false|none|none|
|» max|number|false|none|none|
|» span|number|false|none|none|
|» from|string(date-time)|false|none|none|
|» to|string(date-time)|false|none|none|
|» base|number|false|none|none|
|» type|string|false|none|none|
|» invitedUsersEmails|[string]|false|none|none|
|» clock|object|false|none|none|
|»» active|boolean|false|none|none|
|»» start|number|false|none|none|
|»» stop|number|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|pluviometry|
|type|pluviometryAggregate|
|type|hygrometry|
|type|temperature|
|type|temperatureAggregate|
|type|temperatureDegreeDay|
|type|windMeanSpeed|
|type|windGustsSpeed|
|type|wetTemperature|

<h2 id="tocSaggregationitems">AggregationItems</h2>

<a id="schemaaggregationitems"></a>

```json
{
  "aggregations": {},
  "aggregationsResults": {},
  "items": [
    1
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|aggregations|[AggregationHash](#schemaaggregationhash)|true|none|none|
|aggregationsResults|[AggregationsResultsHash](#schemaaggregationsresultshash)|false|none|none|
|items|[number]|true|none|none|

<h2 id="tocSaggregationhash">AggregationHash</h2>

<a id="schemaaggregationhash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[Aggregation](#schemaaggregation)|false|none|none|

<h2 id="tocSaggregationitem">AggregationItem</h2>

<a id="schemaaggregationitem"></a>

```json
{
  "item": 1,
  "entry": 1,
  "aggregations": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|
|aggregations|[AggregationHash](#schemaaggregationhash)|true|none|none|

<h2 id="tocSaggregation">Aggregation</h2>

<a id="schemaaggregation"></a>

```json
{
  "id": 1,
  "contents": {
    "type": "DEGREE_DAY",
    "name": "string",
    "from": "2018-10-04T08:48:46Z",
    "to": "2018-10-04T08:48:46Z",
    "span": 1,
    "base": 0,
    "devicesIds": [
      1
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|contents|[AggregationContents](#schemaaggregationcontents)|true|none|none|

<h2 id="tocSaggregationcontents">AggregationContents</h2>

<a id="schemaaggregationcontents"></a>

```json
{
  "type": "DEGREE_DAY",
  "name": "string",
  "from": "2018-10-04T08:48:46Z",
  "to": "2018-10-04T08:48:46Z",
  "span": 1,
  "base": 0,
  "devicesIds": [
    1
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|string|true|none|none|
|name|string|true|none|none|
|from|string(date-time)|false|none|none|
|to|string(date-time)|false|none|none|
|span|integer|false|none|none|
|base|number|false|none|none|
|devicesIds|[number]|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|DEGREE_DAY|
|type|COLD_HOURS|
|type|RAIN_FALL_SUM|
|type|LEAF_WETNESS|
|type|LEAF_WETNESS_MEDIUM|
|type|LEAF_WETNESS_HIGH|

<h2 id="tocSaggregationresult">AggregationResult</h2>

<a id="schemaaggregationresult"></a>

```json
{
  "type": "DEGREE_DAY"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|string|true|none|none|
|^DEGREE_DAY|COLD_HOURS|RAIN_FALL_SUM|LEAF_WETNESS|LEAF_WETNESS_MEDIUM|LEAF_WETNESS_HIGH$|object|false|none|none|
|» value|number|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|DEGREE_DAY|
|type|COLD_HOURS|
|type|RAIN_FALL_SUM|
|type|LEAF_WETNESS|
|type|LEAF_WETNESS_MEDIUM|
|type|LEAF_WETNESS_HIGH|

<h2 id="tocSaggregationsresultshash">AggregationsResultsHash</h2>

<a id="schemaaggregationsresultshash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[AggregationResult](#schemaaggregationresult)|false|none|none|

<h2 id="tocSdevicesitems">DevicesItems</h2>

<a id="schemadevicesitems"></a>

```json
{
  "items": [
    1
  ],
  "total": 0,
  "models": {},
  "devicesStatuses": {},
  "devicesSummaries": {},
  "devices": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[number]|true|none|none|
|total|number|false|none|none|
|models|[ModelHash](#schemamodelhash)|true|none|none|
|devicesStatuses|[DeviceStatusesItemsHash](#schemadevicestatusesitemshash)|true|none|none|
|devicesSummaries|[SummariesItemsHash](#schemasummariesitemshash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|

<h2 id="tocSdeviceitem">DeviceItem</h2>

<a id="schemadeviceitem"></a>

```json
{
  "item": 1,
  "entry": 1,
  "models": {},
  "devicesStatuses": {},
  "devices": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|
|models|[ModelHash](#schemamodelhash)|true|none|none|
|devicesStatuses|[DeviceStatusesItemsHash](#schemadevicestatusesitemshash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|

<h2 id="tocSpartnerdevicesitems">PartnerDevicesItems</h2>

<a id="schemapartnerdevicesitems"></a>

```json
{
  "items": [
    1
  ],
  "total": 0,
  "models": {},
  "devicesStatuses": {},
  "devices": {},
  "users": {},
  "organisations": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[number]|true|none|none|
|total|number|false|none|none|
|models|[ModelHash](#schemamodelhash)|true|none|none|
|devicesStatuses|[DeviceStatusesItemsHash](#schemadevicestatusesitemshash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|users|[UserHash](#schemauserhash)|true|none|none|
|organisations|[OrganisationHash](#schemaorganisationhash)|true|none|none|

<h2 id="tocSdevicehash">DeviceHash</h2>

<a id="schemadevicehash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|undefined|[Device](#schemadevice)|false|none|none|

<h2 id="tocSdevice">Device</h2>

<a id="schemadevice"></a>

```json
{
  "id": 0,
  "contents": {
    "name": "string"
  },
  "accessPeriods": [
    {
      "deviceId": 1,
      "userId": 1,
      "moduleId": 1,
      "delegatorId": 1,
      "parameters": {},
      "name": "string",
      "type": "owner",
      "situation": "unknown",
      "startDate": "2018-10-04T08:48:46Z",
      "endDate": "2018-10-04T08:48:46Z",
      "deletionDate": "2018-10-04T08:48:46Z"
    }
  ],
  "identification": "string",
  "serial": "string",
  "modelId": 1,
  "userId": 1,
  "organisationId": 1
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|contents|[DeviceContents](#schemadevicecontents)|true|none|none|
|accessPeriods|[object]|false|none|none|
|» deviceId|number|true|none|none|
|» userId|number|true|none|none|
|» moduleId|number|false|none|none|
|» delegatorId|number|false|none|none|
|» parameters|object|false|none|none|
|» name|string|false|none|none|
|» type|string|true|none|none|
|» situation|string|false|none|none|
|» startDate|string(date-time)|true|none|none|
|» endDate|string(date-time)|true|none|none|
|» deletionDate|string(date-time)|false|none|none|
|identification|string|false|none|none|
|serial|string|false|none|none|
|modelId|number|false|none|none|
|userId|number|false|none|none|
|organisationId|number|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|owner|
|type|user|
|type|guest|
|type|collaborator|
|type|partner|
|situation|unknown|
|situation|greenhouse|
|situation|outdoor-covered|
|situation|outdoor-influenced|
|situation|outdoor-isolated|

<h2 id="tocSdevicecontents">DeviceContents</h2>

<a id="schemadevicecontents"></a>

```json
{
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|

<h2 id="tocSmodelhash">ModelHash</h2>

<a id="schemamodelhash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[Model](#schemamodel)|false|none|none|

<h2 id="tocSmodel">Model</h2>

<a id="schemamodel"></a>

```json
{
  "id": 1,
  "contents": {
    "name": "string",
    "externalDiameter": 0,
    "conception": "string",
    "manufacturing": "string",
    "calibration": "string",
    "height": 0,
    "weight": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|contents|[ModelContents](#schemamodelcontents)|true|none|none|

<h2 id="tocSmodelcontents">ModelContents</h2>

<a id="schemamodelcontents"></a>

```json
{
  "name": "string",
  "externalDiameter": 0,
  "conception": "string",
  "manufacturing": "string",
  "calibration": "string",
  "height": 0,
  "weight": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|externalDiameter|number|false|none|none|
|conception|string|true|none|none|
|manufacturing|string|true|none|none|
|calibration|string|true|none|none|
|height|number|false|none|none|
|weight|number|true|none|none|

<h2 id="tocSmoduleitems">ModuleItems</h2>

<a id="schemamoduleitems"></a>

```json
{
  "items": [
    1
  ],
  "modules": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[number]|true|none|none|
|modules|[ModuleHash](#schemamodulehash)|true|none|none|

<h2 id="tocSmoduleitem">ModuleItem</h2>

<a id="schemamoduleitem"></a>

```json
{
  "item": 1,
  "entry": 1,
  "modules": {},
  "organisations": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|
|modules|[ModuleHash](#schemamodulehash)|true|none|none|
|organisations|[OrganisationHash](#schemaorganisationhash)|false|none|none|

<h2 id="tocSmodulehash">ModuleHash</h2>

<a id="schemamodulehash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[Module](#schemamodule)|false|none|none|

<h2 id="tocSmodule">Module</h2>

<a id="schemamodule"></a>

```json
{
  "id": 0,
  "organisationId": 1,
  "contents": {
    "name": "string",
    "code": "string",
    "type": "data"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|organisationId|number|false|none|none|
|contents|[ModuleContents](#schemamodulecontents)|true|none|none|

<h2 id="tocSmodulecontents">ModuleContents</h2>

<a id="schemamodulecontents"></a>

```json
{
  "name": "string",
  "code": "string",
  "type": "data"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|code|string|true|none|none|
|type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|data|
|type|schedule|
|type|ftp|
|type|partner|

<h2 id="tocSapplicationitems">ApplicationItems</h2>

<a id="schemaapplicationitems"></a>

```json
{
  "items": [
    "string"
  ],
  "applications": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[string]|true|none|none|
|applications|[ApplicationHash](#schemaapplicationhash)|true|none|none|

<h2 id="tocSapplicationitem">ApplicationItem</h2>

<a id="schemaapplicationitem"></a>

```json
{
  "item": "string",
  "entry": "string",
  "applications": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|string|true|none|none|
|entry|string|false|none|Deprecated, use the `item` property instead.|
|applications|[ApplicationHash](#schemaapplicationhash)|true|none|none|

<h2 id="tocSapplicationhash">ApplicationHash</h2>

<a id="schemaapplicationhash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}$|[Application](#schemaapplication)|false|none|none|

<h2 id="tocSapplication">Application</h2>

<a id="schemaapplication"></a>

```json
{
  "id": "string",
  "userId": 1,
  "organisationId": 1,
  "truncatedSecret": "string",
  "secret": "string",
  "creationDate": "2018-10-04T08:48:46Z",
  "modificationDate": "2018-10-04T08:48:46Z",
  "contents": {
    "name": "string",
    "description": "string",
    "isActive": true
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|userId|number|false|none|none|
|organisationId|number|false|none|none|
|truncatedSecret|string|false|none|The API secret of the application truncated.|
|secret|string|false|none|The API secret of the application (provided only at its creation).|
|creationDate|string(date-time)|false|none|none|
|modificationDate|string(date-time)|false|none|none|
|contents|[ApplicationContents](#schemaapplicationcontents)|true|none|none|

<h2 id="tocSapplicationcontents">ApplicationContents</h2>

<a id="schemaapplicationcontents"></a>

```json
{
  "name": "string",
  "description": "string",
  "isActive": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|description|string|true|none|none|
|isActive|boolean|true|none|none|

<h2 id="tocSoperationsitems">OperationsItems</h2>

<a id="schemaoperationsitems"></a>

```json
{
  "items": [
    1
  ],
  "operations": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[number]|true|none|none|
|operations|[OperationHash](#schemaoperationhash)|true|none|none|

<h2 id="tocSoperationitem">OperationItem</h2>

<a id="schemaoperationitem"></a>

```json
{
  "item": 1,
  "entry": 1,
  "operations": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|
|operations|[OperationHash](#schemaoperationhash)|true|none|none|

<h2 id="tocSoperationhash">OperationHash</h2>

<a id="schemaoperationhash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[Operation](#schemaoperation)|false|none|none|

<h2 id="tocSoperation">Operation</h2>

<a id="schemaoperation"></a>

```json
{
  "id": 0,
  "contents": {
    "name": "string",
    "type": "irrigation",
    "devicesIds": [
      1
    ],
    "startDate": "2018-10-04T08:48:46Z",
    "endDate": "2018-10-04T08:48:46Z",
    "details": {}
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|contents|[OperationContents](#schemaoperationcontents)|true|none|none|

<h2 id="tocSoperationcontents">OperationContents</h2>

<a id="schemaoperationcontents"></a>

```json
{
  "name": "string",
  "type": "irrigation",
  "devicesIds": [
    1
  ],
  "startDate": "2018-10-04T08:48:46Z",
  "endDate": "2018-10-04T08:48:46Z",
  "details": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|type|string|true|none|none|
|devicesIds|[number]|true|none|none|
|startDate|string(date-time)|true|none|none|
|endDate|string(date-time)|false|none|none|
|details|object|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|irrigation|
|type|spraying|
|type|seeding|

<h2 id="tocSerror">Error</h2>

<a id="schemaerror"></a>

```json
{
  "transactionId": "string",
  "code": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|transactionId|string|false|none|none|
|code|string|false|none|none|

<h2 id="tocSdevicesmoveshash">DevicesMovesHash</h2>

<a id="schemadevicesmoveshash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[DeviceMoves](#schemadevicemoves)|false|none|none|

<h2 id="tocSdevicemoves">DeviceMoves</h2>

<a id="schemadevicemoves"></a>

```json
{
  "count": 0,
  "dates": [
    "2018-10-04T08:48:46Z"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|count|number|true|none|none|
|dates|[string]|true|none|none|

<h2 id="tocSdevicestatistics">DeviceStatistics</h2>

<a id="schemadevicestatistics"></a>

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "measures": [
    {
      "key": 0,
      "docCount": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|models|[ModelHash](#schemamodelhash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|item|string|true|none|Deprecated, use the `item` property instead.|
|entry|string|false|none|Deprecated, use the `item` property instead.|
|measures|[object]|true|none|none|
|» key|number|false|none|none|
|» docCount|number|false|none|none|

<h2 id="tocSdevicedegreedays">DeviceDegreeDays</h2>

<a id="schemadevicedegreedays"></a>

```json
{
  "models": {},
  "devices": {},
  "item": 0,
  "entry": 0,
  "degreeDays": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|models|[ModelHash](#schemamodelhash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|
|degreeDays|[DeviceDegreeDayItemsHash](#schemadevicedegreedayitemshash)|true|none|none|

<h2 id="tocSdevicedegreedayitemshash">DeviceDegreeDayItemsHash</h2>

<a id="schemadevicedegreedayitemshash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[DeviceDegreeDay](#schemadevicedegreeday)|false|none|none|

<h2 id="tocSdevicedegreeday">DeviceDegreeDay</h2>

<a id="schemadevicedegreeday"></a>

```json
[
  {
    "date": "2018-10-04",
    "count": 0,
    "min": 0,
    "max": 0,
    "mean": 0
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|date|string(date)|true|none|none|
|count|number|true|none|none|
|min|number|true|none|none|
|max|number|true|none|none|
|mean|number|true|none|none|

<h2 id="tocSdevicesummaryentry">DeviceSummaryEntry</h2>

<a id="schemadevicesummaryentry"></a>

```json
{
  "models": {},
  "devices": {},
  "devicesSummaries": {},
  "item": "string",
  "entry": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|models|[ModelHash](#schemamodelhash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|devicesSummaries|[SummariesItemsHash](#schemasummariesitemshash)|true|none|none|
|item|string|true|none|none|
|entry|string|false|none|Deprecated, use the `item` property instead.|

<h2 id="tocSsummariesitemshash">SummariesItemsHash</h2>

<a id="schemasummariesitemshash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[DeviceSummaryItem](#schemadevicesummaryitem)|false|none|none|

<h2 id="tocSdevicesummaryitem">DeviceSummaryItem</h2>

<a id="schemadevicesummaryitem"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^(RELATIVE_HUMIDITY|TEMPERATURE|WET_TEMPERATURE|RAIN_FALL|WIND_SPEED|WIND_GUST|WIND_DIRECTION|MOVE|LEAF_SENSOR_CONDUCTIVITY|RH_AIR_H1|TEMP_AIR_H1||RAIN_TIC|WIND_MEAN|WIND_MAX)$|object|false|none|none|
|» date|string(date-time)|false|none|none|
|» lastMeasure|number|true|none|none|
|» lastHour|number|false|none|none|
|» last3Hours|number|false|none|none|
|» lastDay|number|false|none|none|
|» lastWeek|number|false|none|none|

<h2 id="tocSdeviceforecasts">DeviceForecasts</h2>

<a id="schemadeviceforecasts"></a>

```json
{
  "models": {},
  "devices": {},
  "item": "string",
  "entry": "string",
  "forecasts": {}
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|models|[ModelHash](#schemamodelhash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|item|string|true|none|none|
|entry|string|false|none|Deprecated, use the `item` property instead.|
|forecasts|object|true|none|none|

<h2 id="tocSdevicestatusesitemshash">DeviceStatusesItemsHash</h2>

<a id="schemadevicestatusesitemshash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[DeviceStatusItem](#schemadevicestatusitem)|false|none|none|

<h2 id="tocSdevicestatusitem">DeviceStatusItem</h2>

<a id="schemadevicestatusitem"></a>

```json
{
  "id": 0,
  "measuresCount": 0,
  "contents": {
    "firmware": "string",
    "battery": 0,
    "signal": 0,
    "latitude": -90,
    "longitude": -180,
    "altitude": 0,
    "locationSatellites": 0,
    "locationPrecision": 0,
    "lastLocationDate": "2018-10-04T08:48:46Z",
    "lastLocationFailureDate": "2018-10-04T08:48:46Z",
    "lastRebootDate": "2018-10-04T08:48:46Z",
    "lastMoveDate": "2018-10-04T08:48:46Z",
    "lastStatusUpdateDate": "2018-10-04T08:48:46Z",
    "activeDate": "2018-10-04T08:48:46Z",
    "manufacturedDate": "2018-10-04T08:48:46Z"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|measuresCount|number|false|none|none|
|contents|[DeviceStatus](#schemadevicestatus)|true|none|none|

<h2 id="tocSdevicestatus">DeviceStatus</h2>

<a id="schemadevicestatus"></a>

```json
{
  "firmware": "string",
  "battery": 0,
  "signal": 0,
  "latitude": -90,
  "longitude": -180,
  "altitude": 0,
  "locationSatellites": 0,
  "locationPrecision": 0,
  "lastLocationDate": "2018-10-04T08:48:46Z",
  "lastLocationFailureDate": "2018-10-04T08:48:46Z",
  "lastRebootDate": "2018-10-04T08:48:46Z",
  "lastMoveDate": "2018-10-04T08:48:46Z",
  "lastStatusUpdateDate": "2018-10-04T08:48:46Z",
  "activeDate": "2018-10-04T08:48:46Z",
  "manufacturedDate": "2018-10-04T08:48:46Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|firmware|string|true|none|none|
|battery|number|true|none|none|
|signal|number|true|none|none|
|latitude|number|true|none|none|
|longitude|number|true|none|none|
|altitude|number|true|none|none|
|locationSatellites|number|true|none|none|
|locationPrecision|number|true|none|none|
|lastLocationDate|string(date-time)|true|none|none|
|lastLocationFailureDate|string(date-time)|true|none|none|
|lastRebootDate|string(date-time)|true|none|none|
|lastMoveDate|string(date-time)|true|none|none|
|lastStatusUpdateDate|string(date-time)|true|none|none|
|activeDate|string(date-time)|false|none|none|
|manufacturedDate|string(date-time)|false|none|none|

<h2 id="tocScollaboratorscollection">CollaboratorsCollection</h2>

<a id="schemacollaboratorscollection"></a>

```json
{
  "users": {},
  "devices": {},
  "collaborators": {},
  "items": [
    0
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|users|[UserHash](#schemauserhash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|collaborators|[CollaboratorsItemsHash](#schemacollaboratorsitemshash)|true|none|none|
|items|[number]|true|none|none|

<h2 id="tocScollaboratorentry">CollaboratorEntry</h2>

<a id="schemacollaboratorentry"></a>

```json
{
  "users": {},
  "devices": {},
  "collaborators": {},
  "item": 0,
  "entry": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|users|[UserHash](#schemauserhash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|collaborators|[CollaboratorsItemsHash](#schemacollaboratorsitemshash)|true|none|none|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|

<h2 id="tocScollaboratorsitemshash">CollaboratorsItemsHash</h2>

<a id="schemacollaboratorsitemshash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[CollaboratorItem](#schemacollaboratoritem)|false|none|none|

<h2 id="tocScollaboratoritem">CollaboratorItem</h2>

<a id="schemacollaboratoritem"></a>

```json
{
  "id": 0,
  "contents": {
    "collaboratorUserId": 1,
    "sharedDevicesIds": [
      1
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|contents|[Collaborator](#schemacollaborator)|true|none|none|

<h2 id="tocScollaboratorinvite">CollaboratorInvite</h2>

<a id="schemacollaboratorinvite"></a>

```json
{
  "user": {
    "id": 1,
    "locale": "strin",
    "timeZone": "string",
    "contents": {
      "email": "user@example.com",
      "phone": "string",
      "firstname": "string",
      "lastname": "string",
      "address": "string",
      "zipcode": "string",
      "city": "string",
      "country": "string",
      "birthDate": "2018-10-04",
      "gender": "string"
    }
  },
  "sharedDevicesIds": [
    0
  ],
  "callbackPath": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|user|[PartialUser](#schemapartialuser)|true|none|none|
|sharedDevicesIds|[number]|true|none|none|
|callbackPath|string|false|none|none|

<h2 id="tocScollaborator">Collaborator</h2>

<a id="schemacollaborator"></a>

```json
{
  "collaboratorUserId": 1,
  "sharedDevicesIds": [
    1
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|collaboratorUserId|number|true|none|none|
|sharedDevicesIds|[number]|true|none|none|

<h2 id="tocSguestscollection">GuestsCollection</h2>

<a id="schemaguestscollection"></a>

```json
{
  "users": {},
  "devices": {},
  "guests": {},
  "items": [
    0
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|users|[UserHash](#schemauserhash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|guests|[GuestsItemsHash](#schemaguestsitemshash)|true|none|none|
|items|[number]|true|none|none|

<h2 id="tocSguestentry">GuestEntry</h2>

<a id="schemaguestentry"></a>

```json
{
  "users": {},
  "devices": {},
  "guests": {},
  "item": 0,
  "entry": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|users|[UserHash](#schemauserhash)|true|none|none|
|devices|[DeviceHash](#schemadevicehash)|true|none|none|
|guests|[GuestsItemsHash](#schemaguestsitemshash)|true|none|none|
|item|number|true|none|none|
|entry|number|false|none|Deprecated, use the `item` property instead.|

<h2 id="tocSguestsitemshash">GuestsItemsHash</h2>

<a id="schemaguestsitemshash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[GuestItem](#schemaguestitem)|false|none|none|

<h2 id="tocSguestitem">GuestItem</h2>

<a id="schemaguestitem"></a>

```json
{
  "id": 0,
  "contents": {
    "guestUserId": 1,
    "sharedDevicesIds": [
      1
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|contents|[Guest](#schemaguest)|true|none|none|

<h2 id="tocSguestinvite">GuestInvite</h2>

<a id="schemaguestinvite"></a>

```json
{
  "user": {
    "id": 1,
    "locale": "strin",
    "timeZone": "string",
    "contents": {
      "email": "user@example.com",
      "phone": "string",
      "firstname": "string",
      "lastname": "string",
      "address": "string",
      "zipcode": "string",
      "city": "string",
      "country": "string",
      "birthDate": "2018-10-04",
      "gender": "string"
    }
  },
  "sharedDevicesIds": [
    0
  ],
  "callbackPath": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|user|[PartialUser](#schemapartialuser)|true|none|none|
|sharedDevicesIds|[number]|true|none|none|
|callbackPath|string|false|none|none|

<h2 id="tocSguest">Guest</h2>

<a id="schemaguest"></a>

```json
{
  "guestUserId": 1,
  "sharedDevicesIds": [
    1
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|guestUserId|number|true|none|none|
|sharedDevicesIds|[number]|true|none|none|

<h2 id="tocSmeasuresitemshash">MeasuresItemsHash</h2>

<a id="schemameasuresitemshash"></a>

```json
{}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|^[0-9]+$|[MeasureItem](#schemameasureitem)|false|none|none|

<h2 id="tocSmeasureitem">MeasureItem</h2>

<a id="schemameasureitem"></a>

```json
{
  "id": 0,
  "contents": {
    "deviceId": 1,
    "startDate": "2018-10-04T08:48:46Z",
    "endDate": "2018-10-04T08:48:46Z",
    "measures": [
      "RELATIVE_HUMIDITY"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|number|false|none|none|
|contents|[Measure](#schemameasure)|true|none|none|

<h2 id="tocSmeasure">Measure</h2>

<a id="schemameasure"></a>

```json
{
  "deviceId": 1,
  "startDate": "2018-10-04T08:48:46Z",
  "endDate": "2018-10-04T08:48:46Z",
  "measures": [
    "RELATIVE_HUMIDITY"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deviceId|number|true|none|none|
|startDate|string(date-time)|false|none|none|
|endDate|string(date-time)|false|none|none|
|measures|[string]|true|none|none|

<h2 id="tocSemails">Emails</h2>

<a id="schemaemails"></a>

```json
[
  {
    "subject": "string",
    "text": "string",
    "html": "string",
    "from": [
      "string"
    ],
    "to": [
      "string"
    ]
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|subject|string|false|none|none|
|text|string|false|none|none|
|html|string|false|none|none|
|from|[string]|false|none|none|
|to|[string]|false|none|none|

<h2 id="tocSsession">Session</h2>

<a id="schemasession"></a>

```json
{
  "token": "string",
  "expirationDate": "2018-10-04T08:48:46Z",
  "userId": 1,
  "organisationId": 1,
  "organisationsIds": [
    1
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|token|string|true|none|none|
|expirationDate|string(date-time)|true|none|none|
|userId|number|true|none|none|
|organisationId|number|true|none|none|
|organisationsIds|[number]|false|none|none|

