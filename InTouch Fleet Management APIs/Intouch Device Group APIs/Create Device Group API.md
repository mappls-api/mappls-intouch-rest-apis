
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Create Device Group API

## **Introduction**

This API is used to *`create a group for devices`*. By passing the required parameters, you can create a group that includes one or multiple devices. You can also associate a color code with the group to visually represent it.


## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `multipart/form-data`**

## **Input Method:** 
- POST

## **Input URL:**

 > https://intouch.mappls.com/iot/api/group


## **Request Body Parametrs**

- **`name`**(string): This the name of the group which you want to create. `Example: MapmyIndia(tesing_device)`
- *`deviceId`*(number): These are the IDs of the devices which you want to have in this group. You can pass a single device id or a set of multiple ids separated by comma. `Example: 10647019,2986152,3042309`
- *`colorCode`*(string): This the color code(in hex format) which you want to associated with the group. `Example: #9868c4`
 
## **Response Type**
- JSON

## **Response Codes** {as HTTP response code}

1. `201(Created)`: Group has been successfully created.
2. `203(Device Not Found)`: The provided deviceId is not found or invalid.
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


## **Sample cURL**

```bash
curl --location 'https://intouch.mappls.com/iot/api/group' \
--header 'accept: */*' \
--header 'Authorization: Bearer 57a5c4d1-cb05-47c7-ba82-ce11e493a850' \
--header 'Content-Type: multipart/form-data' \
--header 'Cookie: HttpOnly; HttpOnly; HttpOnly' \
--form 'name="Tesing_device group"' \
--form 'deviceId="10647019, 2986152, 3042309"' \
--form 'colorCode="\#8562bf"'
```
## **Sample Output**
```json
{
  "id": 8232
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

