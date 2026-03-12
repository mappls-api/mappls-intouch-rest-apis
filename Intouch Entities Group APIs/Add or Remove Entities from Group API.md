
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Add or Remove Entities from Group API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Add or Remove Entities from Group API` allows you to manage entity membership within an existing group, where an entity refers to a device. Using this API, you can either add entities to a group or remove them by simply controlling the `isAdd` flag in the request. This helps maintain accurate and up-to-date group configurations as your fleet changes over time. The API is especially useful for dynamically organizing entities without recreating groups. It ensures efficient group management and operational flexibility.

> **Note:** Ensure the required entityId and groupId are valid and already exist. Use the [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md) to obtain the required `entityId` and the [Fetch Entities Group API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Entities%20Group%20APIs/Fetch%20Entities%20Group%20API.md) to obtain the corresponding `groupId`.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method:** 
- POST

## **Input URL:**
> https://intouch.mappls.com/iot/api/group/addRemoveEntity

## **Response Type**
- JSON

## **Response Codes** {as HTTP response code}
1. `201` (Created): Entity successfully added to or removed from the group.
2. `203` (Entity Not Found): The provided entityId is invalid or does not exist.
3. `204` (No Content): No data found.
4. `400` (Bad Request): Invalid Entity ID supplied or invalid data type.
5. `401` (Unauthorized): Missing or invalid authorization credentials.
6. `404` (Not Found): The requested endpoint does not exist.


## **Request Body Parameters**
The **`"bold"`** parameters are mandatory and the *`"italic"`* parameters are optional.
- **`entityId`** (number): ID(s) of the entity (device) to be added or removed from the group. Multiple IDs can be passed as comma-separated values.
- **`groupId`** (number): Unique identifier of the target group.
- *`isAdd`* (boolean): Controls the action to be performed on the group.
    - *`true`*: Adds the entity to the group
    - *`false`*: Removes the entity from the group

## **Sample cURL when removing entity from the group**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/group/addRemoveEntity?entityId=14414276&groupId=10084&isAdd=false' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample cURL when adding entity in the existing group**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/group/addRemoveEntity?entityId=14414276&groupId=10088&isAdd=true' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Response Parameters**
The response body of this API is empty. Success or failure is indicated through HTTP response codes. In case of a `400 Bad Request`, additional error details may be available in the response headers.







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

