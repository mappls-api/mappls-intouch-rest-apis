
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Trip Closure API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/vandana-gupta8020/Intouch-APIs/tree/main/InTouch%20Fleet%20Management%20APIs).**

## **Introduction**

The `Trip Closure API` is used to manually close a specific trip by providing its unique `tripId`. Once invoked, the trip is marked as closed within the system.

This operation is typically used when a trip has been completed and needs to be formally closed. Upon successful execution, the API returns the complete updated trip object, including status, summary details, and associated metadata.

> **Note:** Ensure the trip exists before attempting closure. Use the [Trips Retrieval API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Trip%20APIs/Trips%20Retrieval%20API.md) to obtain the corresponding tripId.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**
 
## **Input Method** 
- POST

## **Input URL**
> https://intouch.mappls.com/iot/api/v2.0/trips/{tripId}/close


## **Request Parameters**
| **Parameter** | **Type** | **Mandatory** | **Description** | **Example** |
| --- | --- | --- | --- | --- |
| **`tripId`** | string | Yes | This is the ID of the trip that you want to close. | `676cef71f7b03b1054a1cf8a` |
| *`remarks`* | string | No | This field is used to record additional notes or comments while closing the trip. | `trip close` |


## **Response Codes (HTTP Status Codes)**
- `200 OK` – Successful operation.
- `400 Bad Request` – Invalid tripId supplied or incorrect data type.
- `401 Unauthorized` – Missing or invalid authentication token.
- `404 Not Found` – Trip or URL not found.
- `500 Internal Server Error` – Server-side processing error.
    - **Example:**
        ```json
        {
        "error": "invalid hexadecimal representation of an ObjectId: [1363489]"
        }
        ```
> **Note:** Ensure ObjectId (`tripId`) is a valid hexadecimal string.

## **Response Parameters**
- **`data`**: Object containing complete trip information after the trip has been closed.
  - **`tripId`**: Unique identifier of the trip.
  - **`deviceId`**: Unique numeric identifier of the device assigned to the trip.
  - **`deviceName`**: Name of the device associated with the trip.
  - **`destination`**: Object containing details of the trip’s destination location.
    - **`geometry`**: Geographic structure of the destination.
      - **`type`**: Geometry type (e.g., `"Point"`).
      - **`coordinates`**: Array `[longitude, latitude]`.
    - **`radius`**: Geofence radius around the destination in meters.
    - **`plannedTime`**: Scheduled arrival time (Unix timestamp in seconds).
    - **`metadata`**: Object containing additional custom attributes.
      - **`myattribute`**: Example custom key-value pair.
    - **`address`**: Formatted address of the destination.
    - **`time`**: Actual time spent at the destination (if applicable).
    - **`distance`**: Total distance covered to reach the destination (km or meters).
    - **`name`**: Name assigned to the destination.
  - **`geofences`**: Array of objects representing geofence or job locations linked to the trip. Each object contains:
    - **`geometry`**: Geographic structure of the geofence location.
      - **`type`**: Geometry type (e.g., `"Point"`).
      - **`coordinates`**: Array `[longitude, latitude]`.
    - **`radius`**: Geofence radius in meters.
    - **`plannedTime`**: Scheduled arrival time (Unix timestamp in seconds).
    - **`metadata`**: Object containing additional custom attributes.
      - **`myattribute`**: Example custom key-value pair.
    - **`address`**: Formatted address of the geofence.
    - **`time`**: Actual time spent at the geofence (if applicable).
    - **`distance`**: Distance covered to reach this geofence.
    - **`name`**: Name of the geofence location.
    - **`status`**: Current status of the geofence/trip (e.g., active, closed, completed).
    - **`jobId`**: Unique identifier of the job associated with the geofence.
    - **`links`**: Object containing URLs related to the job.
      - **`embedUrl`**: Direct URL to view/embed job details in the system interface.
  - **`status`**: Current status of the trip (e.g., active, closed, completed).
  - **`metadata`**: Object containing additional custom attributes for the trip.
    - **`myattribute`**: Example custom key-value pair.
  - **`closureType`**: Method by which the trip was closed (e.g., manual closure).
  - **`forceClose`**: Boolean indicating whether the trip was forcefully closed.
  - **`name`**: Name assigned to the trip.
  - **`summary`**: Object providing trip summary details.
    - **`plannedStartTime`**: Scheduled trip start time (Unix timestamp).
    - **`plannedEndTime`**: Scheduled trip end time (Unix timestamp).
    - **`plannedDuration`**: Planned trip duration.
    - **`plannedDistance`**: Planned trip distance.
    - **`startedOn`**: Actual trip start time (Unix timestamp).
    - **`endedOn`**: Actual trip end time (Unix timestamp).
    - **`duration`**: Total trip duration.
    - **`distance`**: Total distance covered during the trip.
    - **`delayedBy`**: Delay duration compared to planned schedule.
  - **`start`**: Object containing planned start details.
    - **`plannedTime`**: Scheduled start time of the trip (Unix timestamp).
  - **`links`**: Object containing URLs related to the trip.
    - **`embedUrl`**: Direct URL to view/embed trip details in the system interface.

