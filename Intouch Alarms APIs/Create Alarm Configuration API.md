
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Create Alarm Configuration API
 
> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction** 

The `Create Alarm Configuration API` enables developers to create alarm configurations for one or multiple devices using the specified input parameters. It supports multiple alarm types and customizable conditions to facilitate effective device and vehicle monitoring.

Supported alarm types include `Geofence, IGNITION, OVERSPEED, Unplugged, Panic, Stoppage, Idle, Towing, GPRS Connectivity, Vehicle Battery, Mileage, GPS Connectivity, Distance Covered, and INTERNAL BATTERY VOLTAGEe`.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**


- **Content-Type: `application/json`**

## **Input Method:** 
- POST

## **Input URL**

> https://intouch.mappls.com/iot/api/alarms

## **Response Type**
- JSON

## **Response Codes**

| **Status Code** | **Description** |
| --- | --- |
| `201(OK)` | Alarm created successfully. |
| `203(Device Not Found)` | The specified device(s) could not be located. |
| `400(Bad Request)` | Invalid ID supplied or invalid data type. |
| `401(Unauthorized)` | Invalid token or Access to the API is forbidden. |
| `404(Not Found)` | Specified device or URL Not Found. |

## **Request Parameters**
The **`Bold`** Ones are Mandatory, *`Italic`* ones are optional parameters.
- **`alarmType`**(integer): Type of alarm to create. Below are the alarm types and their corresponding IDs:
  - `21`: IGNITION
  - `22`: OVERSPEED
  - `23`: UNPLUGGED
  - `24`: PANIC
  - `26`: GEOFENCE
  - `27`: STOPPAGE
  - `28`: IDLE
  - `29`: TOWING
  - `126`: GPRS CONNECTIVITY
  - `129`: MILEAGE
  - `133`: VEHICLE BATTERY
  - `146`: GPS CONNECTIVITY
  - `151`: DISTANCE COVERED
  - `161`: INTERNAL BATTERY VOLTAGE 
- *`deviceId`*(Array[long]): Device IDs of those devices for which the alarm configuration is done.
- *`groupId`*(Array[long]): Group ID(s) of device groups associated with the developer. The alarm configuration will apply to all devices within the specified groups.
- *`type`*(integer): Specifies the type of alarm configuration. The values depend on the alarmType: 
    - For `Geofence(alarmType = 26)`:  
      - `2` : Entry  
      - `3` : Exit  
      - `1` : Entry & Exit  
      - `4` : Long stay in geofence  
    - For `IGNITION(alarmType = 21)`:  
      - `1` : Both ON & OFF  
      - `2` : IGNITION On  
      - `3` : IGNITION Off  
      - `5` : Day's First IGNITION ON  
    - For `Mileage(alarmType = 133)`:  
      - `0` : Daily  
      - `1` : Monthly  
    - For `Distance Covered(alarmType = 151)`:  
      - `1` : At Least  
      - `2` : At Most  
- *`duration`*(integer): Only required in case of OVERSPEED, stoppage, idle, towing, GPRS connectivity, vehicle battery, GPS connectivity, distance covered, internal battery alarm.
- *`limit`*(integer): Only required in case of OVERSPEED, vehicle battery, mileage, distance covered, internal battery alarm. 
- *`geofenceId`*(array): Only required when `alarmType` is `26` (Geofence). Accepts single or multiple geofence IDs separated by commas. `Example: [23434, 45454]`
- *`severity`*(integer): This basically defines the severity of the alarm. Use `0` for normal severity and `1` for high severity.
- *`webhookURL`*(string): URL where real-time alarm notifications will be sent when the alarm is triggered.

## **Response Parameter** 
| **Field** | **Type** | **Description** | **Example** |
| --- | --- | --- | --- |
| `id` | number | Unique Id of the created alarm configuration. This ID can be used for future operations such as updating or deleting the alarm. | `14847139` |

## **Sample cURL Request**
```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/alarms?deviceId=14414276&groupId=1413&alarmType=26&type=1&duration=120&geofenceId=438138%2C438132&severity=0' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response**

```json
{
    "id": 14847139
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


