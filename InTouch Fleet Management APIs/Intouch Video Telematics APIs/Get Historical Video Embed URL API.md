
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Get Historical Video Embed URL API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
This `Get Historical Video Embed URL API` allows you to fetch the embedded video URL for historical footage of a specific device. The history feed can be requested for one or more available channels (Front, Rear, Cabin, or Driver) by providing the deviceId along with the start time and end time.

### **Device Identification Requirements**
- Certain APIs require a deviceId to be passed as part of the path parameters or query parameters.
- If the deviceId is not already available, users can retrieve a list of registered devices by invoking the [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/InTouch%20Fleet%20Management%20APIs/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md).
- The device details obtained from the Retrieve Basic Information of Device API can then be used to make subsequent API calls that depend on device-specific identifiers.

## **Security Type**

This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method**
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices/video/history

## **Response Codes**
* `200` (Successful operation): Historical video embed URL retrieved successfully.
* `203` (Non-Authoritative Information): Returned when the device is not permitted to access historical video (e.g., `{"error": "Device not allowed"}`).
* `400` (Unauthorized): Missing device Id. e.g., `{"status": "BAD_REQUEST", "message": "Required Long parameter 'deviceId' is not present", z"error": "deviceId parameter is missing"}`
* `401` (Unauthorized): Missing or invalid authentication.
* `403` (Forbidden): Access not allowed for the provided credentials.
* `404` (Not Found): Device or requested data not available.
* `500` (Internal Server Error): Returned when the server fails to process the request due to a server-side issue (e.g., `{"error": "timeout"}`).

## **Request Parameters**
| **Parameter** | **Type** | **Mandatory** | **Description** |
| --- | --- | --- | --- |
| **deviceId** | number (long) | Yes | Unique ID of the device for which historical video is requested. |
| **channels** | array[string] | Yes | One or more camera channels. Multiple values must be comma-separated. Available channels: `Front`, `Rear`, `Cabin`, `Driver`. |
| **startTime** | long | Yes | Start time of the video in Unix timestamp format. |
| **endTime** | long | Yes | End time of the video in Unix timestamp format. |

## **Response Type**
- JSON

## **Response Parameters**
| **Parameter** | **Description** |
| --- | --- |
| **embedUrl** | A link that can be directly added (embedded) into your web or mobile app to play the historical video. |
| **shareUrl** | A link that can be shared with others to view the historical video in a browser. |


## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/devices/video/history?deviceId=14414276&channels=Front,Rear,Cabin,Driver&startTime=1770800820&endTime=1770802593' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6'
```

## **Sample Response**
```json
{
    "data": {
        "embedUrl": "https://intouch.mappls.com/widget/video/history/#/10667630?access_token=efd5608d-c666-42c1-9b16-c031b1b5b7ea&channels=1,2&startTime=1770661800&endTime=1770748199&isMultiChn=false&playerType=iframe"
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

