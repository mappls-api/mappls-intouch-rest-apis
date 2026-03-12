
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Update Entities Group API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**

The *`Update Entities Group API`* provides a simple yet powerful way to *`modify existing enity groups`*. By passing the *group ID along with the new details, you can update the group’s name, associated devices, and color code. Whether you want to change the name of the group, add new devices to it, or update its visual representation with a new color code*, this API enables you to do so efficiently.

With just a few parameters, you can ensure your entity groups are kept up-to-date and properly organized for optimal management. This API is ideal for maintaining dynamic group configurations and adapting to evolving device setups.
> **Note:** Ensure the group exists before attempting an update. Use the [Fetch Entities Group API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/InTouch%20Fleet%20Management%20APIs/Intouch%20Entities%20Group%20APIs/Fetch%20Entities%20Group%20API.md) and [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/InTouch%20Fleet%20Management%20APIs/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md) API to obtain the corresponding `groupId` and `entityId`, respectively.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**
 

## **Input Method:** 
- POST

## **Input URL:**
> `https://intouch.mappls.com/iot/api/group/{id}`

## **Request Parametrs**

The **“bold”** one's are mandatory, and the *“italic”* one's are optional.

| **Parameter**   | **Type** | **Location** | **Description** | **Example** |
| --- | --- | --- | --- | --- |
| **`id`** | number | path | This the ID of the group which you want to update. | `10084` |
| *`name`* | string | query | This the name of the group which you want to update. | `vandana_test` |
| *`entityId`* | number | query | These are the IDs of the entity which you want to update in this group. You can pass a single entity id or a set of multiple ids separated by comma. | `5547807`, `5547876`, `14414276` |
| *`colorCode`* | string | query | This the color code(in hex format) which you want to associated with the group. | #027853 |

## **Response Code**

| **Code** | **Description** |
| --- | --- |
| `200(Successful operation)` | The group has been successfully updated. |
| `203(Device Not Allowed)` | The specified devices are not allowed to be associated with the group. |
| `400(Bad Request)` | Invalid ID or invalid data type provided. |
| `401(Unauthorized Request)` | Access to the API is forbidden due to lack of proper authorization. |   `
| `404(Not Found)` | The requested URL or group ID was not found. |

## **Response Parameters**
The response of this API would be empty. Success would be denoted by the response codes and error would be denoted with the response codes while information on what went wrong with the request in-case of a 400: bad request would be a part of the response headers message.

## **Sample cURL Request**
```bash
curl --location --request POST 'https://intouch.mapmyindia.in/iot/api/groups/10084?colorCode=%23027853&name=vandana_test&deviceId=5547807%2C%205547876%2C%2014414276' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
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




<div align="center">@ Copyright 2026 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

