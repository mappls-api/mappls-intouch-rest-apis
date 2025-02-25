
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch Device Activities with Respect to Geofences API

## **Introduction**
This API helps *`fetch the details of all activities performed by devices with respect to various geofences`*, such as entry and exit times, across a defined date/time range.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `application/json`**


## **Input Method:**
- GET

## **Input URL:**

 > https://intouch.mappls.com/iot/api/geofence/activity

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

-  `200(OK)`: The request was successfully processed, and the operation was successful.

- `203(Device Not Found)`: No device found with the provided ID.

- `400(Bad Request)`: Invalid ID supplied or invalid data type.

- `401(Unauthorized Request)`: Access to API is forbidden.

- `404(URL Not Found)`: URL Not Found

## **Request Parameters**
> **Note**: **Bold** Ones are Mandatory, *Italic* ones are optional parameters.

| **Parameter** | **Type** | **Description** | **Example** |
| --- | --- | --- | --- |
| **`deviceId `** | string | Id of the device(s) for which you want to fetch the geofence activities. For multiple devices, you can pass comma separated device ids as well in the query string. | 10807208, 10647019 |
| **`startTime`**  | number | Value in timestamp. Start time from where you want to fetch the geofence activities | 1736492081 |
| **`endTime`**  | number | Value in timestamp. End time till where you want to fetch the geofence activities. | 1736751281 |
| *`geofenceId`* | string | Id of the geofence(s) for which you want to fetch the geofence activities done by the device. For multiple geofences, you can pass comma separated geofence ids as well in the query string. | 1190907,1191004 |


## **Response Parameters**

| **Field** | **Type** | **Description** |
| --- | --- | --- |
|`entryLongitude` | number | longitude where the particular device entered the geofence. |
|`entryLatitude` | number | latitude where the particular device entered the geofence.|
|`exitLongitude` | number | longitude where the particular device exited the geofence.|
|`exitLatitude` | number | latitude where the particular device exited the geofence.|
|`entryTimestamp` | number | time at which the device entered the particular geofence.|
|`exitTimestamp` | number | time at which the device exited the particular geofence.|
|`geofenceName` | string | name of the geofence |
|`geofenceId` | number | the id of the geofence where the activity took place. |
|`deviceId` | number | the id of the device which is performing the activities w.r.t the geofence. |

## **Sample Input**
```
https://intouch.mappls.com/iot/api/geofence?id=1190516,190511&ignoreGeometry=true
```
## **Sample ouput**

```json
{
    "data": [
        {
            "id": 1190516,
            "name": "AIIMS",
            "type": "Circle",
            "buffer": 1000.0,
            "creationTime": 1736150681,
            "updatedTime": 1736150681
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




<div align="center">@ Copyright 2025 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

