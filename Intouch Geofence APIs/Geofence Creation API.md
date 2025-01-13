
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Geofence Creation API

## **Introduction**

This API helps to *`create a new geofence`*. A geofence is a user-defined boundary area that triggers Entry and Exit alerts for users or vehicles. Custom areas or places can be created as geofences under your account. The Geofence Creation API allows you to create three types of geofences:

1. **`Point Geofence`**: Input the Latitude, Longitude, and Name of the geofence. This geofence has a fixed radius of 100 meters. No radius input is required for a Point Geofence. If you need a custom radius, refer to the Circle Geofence method.

2. **`Circle Geofence`**: Input Latitude, Longitude, Radius, and Name to create a circle-shaped geofence. You can define the radius to meet your specific requirements.

3. **`Polygon Geofence`**: To create a polygon geofence, input a list of at least three Latitude and Longitude points. More points can be added to create a custom-shaped geofence. The points should be provided in a comma-separated format.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://www.mapmyindia.com/api/advanced-maps/doc/authentication-api.php).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/form-data`**


## **Input Method:**
- POST

## **Input URL:**
> https://intouch.mappls.com/iot/api/geofence/

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- `201(created)`: The geofence was successfully created.
- `203(Device Not Found)`: The device was not found.
- `400(Bad Request)`: User made an error while creating a valid request.
- `401(Unauthorized)`: Access to the API is forbidden.
- `404(Not Found)`: The URL was not found.
- `500(Internal Server Error)`, the request caused an error in our systems.

## **Body Request Parameter**

- **`name`**(string): Name of the geofence. `Example: "market"`
- **`buffer`**(integer): Buffer is nothing but radius in meters. If passed then by default the system will create a circle geofence. If buffer is not passed then by default the system will create a 'point' type geofence with radius as 50 meters `Example: 1000`

- **`geometry`**(string): This is a geoJSON string. You can pass here either 'Point' or 'Polygon'. Point is used for circular geofence, and Polygon is used for a multiple point polygon geofence. `Example:
{ "type": "Point", "coordinates": [77.2334, 28.7676] }`

## **Sample Request cURL**

```bash
curl --location 'https://intouch.mapmyindia.in/iot/api/geofence/' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly; HttpOnly' \
--form 'name="Air-port Entrance"' \
--form 'geometry="{\"type\": \"Polygon\", \"coordinates\":[[[77.08128001958539,28.568242691456405],[77.08128001958539,28.539969794077948],[77.11440689368595,28.539969794077948],[77.11440689368595,28.568242691456405],[77.08128001958539,28.568242691456405]]]}"'
```

## **Sample ouput**

```json
{
    "id":1191004
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

