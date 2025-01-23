# Admin API Documentation

## Endpoints

### Create a New Stream

**POST** `/api/admin/new_stream`

**Description**
Create a new data stream for an admin project.

**Operation ID**: `create_new_stream`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [NewStreamRequest](#newstreamrequest)

**Responses**

- **202 Accepted**
  - **Content Type**: `application/json`
  - **Schema**: [NewStreamResponse](#newstreamresponse)

- **400 Bad Request**
  - Description: The request is malformed or contains invalid data.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Create a New Project

**POST** `/api/admin/create_new_project`

**Description**
Create a new project in the admin context.

**Operation ID**: `create_new_project`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [NewProjectRequest](#newprojectrequest)

**Responses**

- **202 Accepted**
  - **Content Type**: `application/json`
  - **Schema**: [NewProjectResponse](#newprojectresponse)

- **400 Bad Request**
  - Description: The request is malformed or contains invalid data.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Generate a New Identity

**GET** `/api/admin/identity/create`

**Description**
Generate a new identity in the admin context.

**Operation ID**: `generate_identity`

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [IdentityResponse](#identityresponse)

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Retrieve Identity

**GET** `/api/admin/identity`

**Description**
Retrieve an existing identity in the admin context.

**Operation ID**: `retrieve_identity`

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [IdentityResponse](#identityresponse)

- **404 Not Found**
  - Description: The requested identity could not be found.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

## Components

### Schemas

#### NewStreamRequest
Schema for creating a new stream.
- **streamName** (string, required): Name of the stream.
- **projectId** (string, required): ID of the associated project.

#### NewStreamResponse
Schema for the response when creating a new stream.
- **streamId** (string): Unique identifier of the created stream.
- **status** (string): Status of the stream creation.

#### NewProjectRequest
Schema for creating a new project.
- **projectName** (string, required): Name of the project.
- **ownerId** (string, required): ID of the project owner.

#### NewProjectResponse
Schema for the response when creating a new project.
- **projectId** (string): Unique identifier of the created project.
- **status** (string): Status of the project creation.

#### IdentityResponse
Schema for generating or retrieving an identity.
- **identityId** (string): Unique identifier of the identity.
- **details** (object): Additional details about the identity.

