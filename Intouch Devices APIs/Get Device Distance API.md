
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Get Device Distance API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Get Device Distance API` retrieves the total distance traveled by a specific device within a defined time range. It calculates key travel metrics such as total distance, drive distance, movement duration, idle time, and GPS availability using telematics data collected from connected devices, vehicles, or mobile applications.

This API is commonly used in fleet management and asset tracking systems to monitor device activity, analyze travel performance, and generate distance-based operational reports.

### **Device Identification Requirements**
- Certain InTouch APIs require a valid `entityId` to retrieve device-specific data.
- If the `entityId` is not available, it can be obtained using the [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/InTouch%20Fleet%20Management%20APIs/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md).
- The `entityId` returned by that API can then be used to make subsequent API calls that require device-specific identifiers.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/device​/{entityId}​/distance

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**

- `200(OK)`: The operation was successful, and the requested information is returned.
- `204(No content found)`: The request was successful, but no data was found for the given parameters.
- `400(Bad Request)`: Request - Invalid device ID supplied or an incorrect data type was passed (e.g., string instead of integer).
  - Example:
    ```json
    {
      "error": "futuredateselected"
    }
    ```
- `401(Unauthorized)`: The request is forbidden due to missing or invalid authentication credentials.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**
Parameters marked in **`bold`** are mandatory, and those in *`italics`* are optional:
- **`entityId`**(integer): The unique ID of the device for which the travel distance is to be retrieved. The API returns the distance data for the specified entity ID. `Example: 14414276`
- **`startTime`**(integer): The epoch timestamp representing the start of the time range for which the distance is to be calculated. `Example: 1771871400`
- **`endTime`**(integer): The epoch timestamp representing the end of the time range for which the distance is to be calculated. `Example: 1771917157`
- *`driveDistance`*(integer): Specifies the minimum drive distance (in kilometers/meters) to filter results. `Example: 75`
- *`eventsOnly`*(integer): A query parameter that, when provided, returns distance and duration metrics calculated only from recorded device events within the specified time range. `Example: 300`


## **Response Parameters**
- **`driveDistance`**(number): Distance traveled based on drive-specific metrics. `Example: 125.96546504414431`
- **`distance`** (number): Total distance traveled during the specified period. `Example: 125.96546504414431`
- **`totalEvents`** (integer): The total number of events recorded during the period. `Example: 1387`
- **`movementTime`**(integer): The total duration (in seconds) of device movement. `Example: 9942`
- **`nogps`** (integer): Number of instances where no GPS signal was available. `Example: 10`
- **`type`** (integer): The type of device for which data is returned. `Example: 0`
- **`idleTime`** (integer): Total idle time (in seconds) during the period. `Example: 35609`
- **`duration`** (integer): Total duration (in seconds) of the time period. `Example: 45561`
- **`obdConnection`** (integer/null): Represents the state of OBD (On-Board Diagnostics) connection. `Example: null`
- **`idealEvents`**(integer): The number of ideal (expected) events recorded. `Example: 2745`
- **`startTime`**(integer): The epoch timestamp representing the start of the period. `Example: 1771871590`
- **`endTime`** (integer): The epoch timestamp representing the end of the period. `Example: 1771917151`
- **`nogpsDistance`**(number): Distance traveled when GPS signal was unavailable. `Example: 0.18475012641701224`

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/device/14414276/distance?startTime=1771871400&endTime=1771917157&driveDistance=75&eventsOnly=300' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response**
```json
{
    "driveDistance": 125.96546504414431,
    "distance": 125.96546504414431,
    "totalEvents": 1387,
    "movementTime": 9942,
    "nogps": 10,
    "type": 0,
    "idleTime": 35609,
    "duration": 45561,
    "obdConnection": null,
    "idealEvents": 2745,
    "startTime": 1771871590,
    "endTime": 1771917151,
    "nogpsDistance": 0.18475012641701224
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

