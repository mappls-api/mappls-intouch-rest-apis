
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch All Configured Geofences API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Fetch All Configured Geofences API` allows developers to retrieve the list of geofences configured under their account. It provides detailed information such as geofence ID, name, type, creation time, and other associated attributes.

The API also supports the option to include or exclude geofence geometry details (Point, Polygon, or Circle) using the `ignoreGeometry` parameter. If no specific geofence ID is provided, the API returns all geofences configured for the developer.
> **Note:** Ensure the required geofences are already created. If not, Use the [Geofence Creation API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/InTouch%20Fleet%20Management%20APIs/Intouch%20Geofence%20APIs/Geofence%20Creation%20API.md) 
 to create them.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method:**
- GET
## **Input URL:**

 > https://intouch.mappls.com/iot/api/geofences

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**

- 200 `OK` - The request was successfully processed, and the operation was successful.
- 203 `Device Not Found` - No device found with the provided ID.
- 400 `Bad Request` - developer made an error while creating a valid request.
- 401 `Unauthorized Request` - Access to API is forbidden.
- 404 `URL Not Found` - URL Not Found

## **Request Parameters**
All listed parameters are `non-mandatory` for this API.
| **Parameter** | **Type** | **Description** | **Example** |
| --- | --- | --- | --- |
| `id` | Array[long] (query) | Unique ID(s) of the geofence(s) to retrieve. If not provided, all configured geofences will be returned. Multiple IDs can be passed as comma-separated values. | `1190907`,`1191004` |
| `ignoreGeometry` | boolean (query) | Determines whether the geofence shape details (Point, Polygon, Circle) should be excluded from the response. Default value is `false`. | `true` |


## **Response Parameters**

| **Field** | **Type** | **Description** |
| --- | --- | --- |
| `id` | integer | Geofence ID |
| `name` | string | Name of the geofence |
| `geometry` | object | Defines the geofence type (e.g., Point or Polygon) and includes coordinates as a list of numbers (e.g., [77.456, 28.2345]). |
| `type` | string | Depending on the type of geofence this value can be Circle(buffer > 50 meters), Polygon or Point(buffer = 50 mtrs) |
| `buffer` | number | Radius(in meters) of a circlular geofence |
| `creationTime` | number | epoch timestamp in seconds at which the geofence was created. |
| `updatedTime` | number | epoch timestamp in seconds at which the geofence was updated. |

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/geofences?id=438127%2C%20438129%2C%20438125&ignoreGeometry=false' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```
## **Sample Output Response**

```json
{
    "data": [
        {
            "id": 438125,
            "name": "INRJ003160",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    76.251,
                    27.818
                ]
            },
            "type": "Point",
            "buffer": 50.0,
            "creationTime": 1565247738,
            "updatedTime": 1765877993
        },
        {
            "id": 438127,
            "name": "INRJ002716",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    75.778,
                    25.249
                ]
            },
            "type": "Point",
            "buffer": 50.0,
            "creationTime": 1565247738,
            "updatedTime": 1759816954
        },
        {
            "id": 438129,
            "name": "INRJ001972",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    76.765,
                    26.05
                ]
            },
            "type": "Point",
            "buffer": 50.0,
            "creationTime": 1565247738,
            "updatedTime": 1759816511
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

