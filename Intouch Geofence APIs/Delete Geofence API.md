
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Delete Geofence API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Delete Geofence API` allows developers to delete one or more geofences by providing the corresponding `geofenceId`. A single geofence ID can be passed for individual deletion, or multiple geofence IDs can be provided in a single request.
- **Geofence Prerequisite:** Ensure the required geofences are already created. Use the [Geofence Creation API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Geofence%20APIs/Geofence%20Creation%20API.md) to create geofences and the [Fetch All Configured Geofences API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Geofence%20APIs/Fetch%20All%20Configured%20Geofences%20API.md) to obtain the corresponding geofenceId.


## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type:** *`Optional, Not required for this API unless sending body data.`*


## **Input Method**
- DELETE

## **Input URL**
`https://intouch.mappls.com/iot/api/geofences/{id}`

## Response Messages (as HTTP response message)
- `200`(deleted): The geofence was successfully deleted.: Success
- `203`(Device Not Found): No device found with the provided ID.
- `400`(Bad Request): developer made an error while creating a valid request.
- `401`(Unauthorized Request): Access to API is forbidden.
- `404`(Not Found): URL Not Found
- `500`(Internal Server Error): The request caused an error in our systems.
- `503`(Service Unavailable): during our maintenance break or server downtimes.

## **Resquest Parameters**
| **Parameter** | **Type** | **Location** | **Required** | **Description** | **Example** |
| --- | --- | --- | --- | --- | --- |
| `id` | long | path | Yes | Unique ID of the geofence that needs to be deleted. | `438144` |

## **Response Parameters**
The response of this API would be empty. Success would be denoted by the response codes and error would be denoted with the response codes while information on what went wrong with the request in-case of a `400: bad request` would be a part of the response headers message.

## **Sample cURL Request**
```bash
curl --location --request DELETE 'https://intouch.mappls.com/iot/api/geofences/438144' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
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

