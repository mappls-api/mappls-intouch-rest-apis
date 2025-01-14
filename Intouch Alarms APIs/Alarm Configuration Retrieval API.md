
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Alarm Configuration Retrieval API

## **Introduction** 

The *Alarm Configuration Retrieval API* allows users to fetch alarm configurations associated with their account. By providing a valid bearer token, users can retrieve a list of alarm configurations based on optional query parameters such as alarm ID, device ID, or alarm type. If no query parameters are provided, the API returns all alarm configurations linked to the account.


## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**

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

| **Parameter**   | **Type** | **Location** | **Description** | **Example** |
| --- | --- | --- |--- | --- |
| `id` | number | Query | This is the alarm's ID, a non-mandatory parameter. If not passed then by default the API will return the list of all alarm configurations in the account. You can pass single value or comma separated alarm IDs for multiple values. | `13400690` |
| `deviceId` | number | Query | This is device ID. API will return data based on the configs set for the passed device IDs. You can pass a single device ID or comma seperated multiple device IDs. | `10619089` |
| `alarmType` | number | Query | This is alarm type. API will return data based on the passed alarm types. You can pass a single alarm type or comma seperated multiple alarm types. | `24` |


## **Response Parameters**

### **`GetAlarmConfig`**
  - **`id`**(number): The unique ID of the alarm.
  - **`deviceId`**(number): Device ID(s) on which the alarm config got created.
  - **`alarmType`**(integer): Type of alarm (e.g., ignition, overspeed, etc.).
  - **`limit`**(integer): Limit value associated with the alarm.
  - **`duration`**(integer): Duration value associated with the alarm.
  - **`type`**(integer): Values depends on the type of alarm configured.
  - **`creationTime`**(number): Timestamp when the alarm was created.
  - **`updationTime`**(integer): Timestamp when the alarm was last updated.
  - **`geofenceId`**(number): If returned alarm type is geofence, then this will return the list of geofences for which alarms were configured. `Example: [1001, 2002]`
  - **`severity`**(integer): Severity of the alarm (0 for normal, 1 for high severity).

## **Sample cURL Request**

```bash
curl --location 'https://intouch.mappls.com/iot/api/alarm?id=13400690&deviceId=10619089&alarmType=24' \
--header 'accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Content-Type: application/json' \
--header 'Cookie: HttpOnly'
```

## **Sample Output**

```json
{
    "data": [
        {
            "id": 13400690,
            "deviceId": [
                10619089
            ],
            "alarmType": 24,
            "creationTime": 1735285180,
            "updationTime": 1735285180,
            "severity": 0
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

