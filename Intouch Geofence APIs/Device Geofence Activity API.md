
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Device Geofence Activity API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Device Geofence Activity API` retrieves geofence activity records for devices, including entry time, exit time, and total stay duration within a specified time range.

The API also supports filtering based on minimum stay duration, allowing short or accidental geofence visits to be excluded from the response.
- **Geofence Prerequisite:** Ensure the required geofences are already created. Use the [Geofence Creation API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Geofence%20APIs/Geofence%20Creation%20API.md) to create geofences and the [Fetch All Configured Geofences API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Geofence%20APIs/Fetch%20All%20Configured%20Geofences%20API.md) to obtain the corresponding geofenceId.

### **Device Identification Requirements**
- Certain APIs require a deviceId to be passed as part of the path parameters or query parameters.
- If the deviceId is not already available, developers can retrieve a list of registered devices by invoking the [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md).
- The device details obtained from the Retrieve Basic Information of Device API can then be used to make subsequent API calls that depend on device-specific identifiers.


## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method**
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/geofences/activities

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
- `200 (OK)`: The request was successfully processed, and the operation was successful.
- `400 (Bad Request)`: Invalid ID supplied or invalid data type.
- `401 (Unauthorized Request)`: Access to API is forbidden.
- `404 (Not Found)`: No device found with the provided ID.

## **Request Parameters**
| **Parameter** | **Type** | **Required** | **Description** | **Example** |
| :--- | :--- | :--- | :--- | :--- |
| **`deviceId`** | Array[long] | Yes | ID(s) of the device(s) for which geofence activities are to be fetched. Multiple IDs can be passed as comma-separated values. | `14414276` |
| **`startTime`**  | long | Yes | Unix timestamp (in seconds) indicating the start time for fetching geofence activities. | `1771234317` |
| **`endTime`**  | long | Yes | Unix timestamp (in seconds) indicating the end time for fetching geofence activities. | `1771245387` |
| *`geofenceId`* | Array[long] | No | Id of the geofence(s) for which you want to fetch device geofence activities. For multiple geofences, you can pass comma separated geofence ids as well in the query string. | `1489132`, `1487695`, `1224324` |
| *`stayDuration`* | number | No | Minimum duration (in seconds) the device must stay inside the geofence to be included in the response. | `120` |


## **Response Parameters**

| **Field** | **Type** | **Description** |
| :--- | :--- | :--- |
|`entryLongitude` | number | Longitude at which the device entered the geofence. |
|`entryLatitude` | number | Latitude at which the device entered the geofence. |
|`exitLongitude` | number | Longitude at which the device exited the geofence. |
|`exitLatitude` | number | Latitude at which the device exited the geofence.  |
|`entryTimestamp` | number | Time at which the device entered the geofence. |
|`exitTimestamp` | number | Time at which the device exited the geofence. |
|`geofenceName` | string | Name of the geofence. |
|`geofenceId` | number | the id of the geofence where the activity took place. |
|`deviceId` | number | ID of the device associated with the geofence activity. |

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/geofences/activities?startTime=1771234317&endTime=1771245387&geofenceId=1489132%2C%201487695%2C%201224324&deviceId=14414276&stayDuration=120' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```
## **Sample Output Response**
```json
{
    "data": [
        {
            "entryLongitude": 76.890883,
            "entryTimestamp": 1771235807,
            "geofenceName": "Route Point 8 2905092",
            "entryLatitude": 28.369138,
            "geofenceId": 1224324,
            "exitLatitude": 28.36918,
            "exitLongitude": 76.88934,
            "deviceId": 14414276,
            "exitTimestamp": 1771236037
        },
        {
            "entryLongitude": 76.890883,
            "entryTimestamp": 1771235807,
            "geofenceName": "MSIL MPT GATE",
            "entryLatitude": 28.369138,
            "geofenceId": 1487695,
            "exitLatitude": 28.369175,
            "exitLongitude": 76.888736,
            "deviceId": 14414276,
            "exitTimestamp": 1771236047
        },
        {
            "entryLongitude": 76.891148,
            "entryTimestamp": 1771235797,
            "geofenceName": "MSIL - M",
            "entryLatitude": 28.369131,
            "geofenceId": 1489132,
            "exitLatitude": 28.369175,
            "exitLongitude": 76.888736,
            "deviceId": 14414276,
            "exitTimestamp": 1771236047
        }
    ]
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

