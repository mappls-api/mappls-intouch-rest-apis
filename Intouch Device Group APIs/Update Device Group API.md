
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Update Device Group API

## **Introduction**

The *`Update Device Group API`* provides a simple yet powerful way to *`modify existing device groups`*. By passing the *group ID along with the new details, you can update the group’s name, associated devices, and color code. Whether you want to change the name of the group, add new devices to it, or update its visual representation with a new color code*, this API enables you to do so efficiently.

With just a few parameters, you can ensure your device groups are kept up-to-date and properly organized for optimal management. This API is ideal for maintaining dynamic group configurations and adapting to evolving device setups.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `multipart/form-data`**
 

## **Input Method:** 
- POST

## **Input URL:**
 > https://intouch.mappls.com/iot/api/group/{id}

## **Request Parametrs**

The **“bold”** one's are mandatory, and the *“italic”* one's are optional.
Path Parameters:v 

| **Parameter**   | **Type** | **Location** | **Description** | **Example** |
| --- | --- | --- | --- | --- |
| **`id`** | number | path | This the ID of the group which you want to update. | `8228` |
| **`name`** | string | query | This the name of the group which you want to update. | `mappls testing_devices` |
| *`deviceId`* | number | query | These are the IDs of the devices which you want to update in this group. You can pass a single device id or a set of multiple ids separated by comma. | `[1412585, 1441232, 1449737]` |
| *`colorCode`* | string | query | This the color code(in hex format) which you want to associated with the group. | `null` |

## **Response Code**

| **Code** | **Description** |
| --- | --- |
| `200(Successful operation)` | The group has been successfully updated. |
| `203(Device Not Allowed)` | The specified devices are not allowed to be associated with the group. |
| `400(Bad Request)` | Invalid ID or invalid data type provided. |
| `401(Unauthorized Request)` | Access to the API is forbidden due to lack of proper authorization. |   `
| `404(Not Found)` | The requested URL or group ID was not found. |

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/group/8228#027853' \
--header 'accept: */*' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Content-Type: application/form-data' \
--header 'Cookie: HttpOnly; HttpOnly' \
--data '{
            "id": 8228,
            "name": "mappls testing_devices",
            "deviceId": [
                1412585,
                1441232,
                1449737
            ],
            "colorCode": null
        }'
```
## **Sample output**

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




<div align="center">@ Copyright 2025 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

