# Context API Documentation

## Endpoints

### Retrieve Data

**POST** `/api/context/data/retrieve`

**Description**
Retrieve data from the context API.

**Operation ID**: `data_retrieve`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [DataRetrieveRequest](#dataretrieverequest)

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [DataRetrieveResponse](#dataretrieveresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Send Data

**POST** `/api/context/data/send`

**Description**
Send data to the context API.

**Operation ID**: `data_send`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [DataSendRequest](#datasendrequest)

**Responses**

- **202 Accepted**
  - **Content Type**: `application/json`
  - **Schema**: [DataSendResponse](#datasendresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Guardian Report

**POST** `/api/context/guardian/report`

**Description**
Submit a report to the guardian API.

**Operation ID**: `guardian_report`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [GuardianReportRequest](#guardianreportrequest)

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [GuardianReportResponse](#guardianreportresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled. [Learn more](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)

- **500 Internal Server Error**
  - Description: Something went wrong on the server.

---

### Sensors List

**GET** `/{site_id}/sensors`

**Description**
Retrieve a list of sensors for a given site.

**Operation ID**: `sensors_list`

**Parameters**

- `site_id` (path, required): The site identifier.

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [SensorsListResponse](#sensorslistresponse)

- **404 Not Found**
  - Description: No sensors found for the given site.

---

### Sensor Details

**GET** `/{site_id}/sensors/{sensor_id}`

**Description**
Retrieve details of a specific sensor.

**Operation ID**: `sensor_details`

**Parameters**

- `site_id` (path, required): The site identifier.
- `sensor_id` (path, required): The sensor identifier.

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [SensorDetailsResponse](#sensordetailsresponse)

- **404 Not Found**
  - Description: No sensor found for the given sensor ID.

---

### Project Loading Status

**GET** `/{site_id}/loading`

**Description**
Retrieve the loading status of a project.

**Operation ID**: `project_loading_status`

**Parameters**

- `site_id` (path, required): The site identifier.

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [ProjectLoadingResponse](#projectloadingresponse)

- **404 Not Found**
  - Description: The loading status could not be retrieved.

---

### Delete Project

**DELETE** `/{site_id}`

**Description**
Delete a project associated with a specific site.

**Operation ID**: `delete_project`

**Parameters**

- `site_id` (path, required): The site identifier.

**Responses**

- **202 Accepted**
  - **Content Type**: `application/json`
  - **Schema**: [DeleteProjectResponse](#deleteprojectresponse)

- **404 Not Found**
  - Description: The specified project could not be found.

---

### Retrieve Project Assets

**GET** `/{site_id}/assets`

**Description**
Retrieve assets associated with a specific project.

**Operation ID**: `retrieve_project_assets`

**Parameters**

- `site_id` (path, required): The site identifier.

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [ProjectAssetsResponse](#projectassetsresponse)

- **404 Not Found**
  - Description: The assets could not be found for the given site.

---

### Analytics Submission

**POST** `/{site_id}/analytics`

**Description**
Submit analytics data for a project.

**Operation ID**: `submit_analytics`

**Request Body**
- **Content Type**: `application/json`
- **Schema**: [SubmitAnalyticsRequest](#submitanalyticsrequest)

**Responses**

- **202 Accepted**
  - **Content Type**: `application/json`
  - **Schema**: [SubmitAnalyticsResponse](#submitanalyticsresponse)

- **400 Bad Request**
  - Description: The request given is wrongly formatted or data asked could not be fulfilled.

---

### Analytics Retrieval

**GET** `/{site_id}/analytics/{analytics_id}`

**Description**
Retrieve analytics data for a specific project.

**Operation ID**: `retrieve_analytics`

**Parameters**

- `site_id` (path, required): The site identifier.
- `analytics_id` (path, required): The analytics identifier.

**Responses**

- **200 OK**
  - **Content Type**: `application/json`
  - **Schema**: [RetrieveAnalyticsResponse](#retrieveanalyticsresponse)

- **404 Not Found**
  - Description: The analytics data could not be retrieved.

## Components

### Schemas

#### DataRetrieveRequest
Schema for the data retrieve request.
- **filter** (object, optional): Criteria for filtering data retrieval.

#### DataRetrieveResponse
Schema for the response to a data retrieval request.
- **data** (array): List of retrieved data items.

#### DataSendRequest
Schema for the data send request.
- **payload** (object, required): Data payload to send.

#### DataSendResponse
Schema for the response to a data send request.
- **status** (string): Status of the operation.

#### GuardianReportRequest
Schema for submitting a guardian report.
- **message** (string, required): Report details.

#### GuardianReportResponse
Schema for the response to a guardian report submission.
- **reportId** (string): Unique identifier of the report.

#### SensorsListResponse
Schema for the response when retrieving a list of sensors.
- **sensors** (array): List of sensor objects.

#### SensorDetailsResponse
Schema for the response when retrieving sensor details.
- **sensorId** (string): Unique identifier of the sensor.
- **metadata** (object): Metadata about the sensor.

#### ProjectLoadingResponse
Schema for the response when retrieving project loading status.
- **loadingStatus** (string): The status of the loading process.

#### DeleteProjectResponse
Schema for the response when deleting a project.
- **status** (string): Status of the deletion.

#### ProjectAssetsResponse
Schema for the response when retrieving project assets.
- **assets** (array): List of asset objects. Each object contains:
  - **assetId** (string): Unique identifier of the asset.
  - **name** (string): Name of the asset.
  - **type** (string): Type of the asset.

#### SubmitAnalyticsRequest
Schema for submitting analytics data.
- **analyticsData** (object, required): Data for analytics submission.

#### SubmitAnalyticsResponse
Schema for the response to analytics submission.
- **status** (string): Status of the analytics submission.

#### RetrieveAnalyticsResponse
Schema for the response when retrieving analytics data.
- **analytics** (object): The retrieved analytics data.

