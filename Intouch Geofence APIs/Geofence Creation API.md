
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Geofence Creation API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
This API `creates a new geofence`. A geofence is a developer-defined boundary area that triggers Entry and Exit alerts for developers or vehicles. Custom areas or places can be created as geofences under your account. The Geofence Creation API allows you to create three types of geofences:
1. **`Point Geofence`**: Provide longitude and latitude, and name of the geofence. This geofence has a fixed radius of 100 meters. No radius input is required for a Point Geofence. If you need a custom radius, refer to the Circle Geofence method.
2. **`Circle Geofence`**: Input Latitude, Longitude, Radius, and Name to create a circle-shaped geofence. You can define the radius to meet your specific requirements.
3. **`Polygon Geofence`**: To create a polygon geofence, input a list of at least three Latitude and Longitude points. More points can be added to create a custom-shaped geofence. The points should be provided in a comma-separated format.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method**
- POST

## **Input URL**
> https://intouch.mappls.com/iot/api/geofences

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
| **Status Code** | **Description** |
| --- | --- |
| `201` (Created) | Geofence created successfully. |
| `400` (Bad Request) | Invalid request parameters or malformed geometry. |
| `401` (Unauthorized) | Missing or invalid authentication token. |
| `404` (Not Found) | Endpoint not found. |
| `500` (Internal Server Error) | Server encountered an unexpected error. |

## **Request Parameter**
The **`Bold`** Ones are Mandatory, *`Italic`* ones are optional parameters.
- **`name`**(string): Name of the geofence. `Example: "geofence_test_123"`
- **`geometry`**(object): GeoJSON object that defines the shape and location of the geofence.
    - **`Polygon`**: Polygon requires at least 3 coordinate points to form a valid shape.
    - **`Point`**: Represents the center of the geofence. When used with the `buffer` parameter, it creates a circular geofence.
    - **Example:**
        ```
        {
        "type": "Point",
        "coordinates": [78.9, 22.06816]
        }
        ```
    > **Note:** Coordinates must be in [longitude, latitude] format.
- *`buffer`*(double): Radius of the geofence in meters. If not provided, default radius is 100 meters. `Example: 200`
- *`uniqueRefId`*(string): Unique reference ID to associate with the geofence for mapping or tracking. `Example: 23344`


## **Response Parameter** 
| **Field** | **Type** | **Description** | **Example** |
| --- | --- | --- | --- |
| `id` | number | Unique ID of the created geofence. | `1608509` |

## **Sample cURL Request**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/geofences?name=geofence_test_123&geometry=%7B%22type%22%3A%22Point%22%2C%22coordinates%22%3A%5B78.9%2C22.06816%5D%7D&buffer=200&uniqueRefId=23344' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response**
```json
{
    "id": 1608509
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

