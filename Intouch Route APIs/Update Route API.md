
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Update Route API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/vandana-gupta8020/Intouch-APIs/tree/main/InTouch%20Fleet%20Management%20APIs).**

## **Introduction**
The `Update Route API` allows you to modify an existing route associated with an InTouch user. By providing the route ID, you can update route details such as the route name, associated geofences, route type, distance, and other configurable attributes. This API is used when route information needs to be edited or refined after creation.
> **Note:** Ensure the route exists before attempting an update. Use the [Routes Retrieval API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Route%20APIs/Routes%20Retrieval%20API.md) to obtain the corresponding routeId.

## **Security Type**

This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method:**
- POST
## **Input URL**

`https://intouch.mappls.com/iot/api/route/{id}`

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
| **HTTP Code** | **Message** | **Description** |
| --- | --- | --- |
| **201** | Created | Route created successfully. |
| **400** | Bad Request | The request is invalid or contains incorrect parameters. Example: `{"error": "Minimum number of geofenceId entered should be 2."}` or `{"error": "Please enter a valid geofenceId"}`|
| **401** | Unauthorized | Invalid or missing authorization token. |
| **403** | Forbidden | Access to the API is not allowed for the provided credentials. |
| **404** | Not Found | The requested resource or endpoint does not exist. |


## **Request Parameters**
The **`“bold”`** one's are mandatory, and the *`“italic”`* one's are optional.
1. **`id`** (long, path): Unique ID of the route to be updated. 
2. `name`(string): Updated name of the route.
3. `geofenceId`(Array[long]): List of geofence IDs to associate with the route. Multiple values can be provided.
4. `routeType`(string): Type/category of the route. 
5. `distance`(double): Total distance of the route.
6. `type`(integer): Route type identifier (if applicable).
7. `accountId`(long): Account ID associated with the route.

## **Response Parameters**
The response of this API would be empty. Success would be denoted by the response codes and error would be denoted with the response codes while information on what went wrong with the request in-case of a 400: bad request would be a part of the response headers message.

## **Sample cURL Request**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/route/3823786?name=test%403452jhj&geofenceId=438123%2C438125%2C438126&routeType=1' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{}
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

