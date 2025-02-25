
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Delete Geofence API

## **Introduction**

This API allows you to *`delete one or more geofences`*. You can delete geofences using the following methods:

1. *`Delete a Single Geofence:`*: To delete a particular geofence by mentioning the geofence ID.

2. *`Delete Multiple Geofences:`*: To delete multiple geofences by providing a list of geofence IDs.


## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type:** *`Optional, Not required for this API unless sending body data.`*

## **Input Method:**
- Delete

## **Input URL:**
> https://intouch.mappls.com/iot/api/geofence/{id}

## Success:
1. `200(deleted)`: The geofence was successfully deleted.

## Client-side issues:
1. `400(Bad Request)`: User made an error while creating a valid request.
2. `401(Unauthorized)`: the Developer’s key is not allowed to send a request with restricted parameters.
3. `403(Forbidden)`: the Developer’s key has hit its daily/hourly limit.

## Server-Side Issues:
1.  `500`: Internal Server Error, the request caused an error in our systems.
2.  `503`: Service Unavailable, during our maintenance break or server downtimes.

## Response Messages (as HTTP response message)
1. `200`: Success
2. `203`: Device Not Found
3. `400`: Bad Request - Invalid device ID supplied or invalid data type. For example, the input attribute "id" is an integer but string value gets passed.
4. `401`: Unauthorized Request. Access to API is forbidden.
5. `404`: Not Found - URL Not Found

## **Response Parameters**
The response of this API would be empty. Success would be denoted by the response codes and error would be denoted with the response codes while information on what went wrong with the request in-case of a 400: bad request would be a part of the response headers message.

## **Sample Request cURL**

```bash
curl --location --request DELETE 'https://intouch.mappls.com/iot/api/geofence/1191001,1191002' \
--header 'accept: */*' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
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




<div align="center">@ Copyright 2025 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

