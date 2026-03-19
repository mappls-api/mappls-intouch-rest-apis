
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Update Geofence API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
This API allows developers to `update the details of an existing geofence` in the system. Using the unique Geofence ID, you can modify attributes such as the geofence name, latitude, longitude, and radius based on the type of geofence (point, circle, or polygon).
1. *`Point Geofence:`* Update geofence name and precise latitude/longitude coordinates.
2. *`Circle Geofence:`* Update geofence name, latitude, longitude, and radius to define circular boundaries.
3. *`Polygon Geofence:`* Update geofence name and the set of latitude/longitude coordinates forming the polygon boundary.
> **Note:** Ensure the geofence exists before attempting an update. Use the [Fetch All Configured Geofences API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Geofence%20APIs/Fetch%20All%20Configured%20Geofences%20API.md) to obtain the corresponding geofence ID.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method:**
- POST

## **Input URL**
`https://intouch.mappls.com/iot/api/geofences/{id}`

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
- `200(Updated)`: The geofence was successfully updated.
- `400(Bad Request)`: developer made an error while creating a valid request.
- `401(Unauthorized)`: Access to the API is forbidden.
- `404(Not Found)`: The URL was not found.
- `500(Internal Server Error)`, the request caused an error in our systems.

## **Request Parameter**
| **Parameter** | **Type** | **Location** |  **Required** |**Description** | **Example** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`ID`** | integer | Path | Yes | Id of the existing geofence. | `1608509` |
| `geometry` | string | query | No | GeoJSON string defining the updated geofence shape. Supports `Point` (circular geofence) or `Polygon` (multi-point geofence). | `{'type': 'Point', 'coordinates': [77.2923391217307, 28.55736920869158]}` |
| `name` | string | query | No | Updated name of the geofence. | `geofence_test@123` |
| `buffer` | double | query | No | Radius in meters for circular geofence. If provided, the system updates it as a circular geofence. | `200` |
| `uniqueRefId` | string | query | No | Unique reference ID mapped to the geofence for external tracking or identification. | `233445`|


## **Sample cURL Request**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/geofences/1608509?geometry=%7B%22type%22%3A%22Point%22%2C%22coordinates%22%3A%5B77.2923391217307%2C28.55736920869158%5D%7D&name=geofence_test%40123&buffer=200&uniqueRefId=233445' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{
    "message": " Geofence Updated"
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

