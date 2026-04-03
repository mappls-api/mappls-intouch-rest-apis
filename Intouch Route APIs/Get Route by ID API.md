
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Get Route by ID API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Get Route by ID` API allows users to retrieve detailed information about a specific route using its unique `routeId`. The API returns complete route configuration including route name, start and end points, intermediate geofence points, total distance, total time, polyline coordinates, and other route attributes.

This API is useful for viewing complete route details after creation or for validating route configuration before updating or deleting it.
> **Note:** Ensure the route already exists. Use the [Routes Retrieval API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Route%20APIs/Routes%20Retrieval%20API.md) to obtain valid routeId values.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method**
- GET

## **Input URL**
> `https://intouch.mappls.com/iot/api/route/{id}`

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
| **HTTP Code** | **Message** | **Description** |
| :--- | :--- | :--- |
| `200` | OK | Route details fetched successfully. |
| `400` | Bad Request | The request is invalid or contains incorrect parameters.|
| `401` | Unauthorized | Invalid or missing access token. |
| `403` | Forbidden | API access not enabled for the provided CI/CS |
| `404` | Not Found | Route not found for the given ID(s) |
| `500` | Internal Server Error | Server-side error |

## **Request Parameters**
| **Parameter** | **Type**| **Required** | **Description** |  
| :--- | :--- | :--- | --- |
| **`id`** | Array[long] | Yes | One or more route IDs for which details need to be fetched. Multiple route IDs can be passed as a comma-separated list. |
| *`accountId`* | long | No | AcAccount ID associated with the user. If provided, the response is filtered for the specified account. |

## **Response Parameters**
- **`id`**(long): Unique identifier of the route.
- **`name`**(string): Name assigned to the route.
- **`startPoint`**(long): Geofence ID representing the starting point of the route.
- **`endPoint`**(long): Geofence ID representing the ending point of the route.
- **`points`**(Object): Collection of route stops or legs indexed in sequence order. Each key (`0`, `1`, `2`, etc.) represents a route stop or leg in sequential order.
    - **`geozoneId`**(long): Unique identifier of the geofence associated with this route point.
    - **`address`**(string): Address of the geofence location corresponding to the route point.
    - **`distance`**(double): Distance from the previous route point to this point (in meters). For the starting point, this is typically `0.0`.
    - **`time`**(long): Estimated travel time from the previous route point (in seconds). For the starting point, this is usually `0`.
    - **`buffer`**(integer): Additional buffer time allocated at this route point (in seconds).
    - **`stayInSide`**(integer): Allowed duration for staying inside the geofence at this route point (in seconds).
    - **`maxSpeed`**(double): Maximum permitted speed while traveling to or near this route point (typically in km/h).
    - **`type`**(integer): Indicates the type of route point (e.g., start point, intermediate stop, or end point).
- **`totalPoints`**(integer): Total number of geofence points included in the route.
- **`totalDistance`**(double): Total calculated distance of the complete route (in meters).
- **`totalTime`**(long): Total estimated travel time for the complete route (in seconds).
- **`createdOn`**(long): Timestamp (epoch format) when the route was created.
- **`updatedOn`**(long): Timestamp (epoch format) when the route was last updated.
- **`polylinePoints`**(Array): List of latitude and longitude coordinates representing the route path on the map.
    - **`lat`**(double): Latitude coordinate of the route path.
    - **`lng`**(double): Longitude coordinate of the route path.
- **`type`**(integer): Internal route classification type.
- **`routeType`**(integer): Defines route behavior. Example: `1` = normal, `2` = optimized.
- **`isFixedPoint`**(boolean): Indicates whether the route has fixed predefined points.
- **`isOptimizedTrip`**(boolean): Indicates whether the route was generated using route optimization logic.
- **`serviceType`**(integer): Identifier representing the service category associated with the route.
- **`country`**(string): Country code where the route is configured (ISO format).

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/route/75074' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{
  "data": {
    "id": 75074,
    "name": "Delhi-Jaipur Route",
    "startPoint": 438123,
    "endPoint": 438126,
    "points": {
      "0": {
        "geozoneId": 438123,
        "address": "Connaught Place, New Delhi",
        "distance": 0.0,
        "time": 0,
        "buffer": 0,
        "stayInSide": 600,
        "maxSpeed": 80.0,
        "type": 1
      },
      "1": {
        "geozoneId": 438124,
        "address": "Manesar, Haryana",
        "distance": 55000.5,
        "time": 3600,
        "buffer": 300,
        "stayInSide": 900,
        "maxSpeed": 90.0,
        "type": 2
      },
      "2": {
        "geozoneId": 438126,
        "address": "MI Road, Jaipur",
        "distance": 116345.2,
        "time": 21147,
        "buffer": 0,
        "stayInSide": 0,
        "maxSpeed": 100.0,
        "type": 3
      }
    },
    "totalPoints": 3,
    "totalDistance": 171345.7,
    "totalTime": 24747,
    "createdOn": 1556004092,
    "updatedOn": 1738236902,
    "polylinePoints": [
      { "lat": 28.6315, "lng": 77.2167 },
      { "lat": 28.3600, "lng": 76.9400 },
      { "lat": 26.9124, "lng": 75.7873 }
    ],
    "type": 2,
    "routeType": 1,
    "isFixedPoint": false,
    "isOptimizedTrip": false,
    "serviceType": 1,
    "country": "ind"
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