## **Sample cURL Request**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/v2.0/trips/676cef71f7b03b1054a1cf8a/close?remarks=trip%20close' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly; HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{
    "data": {
        "tripId": "676cef71f7b03b1054a1cf8a",
        "deviceId": 10647019,
        "deviceName": "Vandana-test ",
        "destination": {
            "geometry": {
                "type": "Point",
                "coordinates": [
                    77.234,
                    28.456
                ]
            },
            "radius": 100,
            "plannedTime": 1591891234,
            "metadata": {
                "myattribute": "sample text"
            },
            "address": "unnamed road, asola, new delhi, delhi. pin-110074 (india)",
            "time": 0,
            "distance": 0.0,
            "name": "string"
        },
        "geofences": [
            {
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        77.234,
                        28.456
                    ]
                },
                "radius": 100,
                "plannedTime": 1735192433,
                "metadata": {
                    "myattribute": "sample text"
                },
                "address": "unnamed road, asola, new delhi, delhi. pin-110074 (india)",
                "time": 0,
                "distance": 0.0,
                "name": "string",
                "status": 0,
                "jobId": "676cef71f7b03b1054a1cf8b",
                "links": {
                    "embedUrl": "https://intouch.mappls.com/widget/jobs/#/676cef71f7b03b1054a1cf8b?access_token=11571ee1-7b09-4173-90af-6378e9cd2190"
                }
            }
        ],
        "status": 2,
        "metadata": {
            "myattribute": "sample text"
        },
        "closureType": 1,
        "forceClose": true,
        "name": "Vandana-test",
        "summary": {
            "startedOn": null,
            "duration": null,
            "distance": null,
            "endedOn": 1735195774,
            "delayedBy": null,
            "plannedEndTime": 1591891234,
            "plannedStartTime": 1735192433,
            "plannedDuration": 0,
            "plannedDistance": 0.0
        },
        "start": {
            "plannedTime": 1735192433
        },
        "links": {
            "embedUrl": "https://intouch.mappls.com/widget/trips/#/676cef71f7b03b1054a1cf8a?access_token=11571ee1-7b09-4173-90af-6378e9cd2190"
        }
    }
}
```

<br></br>

For any queries and support, please contact: 

[<img src="https://about.mappls.com/images/mappls-logo.svg" height="40"/> </p>](https://about.mappls.com/api/)
Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)


![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://about.mappls.com/contact/)
Need support? contact us!

<br></br>


<br></br>

[<p align="center"> <img src="https://www.mapmyindia.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mappls-api)[![](https://www.mapmyindia.com/api/img/icons/blog.png)](https://about.mappls.com/blog/)[![](https://www.mapmyindia.com/api/img/icons/gethub.png)](https://github.com/Mappls-api)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia) 



[<p align="center"> <img src="https://www.mapmyindia.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/Mapplsofficial)[![](https://www.mapmyindia.com/june-newsletter/icon2.png)](https://twitter.com/mappls)[![](https://www.mapmyindia.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mappls/)[![](https://www.mapmyindia.com/june-newsletter/icon3.png)](https://www.youtube.com/channel/UCAWvWsh-dZLLeUU7_J9HiOA)




<div align="center">@ Copyright 2026 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

