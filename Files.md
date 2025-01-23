# Files API Documentation

## Endpoints

### Download File

**GET** `/{site_id}/files/{file_id}`

**Description**
Retrieve a file by its identifier for a specific site.

**Operation ID**: `download_file`

**Parameters**

- `site_id` (path, required): The site identifier.
- `file_id` (path, required): The file identifier.

**Responses**

- **200 OK**
  - **Content Type**: `application/octet-stream`
  - **Schema**: File content.

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **404 Not Found**
  - Description: The specified file could not be found.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Delete File

**DELETE** `/{site_id}/files/{file_id}`

**Description**
Delete a file by its identifier for a specific site.

**Operation ID**: `delete_file`

**Parameters**

- `site_id` (path, required): The site identifier.
- `file_id` (path, required): The file identifier.

**Responses**

- **204 No Content**
  - Description: The file was successfully deleted.

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled.

- **404 Not Found**
  - Description: The specified file could not be found.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### List Files

**GET** `/{site_id}/files`

**Description**
Retrieve a list of files for a specific site.

**Operation ID**: `list_files`

**Parameters**

- `site_id` (path, required): The site identifier.

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [ListFilesResponse](#listfilesresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled.

- **404 Not Found**
  - Description: No files found for the specified site.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Get File Metadata

**GET** `/{site_id}/files/metadata`

**Description**
Retrieve metadata for all files in a specific site.

**Operation ID**: `get_file_metadata`

**Parameters**

- `site_id` (path, required): The site identifier.

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [FileMetadataResponse](#filemetadataresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled.

- **404 Not Found**
  - Description: Metadata could not be retrieved for the specified site.

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

## Components

### Schemas

#### ListFilesResponse
Schema for listing files in a site.
- **files** (array): List of file objects. Each object contains:
  - **file_id** (string): Unique identifier of the file.
  - **name** (string): Name of the file.
  - **size** (integer): Size of the file in bytes.

#### FileMetadataResponse
Schema for metadata of files in a site.
- **metadata** (array): List of metadata objects. Each object contains:
  - **file_id** (string): Unique identifier of the file.
  - **size** (integer): Size of the file in bytes.
  - **created_at** (string): Timestamp when the file was created.

#### FileContent
Schema for file content.
- **content** (binary): Binary content of the file.

