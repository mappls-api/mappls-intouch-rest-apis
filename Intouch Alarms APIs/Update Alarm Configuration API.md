
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Update Alarm Configuration API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Update Alarm Configuration API` allows developers to update an existing alarm configuration. Using a valid bearer token and the ID of the alarm configuration, developers can modify various parameters such as device IDs, geofence IDs, alarm type, severity, and more.
> **Note:** Ensure the alarm exists before attempting an update. Use the [Alarm Configuration Retrieval API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Alarms%20APIs/Alarm%20Configuration%20Retrieval%20API.md) to obtain the corresponding `alarm Id`.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method** 
- POST

## **Input URL**
`https://intouch.mappls.com/iot/api/alarms/{id}`

## **Response Codes**
| **Status Code** | **Description** |
| --- | --- |
| `200` (OK) | Alarm configuration updated successfully. |
| `203` (Non-Authoritative Information) | Alarm does not exist for the given ID.<br>*Example:* `{ "error": "Alarm does not exist in this account" }` |
| `400` (Bad Request) | Invalid request. This may occur due to incorrect ID, missing required parameters, or invalid data types. |
| `401` (Unauthorized) | Authentication failed due to missing or invalid Bearer token. |
| `403` (Forbidden) | Access denied. The user does not have permission to update this alarm. |
| `404` (Not Found) | The specified resource or endpoint could not be found. |

## **Request Parameters**
| **Parameter**   | **Type** | **Location** | **Required** | **Description** |
| --- | --- | --- | --- |--- |
| **`id`** | number | path | Yes | The unique ID of the alarm configuration to be updated. |
| `deviceId` | array[number] | query | No | ID(s) of the device(s) for which the alarm config has to be updated. Multiple IDs can be passed separated by comma. |
| `groupId` | array[number] | query | No | Optional group IDs to filter which devices the alarm configuration applies to. |
| `type` | number | query | No | Specifies subtype based on the alarm type: `26` = Geofence, `21` = Ignition, `133` = Mileage, `151` = Distance Covered. |
| `duration` | number | query | No | Required for certain alarm types like overspeed, stoppage, idle, towing, GPRS connectivity, vehicle battery, GPS connectivity, etc. |
| `limit` | number | query | No | Required for alarm types such as overspeed, vehicle battery, mileage, distance covered, or internal battery alarms. |
| `geofenceId` | array[number] | query | No | Required when alarmType is 26 (Geofence). Multiple IDs can be passed separated by comma. |
| `severity` | number | query | No | Defines severity of alarm: `0` = Normal, `1` = High. |
| `webhookURL` | string | query | No | Webhook URL to notify when the alarm triggers. Example: `"https://example.com/webhook"` |


## **Response Parameters**
The response of this API would be empty in case of success. A successful update is denoted by `200 OK`. In case of an error (for example, `400 Bad Request`), the response body will contain details describing the issue.

## **Sample cURL Request**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/alarms/14887320?deviceId=14414276&duration=100&geofenceId=438138' \
--header 'Content-Type: application/json' \
--header 'Accept: text/plain' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
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

