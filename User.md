# User API Documentation

## Endpoints

### Retrieve User Profile

**GET** `/api/user/profile`

**Description**
Retrieve profile information about your active user instance.

**Operation ID**: `profile`

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [UserProfile](#userprofile)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **404 Not Found**
  - Description: The requested profile could not be found.

- **422 Unprocessable Entity**
  - Description: The request body is not correctly formatted.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### List Subscriptions

**GET** `/api/user/subscriptions`

**Description**
Retrieve a list of active subscriptions for the user.

**Operation ID**: `subscriptions`

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [SubscriptionResponse](#subscriptionresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled.

- **404 Not Found**
  - Description: No subscriptions found for the user.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Retrieve Identity Document

**POST** `/api/user/identity/document`

**Description**
Retrieve an identity document for the user.

**Operation ID**: `identity_document`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [DIDData](#diddata)

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [IdentityDocumentResponse](#identitydocumentresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled.

- **404 Not Found**
  - Description: The requested document could not be found.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Guardian Identity

**POST** `/api/user/guardian/identity`

**Description**
Retrieve or manage a guardian identity for the user.

**Operation ID**: `guardian_identity`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [GuardianIdentityParams](#guardianidentityparams)

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [GuardianIdentityResponse](#guardianidentityresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled.

- **404 Not Found**
  - Description: The requested identity could not be found.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Retrieve Guardian Profile

**GET** `/api/user/guardian/profile`

**Description**
Retrieve the guardian profile associated with the user.

**Operation ID**: `retrieve_guardian_profile`

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [GuardianProfileResponse](#guardianprofileresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled.

- **404 Not Found**
  - Description: The guardian profile could not be found.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.


## Components

### Schemas

#### UserProfile
Schema for user profile information.
- **username** (string): Username of the user.
- **userId** (string): Unique identifier of the user.
- **email** (string): Email address of the user.

#### SubscriptionResponse
Schema for subscription response.
- **subscriptions** (array): List of subscription objects.
  - **id** (string): Unique identifier of the subscription.
  - **status** (string): Current status of the subscription.
  - **expiration** (string): Expiration date of the subscription.

#### DIDData
Schema for retrieving identity data.
- **docId** (string, required): Document ID for the identity.
- **methods** (array, required): Array of methods for retrieving the document.

#### IdentityDocumentResponse
Schema for the response when retrieving an identity document.
- **document** (object): Retrieved identity document.

#### GuardianIdentityParams
Schema for guardian identity parameters.
- **message** (string, required): Message associated with the identity.
- **userId** (string, required): User identifier.

#### GuardianIdentityResponse
Schema for the response when retrieving or managing a guardian identity.
- **id** (string): Unique identifier of the guardian identity.
- **message** (string): Associated message.
- **status** (string): Current status of the identity.

#### GuardianProfileResponse
Schema for the guardian profile response.
- **username** (string): Username linked to the guardian profile.
- **role** (string): Role of the user in the guardian system.
- **did** (string): Decentralized identifier.

