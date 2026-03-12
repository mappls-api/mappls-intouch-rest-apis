
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch Live Video Embed URL API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Fetch Live Video Embed URL API` allows you to retrieve a secure, embeddable live video streaming URL for a specified device. This API is typically used when real-time monitoring of a vehicle or asset is required through integrated camera systems.

By providing the required device details, the API generates a live video embed link that can be directly integrated into web applications, dashboards, or monitoring platforms using an `<iframe>` or similar embedding mechanism.

- The live stream can be requested for one or multiple available camera channels associated with the device, such as:
    - `Front` – Captures the forward road view
    - `Cabin` – Monitors inside the vehicle cabin
    - `Driver` – Focuses specifically on the driver
    - `Rear`– Captures the rear-side view
    
### **Device Identification Requirements**
- Certain APIs require a deviceId to be passed as part of the path parameters or query parameters.
- If the deviceId is not already available, developers can retrieve a list of registered devices by invoking the [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md).
- The device details obtained from the Retrieve Basic Information of Device API can then be used to make subsequent API calls that depend on device-specific identifiers.


## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices/video/live

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
- `200` (OK): Successful operation. Live video embed URL retrieved successfully.
- `203` (Device Not Found): The specified device ID was not found in the system.
- `400` (Bad Request): Invalid request parameters or incorrect data type passed (e.g., invalid channel name).
- `401` (Unauthorized): The request is forbidden due to missing or invalid authentication/authorization.
- `404` (Not Found): The specified URL was not found.

## **Request Parameters**

The **`"bold"`** parameters are mandatory, and the *`"italic"`* parameters are optional.
| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| **`deviceId`** | number | The unique ID of the device for which the live video feed is requested. |
| **`channels`** | string | One or more camera channels for which the live feed is required. Multiple channels must be separated by commas. Channel Description: `Front=(1)`: Front-facing camera; `Cabin=(2)`: Cabin/internal camera; `Driver=(3)`: Driver-facing camera; `Rear=(4)`: Rear-facing camera|

## **Response Parameters**
- **`embedUrl`**: The embeddable URL for accessing the live video feed of the requested device and channels. This URL can be directly embedded in a web or mobile application to stream live video.


## **Sample cURL Resquest**  
```bash
curl --location 'https://intouch.mappls.com/iot/api/devices/video/live?channels=Front%2C%20Rear%2C%20Cabin%2C%20Driver&deviceId=14414276' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```

## **Sample Output Response** 
```json
{
    "data": {
        "embedUrl": "https://intouch.mappls.com/widget/video/live/#/14414276?access_token=0498703b-8a77-4c3f-91dd-0d0a4b5c9dd3&channels=1,2,3"
    }
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

