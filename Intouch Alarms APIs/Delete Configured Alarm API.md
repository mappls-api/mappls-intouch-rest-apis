
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Delete Configured Alarm API

## **Introduction**

The *`Delete Configured Alarm API`* is used to delete a specific alarm configuration from the system. This API requires the unique identifier (ID) of the alarm configuration that you wish to remove. It performs a DELETE operation, which, once successfully executed, removes the specified alarm from the system.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `{token_type} {access_token}.`**

- **Content-Type:** *`Optional, Not required for this API unless sending body data.`*

## **Input Method:** 
- DELETE

## **Input URL**

> https://intouch.mappls.com/iot/api/alarm/{id}

## **Response Type**
- JSON

## **Response Codes**

| **Status Code** | **Description** |
| --- | --- |
| `200 (OK)` | Successful operation, The operation was successful and the alarm configuration has been deleted. |
| `204 (No Content)` | The operation was successful, but no content is returned (e.g., no alarm found). |
| `400 (Bad Request)` | Invalid ID supplied or invalid data type in the request. |
| `401 (Unauthorized)` | The request is forbidden due to lack of authentication or authorization. |
| `404 (Not Found)` | The specified URL was not found. |

## **Request Mandatory Parameters**

| **Parameter**   | **Type** | **Location** | **Description** | **Example** |
| --- | --- | --- |--- | --- |
| **`id`** | integer | Path | The unique ID of the alarm configuration that you want to delete. | `13401425` |


## **Sample cURL Request**
 ```bash
 curl --location --request DELETE 'https://intouch.mappls.com/iot/api/alarm/13401425' \
--header 'accept: */*' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```

## **Sample Output**

```json
{
    "message": "success"
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




<div align="center">@ Copyright 2025 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

