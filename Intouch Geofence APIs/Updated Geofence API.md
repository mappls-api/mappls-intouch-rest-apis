
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Updated Geofence API

## **Introduction**

This API allows users to *`update the details of existing geofence`* in the system. Using the unique Geofence ID, you can modify attributes such as the geofence name, latitude, longitude, and radius based on the type of geofence (point, circle, or polygon).

1. *`Point Geofence:`* Update geofence name and precise latitude/longitude coordinates.
2. *`Circle Geofence:`* Update geofence name, latitude, longitude, and radius to define circular boundaries.
3. *`Polygon Geofence:`* Update geofence name and the set of latitude/longitude coordinates forming the polygon boundary.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `multipart/form-data`**


## **Input Method:**
- POST

## **Input URL:**
> https://intouch.mappls.com/iot/api/geofence/{id}

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- `200(Updated)`: The geofence was successfully updated.
- `400(Bad Request)`: User made an error while creating a valid request.
- `401(Unauthorized)`: Access to the API is forbidden.
- `404(Not Found)`: The URL was not found.
- `500(Internal Server Error)`, the request caused an error in our systems.

## **Mandatory Request Parameter**

| **Parameter** | **Type** | **Location** | **Description** | **Example** |
| --- | --- | --- | --- | --- |
| **`ID`** | integer | Path | Mandatory field, Id of the existing geofence. | 1190820 |

## **Body Request Parameter**

- **`name`**(string): Name of the geofence. `Example: "market"`

- **`buffer`**(integer): Buffer is nothing but radius in meters. If passed then by default the system will create a circle geofence. If buffer is not passed then by default the system will create a 'point' type geofence with radius as 50 meters `Example: 1000`

- **`geometry`**(string): This is a geoJSON string. You can pass here either 'Point' or 'Polygon'. Point is used for circular geofence, and Polygon is used for a multiple point polygon geofence. `Example:
{ "type": "Point", "coordinates": [77.2334, 28.7676] }`

## **Sample Request cURL**

```bash
curl --location 'https://intouch.mappls.com/iot/api/geofence/1190820' \
--header 'accept: */*' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Content-Type: multipart/form-data' \
--header 'Cookie: HttpOnly' \
--form 'name="Air-port Parking"' \
--form 'geometry="{\"type\":\"Point\",\"coordinates\":[77.08128001958539,28.568242691456405,77.08128001958539,28.539969794077948,77.11440689368595,28.539969794077948,77.11440689368595,28.568242691456405,77.08128001958539,28.568242691456405]}"' \
--form 'buffer="500"'
```

## **Sample ouput**

```json
{
    "message":" Geofence Updated"
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

