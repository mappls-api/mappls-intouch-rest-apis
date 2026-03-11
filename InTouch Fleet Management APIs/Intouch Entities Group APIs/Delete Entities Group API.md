
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Delete Entities Group API
> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/vandana-gupta8020/Intouch-APIs/tree/main/InTouch%20Fleet%20Management%20APIs).**

## **Introduction**

The *`Delete Entities Group API`* offers a quick and effective way to remove unwanted or obsolete entities groups from your platform. With a simple DELETE request, you can permanently delete a specific entity group using its unique group ID. This API is perfect for maintaining a clean, organized environment by eliminating entity groups that are no longer necessary, ensuring that your platform remains streamlined and up to date.

Whether you need to clear up unused groups or perform administrative cleanup, this API gives you the power to manage your device groups efficiently.
> **Note:** Ensure the group exists before attempting deletion. Use the [Fetch Entities Groups API](https://github.com/vandana-gupta8020/Intouch-APIs/blob/main/InTouch%20Fleet%20Management%20APIs/Intouch%20Entities%20Group%20APIs/Fetch%20Entities%20Groups%20API.md) to obtain the corresponding `groupId`.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**

- **Content-Type Header:** **`Optional, Not required for this API unless sending body data.`**
 

## **Input Method:** 
- DELETE

## **Input URL:**
> `https://intouch.mappls.com/iot/api/groups/{id}`

## **Request Parametrs**
| **Parameter**   | **Type** | **Location** | **Required** | **Description** | **Example** |
| --- | --- | --- | --- | --- | --- |
| **`id`** | integer | path | Mandatory |This is the ID of the group you want to delete. | `10087` |

## **Response Code**

| **Code** | **Description** |
| --- | --- |
| `200(Successful operation)` | The group has been successfully deleted. |
| `204(No Content)` | The group could not be found or was already deleted. |
| `400(Bad Request)` | Invalid group ID or data type provided. |
| `401(Unauthorized Request)` | Access to the API is forbidden due to insufficient permissions. |   `
| `404(Not Found)` | The requested group ID or URL was not found. |

## **Response Parameters**
The response of this API would be empty. Success would be denoted by the response codes and error would be denoted with the response codes while information on what went wrong with the request in-case of a 400: bad request would be a part of the response headers message.

## **Sample cURL Request**

```bash
curl --location --request DELETE 'https://intouch.mappls.com/iot/api/groups/10087' \
--header 'Accept: text/plain' \
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

