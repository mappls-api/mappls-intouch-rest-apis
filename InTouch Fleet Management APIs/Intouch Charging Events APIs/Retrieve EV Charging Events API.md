
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Retrieve EV Charging Events API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/vandana-gupta8020/Intouch-APIs/tree/main/InTouch%20Fleet%20Management%20APIs).**

## **Introduction**
This API *`retrieves the details of charging events performed by electric vehicles (EVs)`*. It returns a list of parameters for each charging event, including start time, end time, location, and other relevant details within a specified time range.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method:**
- GET

## **Input URL:**
> https://intouch.mappls.com/iot/api/devices​/chargingEvents

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
1. *`200(OK)`*: The request was successful, and the response contains charging event data.
2. *`203(Device Not Found)`*: The specified device was not found.
3. *`400(Bad Request)`*: Invalid input provided. For instance, the `deviceId` should be an integer but was supplied as a string.
4. *`401(Unauthorized)`*: The request was unauthorized; access to the API is forbidden.
5. *`404(Not Found)`*: The requested URL or resource was not found.

## **Request Parameters**
The **`“bold”`** one's are mandatory, and the *`“italic”`* one's are optional.

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| **`deviceId`** | integer | ID of the device for which the events need to be fetched. |
| *`startTime`* | number  | The starting timestamp (in epoch format) from which the events need to be fetched. |
| *`endTime`*   | number  | The ending timestamp (in epoch format) till which the events need to be fetched. |

## **Response Parameters**

| **Field** | **Type** | **Description** |
| --- | --- | --- |
| `entityId` | number | The device ID. |
| `startTime` | number | Start time of the charging event in epoch values. |
| `endTime` | interger | End time of the charging eventin epoch values. |
| `duration` | interger | Duration of the charging event in seconds. |
| `latitude` | interger | Latitude coordinate of the charging event location. |
| `longitude` | interger | Longitude coordinate of the charging event location. |
| `chargingType` | boolean | Charging type (Fast charge: `1`, Slow charge: `0`). |
| `startSoc` | interger | SOC (State of Charge) percentage at the beginning of the charging event. |
| `endSoc` | interger | SOC (State of Charge) percentage at the end of the charging event. |
| `startDte` | interger | Distance to Empty (DTE) in kilometers at the beginning of the charging event. |
| `endDte` | interger | Distance to Empty (DTE) in kilometers at the end of the charging event. |
| `chargeAccumulated` | interger | Total charge accumulated (in kWh) during the charging event. |


## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/devices/chargingEvents/devices/chargingEvents?deviceId=10647019&startTime=1661026455&endTime=1661029580' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{
  "description": "The response of the API with data",
  "data": [
    {
      "entityId": "14385087",
      "startTime": 1661026455,
      "endTime": 1661029580,
      "duration": 3125,
      "latitude": 28.621429419646432,
      "longitude": 77.3567914740013,
      "chargingType": 0,
      "startSoc": 63,
      "endSoc": 100,
      "startDte": 89,
      "endDte": 145,
      "chargeAccumulated": 37
    }
  ]
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

