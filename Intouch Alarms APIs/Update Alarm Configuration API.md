
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
- **Content-Type: `application/form-data`**

## **Input Method:** 
- POST

## **Input URL**
`https://intouch.mappls.com/iot/api/alarm/{id}`

## **Response Type**
- JSON

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
| **Parameter**   | **Type** | **Location** | **Required** | **Description** | **Example** |
| --- | --- | --- | --- |--- | --- |
| `id` | number | query | Yes | The unique ID of the alarm configuration to be updated. | `14814369` |

## **Request Body Parameters**
- **`deviceId`**(number): ID of the device for which the alarm config has to be updated. If there are multiple devices then you can pass them separated by comma.
- **`type`**(integer): Specifies the type based on the alarm type.  
    - **For `Geofence (alarmType = 26)`**  
        - `2` : Entry
        - `3` : Exit
        - `1` : Entry & Exit
        - `4` : Long stay in geofence  
    - **For `IGNITION (alarmType = 21)`**  
        - `1` : Both ON & OFF
        - `2` : ignition On
        - `3` : ignition Off
        - `5` : Day's First ignition ON  
    - **For `Mileage (alarmType = 133)`**  
        - `0` : Daily
        - `1` : Monthly  
    - **For `Distance Covered (alarmType = 151)`**
        - `1` : At Least
        - `2` : At Most
- **`duration`**(integer): Only required for certain alarm types like overspeed, stoppage, idle, towing, GPRS connectivity, vehicle battery, GPS connectivity, etc.
- **`limit`**(integer): Only required for alarm types such as overspeed, vehicle battery, mileage, distance covered, and internal battery alarm.
- **`geofenceId`**(number): Only Required when alarmType is 26 (Geofence). Pass a single or multiple geofence IDs separated by comma.
- **`severity`**(integer): This basically defines the severity of the alarm.  
    - `0` : Normal severity  
    - `1` : High severity
- **`alarmType`**(integer): Specifies the type of alarm being updated.
- **`alarmTimeType`**(integer): Specifies the timing type of the alarm.


## **Response Parameters**
The response of this API would be empty in case of success. A successful update is denoted by `200 OK`. In case of an error (for example, `400 Bad Request`), the response body will contain details describing the issue.

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/alarm/14814369' \
--header 'accept: */*' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly; HttpOnly' \
--form 'entityIds="10647019,12779360"' \
--form 'geofenceIds="1192256"' \
--form 'alarmType="26"' \
--form 'severity="0"' \
--form 'type="1"' \
--form 'alarmTimeType="0"'
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

