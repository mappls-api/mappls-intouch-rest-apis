
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Alarm Webhook Configuration API

## **Introduction**

This API allows you to trigger alarms based on device status changes such as *`Ignition On`* or *`Ignition Off`*. The alarm is sent to a specified Webhook URL, and the device’s location is included in the payload. The alarm can be triggered for different *`device IDs`* based on the *`event type`* (e.g., ignition change).

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `{token_type} {access_token}.`**

## **Input URL:**

 > https://intouch.mappls.com/iot/api/alarm/

### **Input Method:** 
- POST

## **Request Type** 
- **Content-Type:** *`application/x-www-form-urlencoded`*

## **Body Parameters**


| **Parameter**  | **Type**          | **Required** | **Description** |
| -------------- | ----------------- | ------------ | --------------- |
| `alarmType`    | Integer           | Yes          | The type of alarm to create. Each alarm type has a constant value: Ignition (`21`), Overspeed (`22`), Unplugged (`23`), Panic (`24`), Geofence (`26`), Stoppage (`27`), Idle (`28`), Towing (`29`), GPRS Connectivity (`126`), Vehicle Battery (`129`), Mileage (`133`), GPS Connectivity (`146`), Distance Covered (`151`), Internal Battery Voltage (`161`). |
| `geofenceId`   | Array\[String\]   | No           | Geofence ID(s). Required only for the Geofence alarm (`alarmType = 26`). You can pass a single Geofence ID or multiple Geofence IDs in an array. Example: `["GF1", "GF2"]`. |
| `type`         | Integer           | No           | Specifies additional context for alarms. Required for `alarmType = 21 (Ignition)`, `26 (Geofence)`, `133 (Mileage)`, and `151 (Distance Covered)`. Example: For Geofence alarms, use `InTouchConstants.ALARM_GEOFENCE_ENTRY` (value: `2`). |
| `deviceId`     | Array\[Long\]     | Yes          | Device ID(s). You can pass a single device ID or multiple device IDs in an array. Example: `[1782]` for a single ID or `[1782, 1783, 1784]` for multiple IDs. |
| `duration`     | Integer           | No           | Time duration in seconds. Required only for the following alarms: `Overspeed`, `Stoppage`, `Idle`, `Towing`, `GPRS Connectivity`, `Vehicle Battery`, `GPS Connectivity`, `Distance Covered`, and `Internal Battery Voltage`. Example: `60` for 1 minute. |
| `webhookURL`   | String            | No           | A webhook URL to receive real-time alarm updates. Example: `https://webhook.site/your-custom-url`. |

## **Response Type** 
- *`JSON`*

## **Response Codes**

| **Status Code** | **Description** |
| ---------------- | --------------- |
| `201 - OK`         | Alarm created successfully. |
| `400 - Bad Request` | Invalid parameters in the request body. |
| `401 - Unauthorized` | Missing or invalid Bearer Token. |
| `403 - Forbidden`   | User lacks permission for the requested action. |
| `404 - Not Found`   | Specified device or Geofence not found. |
| `500 - Internal Server Error` | Server encountered an unexpected error. |


## **Sample curl Request**

```bash
curl --location 'https://intouch.mappls.com/iot/api/alarm/' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly' \
--data-urlencode 'alarmType=21' \
--data-urlencode 'deviceId=1782' \
--data-urlencode 'duration=' \
--data-urlencode 'webhookURL=https://webhook.site/<your_webhook_id>' \
--data-urlencode 'geofenceId=' \
--data-urlencode 'type=1'

```
## **Sample Payloads**
### **Ignition Off**

```json
{
  "generationTime": 1724850454,
  "data": {
    "id": 12840191,
    "timestamp": 1724850454,
    "location": {
      "type": "Point",
      "coordinates": [77.1659899, 28.5606633]
    },
    "alertType": 21,
    "configuredLimit": 0,
    "alertData": 0,
    "deviceId": 1782
  },
  "type": "alarm",
  "version": "Release-9.0.0",
  "deviceId": 1782,
  "deviceName": "Simulator Testing",
  "tripId": "null"
}

```
### **Ignition On**

```json
{
  "generationTime": 1724850464,
  "data": {
    "id": 12840191,
    "timestamp": 1724850464,
    "location": {
      "type": "Point",
      "coordinates": [77.1678416, 28.5612066]
    },
    "alertType": 21,
    "configuredLimit": 0,
    "alertData": 1,
    "deviceId": 1782
  },
  "type": "alarm",
  "version": "Release-9.0.0",
  "deviceId": 1782,
  "deviceName": "Simulator Testing",
  "tripId": "null"
}
```
## **Sample Response**

```json
{  
  "id": 12840191
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

