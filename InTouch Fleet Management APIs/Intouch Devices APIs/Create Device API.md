
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Create Device API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/vandana-gupta8020/Intouch-APIs/tree/main/InTouch%20Fleet%20Management%20APIs).**

## **Introduction** 
The `Create Device API` registers a new device in the InTouch system by creating a unique device record. This device can then be used for tracking and monitoring through web and mobile platforms. By providing details like tracking code, device type, and registration number, it creates a unique device record for tracking and monitoring across web and mobile platforms.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method:** 
- POST

## **Input URL**

> https://intouch.mappls.com/iot/api/device


## **Response Type**
- JSON

## **Response Codes**
| **Status Code** | **Description** |
| --- | --- |
| `201 (Created)` | Device created successfully. |
| `400(Bad Request)` | Missing mandatory parameter or invalid input. Possible messages: `Required String parameter 'deviceName' is not present` or `No tracking key found`.|
| `401(Unauthorized)` | Invalid or expired access token. |

## **Request Parameters**
| **Parameter** | **Type** | **Required** | **Description** |
| --- | --- | --- | --- |
| **`deviceName`** | string | Yes | Name of the device. |
| **`trackingCode`** | string | Conditional | Unique tracking code. Required if `deviceCode` is not provided.   |
| **`deviceCode`** | string | Conditional | Device-specific code. Required if `trackingCode` is not provided. |
| *`deviceType`* | integer | No | Identifier representing the device type. |
| *`deviceTypeName`* | string | No | Name of the device type. |
| *`expiry`* | long | No | Expiry timestamp for the device. |
| *`registrationNo`* | string | No | Registration number of the device. |
| *`entityType`* | integer | No | Entity type associated with the device. |


## **Response Parameters**
- **`crashdetection`** (object): Contains configuration parameters related to crash detection thresholds.
    - **`minGValueHeavyCrash`** (number): Minimum G-force threshold configured for detecting heavy crash events. `Example: null`
    - **`minGValue`** (number): General G-force threshold used for crash detection. `Example: null`
    - **`minGValueLightCrash`** (number): Minimum G-force threshold configured for detecting light crash events. `Example: null`
    - **`minGValueHaHb`** (number): Minimum G-force threshold used for detecting harsh acceleration or harsh braking events. `Example: null`
- **`entityId`** *(integer): Identifier representing the entity to which the device belongs. `Example: 14385087`
- **`trackingCode`** (string): Tracking code associated with the device used for identification and tracking. `Example: abcd123`
- **`deviceId`** (integer): Unique identifier assigned to the device after successful creation. `Example: 9086280`
- **`key`** (string): Unique authentication key generated for the device. This key is used internally by the system for device communication and verification. `Example: D9E6EA2C6D79BF19899149C29B544A1F6D208A079B163410`

## **Sample cURL Request**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/device?trackingCode=abcd123&deviceCode=123abcd&deviceType=35&deviceTypeName=Beacon&deviceName=mappls_test_device&expiry=1806987140&registrationNo=123abcdabcd123204466&entityType=1' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response**

```json
{
    "crashdetection": {
        "minGValueHeavyCrash": null,
        "minGValue": null,
        "minGValueLightCrash": null,
        "minGValueHaHb": null
    },
    "entityId": 14385087,
    "trackingCode": "abcd123",
    "deviceId": 9086280,
    "key": "D9E6EA2C6D79BF19899149C29B544A1F6D208A079B163410"
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

