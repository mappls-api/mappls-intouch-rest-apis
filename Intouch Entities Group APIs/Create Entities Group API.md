
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Create Entities Group API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Create Entities Group API` allows you to create and manage logical groups of entities (devices) within the platform. By providing the required parameters, you can create a new group and assign one or multiple entity IDs in a single request. You can also associate a hex color code with the group for easy visual identification in the application interface. This API helps streamline device organization, monitoring, and operational management, especially when handling large fleets of devices.

> **Note:** Ensure that valid device IDs are available before creating a group. Use the [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md) to obtain the required `deviceId`.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method** 
- POST

## **Input URL**
> https://intouch.mappls.com/iot/api/groups

## **Response Type**
- JSON

## **Response Codes** {as HTTP response code}

1. `201(Created)`: Group has been successfully created.
2. `203(Device Not Found)`: The provided enityId is not found or invalid.
3. `204(No Content)`: No data found.
4. `400(Bad Request)`: Invalid ID supplied or invalid data type.
    -  Example:
        ```json
        {
          "status": "error",
          "message": "Invalid ID supplied",
          "error": "Invalid deviceId"
        }
        ```
5. `401(Unauthorized)`: The API request is forbidden, possibly due to missing or invalid authorization credentials.
6. `404(Not Found)`: The requested URL endpoint does not exist.

  
## **Request Body Parametrs**
Parameters marked in **`bold`** are mandatory, and those in *`italics`* are optional:
- **`name`**(string): This the name of the group which you want to create. `Example: Test_vandana`
- **`entityId`**(number): These are the IDs of the entities that you want to include in this group. You can pass a single entity ID or multiple IDs separated by commas. `Example: 5547807, 5547876`
- *`colorCode`*(string): This the color code(in hex format) which you want to associated with the group. `Example: #9CBF63`
   
## **Response Parametrs**
- **`groupId`**: This is the generated group Id.

## **Sample cURL**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/groups?name=Test_vandana&colorCode=%239CBF63&deviceId=5547807%2C%205547876' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{
    "groupId": 10084
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




<div align="center">@ Copyright 2026 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

