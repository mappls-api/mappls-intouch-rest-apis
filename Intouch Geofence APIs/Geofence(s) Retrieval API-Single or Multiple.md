
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Geofence(s) Retrieval API - Single or Multiple

## **Introduction**

This API allows you to *`fetch geofence details, either for a single geofence or multiple geofences`*. It provides flexibility in retrieving geometry information, such as circles, polygons, or points, based on the ignoreGeometry parameter. Key features include:
1. *`Get Single Geofence:`* Retrieve details of a specific geofence, with or without its geometry value, by setting the *ignoreGeometry* parameter to true or false.
2. *`Get Multiple Geofences:`* Fetch details for an array of geofence IDs, with an option to include geometry by setting the *ignoreGeometry* parameter to false.


## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://www.mapmyindia.com/api/advanced-maps/doc/authentication-api.php).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/json`**


## **Input Method:**
- GET

## **Input URL:**

 > https://intouch.mappls.com/iot/api/geofence/{id}

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

-  `200(OK)`: The request was successfully processed, and the operation was successful.

- `203(Device Not Found)`: No device found with the provided ID.

- `400(Bad Request)`: Invalid ID supplied or invalid data type.

- `401(Unauthorized Request)`: Access to API is forbidden.

- `404(URL Not Found)`: URL Not Found

## **Request Parameters**
> **Note**: **Bold** Ones are Mandatory, *Italic* ones are optional parameters.

| **Parameter** | **Type** | **Description** | **Example** |
| --- | --- | --- | --- |
| **`id`** | integer | geofence id. This path variable will take precedence even if multiple geofence ids are passed in the query param. | 1190516, 1190511 |
| *`ignoreGeometry`* | boolean | Non-mandatory field, Flag to get geometry data. | true |


## **Response Parameters**

| **Field** | **Type** | **Description** |
| --- | --- | --- |
| `id` | number | Geofence ID |
| `name` | string | Name of the geofence |
| `geometry` | object | Defines the geofence type (e.g., Point or Polygon) and includes coordinates as a list of numbers (e.g., [77.456, 28.2345]). |
| `type` | string | Depending on the type of geofence this value can be Circle(buffer > 50 meters), Polygon or Point(buffer = 50 mtrs) |
| `buffer` | number | Radius(in meters) of a circlular geofence |
| `creationTime` | number | epoch timestamp in seconds at which the geofence was created. |
| `updatedTime` | number | epoch timestamp in seconds at which the geofence was updated. |

## **Sample Input**
```
https://intouch.mappls.com/iot/api/geofence?id=1190516, 1190511&ignoreGeometry=true
```
## **Sample ouput**

```json
{
    "data": [
        {
            "id": 1190511,
            "name": "big bazar",
            "type": "Circle",
            "buffer": 1000.0,
            "creationTime": 1736147974,
            "updatedTime": 1736222803
        },
        {
            "id": 1190516,
            "name": "AIIMS",
            "type": "Circle",
            "buffer": 1000.0,
            "creationTime": 1736150681,
            "updatedTime": 1736150681
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




<div align="center">@ Copyright 2022 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

