
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Alarm Configuration Retrieval API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction** 
The `Alarm Configuration Retrieval API` enables users to view alarm configurations linked to their account. By passing a valid bearer token, users can fetch alarm details using optional filters such as alarmId, deviceId, or alarmType. This helps in identifying particular alarm setups for individual devices or specific alarm categories. If no filters are applied, the API returns the complete list of alarm configurations associated with the account.

> **Note:** To obtain valid deviceId or groupId values, use the respective [Device](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/InTouch%20Fleet%20Management%20APIs/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md) and [Group](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/InTouch%20Fleet%20Management%20APIs/Intouch%20Entities%20Group%20APIs/Fetch%20Entities%20Group%20API.md) retrieval APIs.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method:** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/alarm

## **Response Type**
- JSON

## **Response Codes**

| **Status Code** | **Description** |
| --- | --- |
| `200(OK)` | Successful operation. |
| `203(Device Not Found)` | The specified device(s) could not be located. |
| `400(Bad Request)` | Invalid ID supplied or invalid data type. |
| `401(Unauthorized Request)` | Access to API is forbidden. |
| `404(Not Found)` | Specified device or URL Not Found. |

## **Request Parameters**
All the below parameters are `optional`.
| **Parameter**   | **Type** | **Location** | **Description** | **Example** |
| --- | --- | --- |--- | --- |
| *`id`* | Array[long] | Query | Alarm ID(s). If not provided, the API returns all alarm configurations associated with the account. Accepts a single value or multiple comma-separated alarm IDs. | `14849029` |
| *`deviceId`* | Array[long] | Query | Device ID(s) for which alarm configurations are to be retrieved. Accepts a single device ID or multiple comma-separated device IDs. | `14414276` |
| *`groupId`* | Array[long] | Query | Group ID(s) associated with the user. Returns alarm configurations applicable to all devices within the specified group(s). | `1413` |
| *`alarmType`* | Array[long] | Query | Alarm type ID(s). Returns alarm configurations based on the specified alarm type(s). Accepts a single value or multiple comma-separated values. | `26` |


## **Response Parameters**

### **`data`**
  - **`id`**(number): The unique ID of the alarm.
  - **`deviceId`**(number): Device ID(s) on which the alarm config got created.
  - **`alarmType`**(integer): Type of alarm (e.g., IGNITION, OVERSPEED, etc.).
  - **`limit`**(integer): Limit value associated with the alarm.
  - **`duration`**(integer): Duration value associated with the alarm.
  - **`alarmType`**(integer): Values depends on the type of alarm configured.
  - **`creationTime`**(number): Timestamp when the alarm was created.
  - **`updationTime`**(integer): Timestamp when the alarm was last updated.
  - **`geofenceId`**(number): If returned alarm type is geofence, then this will return the list of geofences for which alarms were configured. `Example: [1001, 2002]`
  - **`severity`**(integer): Severity of the alarm (0 for normal, 1 for high severity).

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/alarms?id=14849029&deviceId=14414276&groupId=1413&alarmType=26' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response**
```json
{
    "data": [
        {
            "id": 14849029,
            "deviceId": [
                14414276
            ],
            "alarmType": 26,
            "type": 1,
            "creationTime": 1771393896,
            "updationTime": 1771393896,
            "severity": 0,
            "geofenceId": [
                438138,
                438132
            ]
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

