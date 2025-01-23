# Auth API Documentation

## Endpoints

### Login

**POST** `/api/auth/login`

**Description**
Authenticate a user and retrieve an access token.

**Operation ID**: `login`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [LoginCredentials](#logincredentials)

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [LoginResponse](#loginresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **422 Unprocessable Entity**
  - Description: The request body is not correctly formatted.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Register Guardian

**POST** `/api/auth/guardian/register`

**Description**
Register a new guardian instance.

**Operation ID**: `register_guardian`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [GuardianRegistryParams](#guardianregistryparams)

**Responses**

- **202 Accepted**
  - **Content Type**: `text/plain`
  - **Schema**: `string`

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **422 Unprocessable Entity**
  - Description: The request body is not correctly formatted.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Link Guardian

**POST** `/api/auth/guardian/link`

**Description**
Link a user to an existing guardian instance.

**Operation ID**: `link_guardian`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [GuardianLinkForm](#guardianlinkform)

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [GuardianProfileResponse](#guardianprofileresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **422 Unprocessable Entity**
  - Description: The request body is not correctly formatted.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Remove Guardian

**DELETE** `/{site_id}/guardian/remove`

**Description**
Remove an existing guardian from a site.

**Operation ID**: `remove_guardian`

**Parameters**

- `site_id` (path, required): The site identifier. Must be a string.

**Responses**

- **202 Accepted**
  - **Content Type**: `text/plain`
  - **Schema**: `string`

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **404 Not Found**
  - Description: The specified site or guardian was not found.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

## Components

### Schemas

#### LoginCredentials
Schema for user login.
- **username** (string, required): Username of the user.
- **password** (string, required): Password of the user.

#### LoginResponse
Schema for the login response.
- **token** (string): Access token for the user session.

#### GuardianRegistryParams
Schema for guardian registration.
- **operatorId** (string, required): ID of the operator registering the guardian.
- **siteId** (string, required): ID of the site.

#### GuardianLinkForm
Schema for linking a user to a guardian instance.
- **username** (string, required): Username of the user.
- **password** (string, required): Password of the user.

#### GuardianProfileResponse
Schema for guardian profile response.
- **username** (string): Linked user's username.
- **role** (string): Role assigned to the user.
- **did** (string): Decentralized identifier for the user.

