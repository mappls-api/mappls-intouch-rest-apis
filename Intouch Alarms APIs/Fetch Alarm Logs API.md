
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch Alarm Logs API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Fetch Alarm Logs for Configured Alarms API` enables users to retrieve alarm logs for configured alarms within a specified time range. By providing a valid start time and end time, along with optional parameters such as device ID and alarm type, this API allows users to filter and fetch detailed alarm log information. The API returns a list of alarm configurations, and the logs contain key details about each alarm event, such as the alarm type, device ID, location, severity, and actual data received. This facilitates efficient monitoring, troubleshooting, and management of devices and alarm configurations.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**

> https://intouch.mappls.com/iot/api/alarms/alarmLogs/

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**

- `200(OK)`: Successful operation. Alarm logs retrieved successfully.
- `203(Device Not Found)`: The specified device ID(s) were not found in the system.
- `400(Bad Request)`: Invalid parameters or an incorrect data type was passed (e.g., string instead of integer).
  - **Example:**
    ```json
    {
      "error": "futuredateselected"
    }
    ```
- `401(Unauthorized)`: The request is forbidden due to lack of authentication or authorization.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**

Parameters marked in **`bold`** are mandatory, and those in *`italics`* are optional:

- **`startTime`**(long, query): The start timestamp (in seconds) for the alarm log search. This is a required field.
- **`endTime`**(long, query): The end timestamp (in seconds) for the alarm log search. This is a required field.
- *`deviceId`*(Array[long], query): The ID(s) of the device(s) for which the alarm log is need to be fetched. You can pass single device ID or multiple device IDs separated by commas.
- *`projection`*(Array[long], header): Specifies the response fields to be included in the API output.
- *`alarmType`*(Array[long], query): This is the type of alarm for which the alarm log need to be fetched. single or Multiple alarm types can be separated by commas. Alarm types and their corresponding IDs are as follows:
    | **General Alarms Types**| **Video Telematics Alarms Types**|
    | :--- | :--- |
    | `IGNITION (21)`| `(DMS) No Driver Alert (391)` |
    | `OVERSPEED (22)`| `(DMS) Phone Detection Alert (392)` |
    | `UNPLUGGED (23)`| `(DMS) Smoking Detection Alert (393)` |
    | `PANIC (24)`| `(DMS) Driver Distraction Alert (394)` |
    | `AC (25)`| `(ADAS) Lane Departure Alert (395)` |
    | `GEOFENCE (26)`| `(ADAS) Forward Collision Warning Alert (396)` |
    | `STOPPAGE (27)`| `(ADAS) Following Distance Monitoring Alert (400)` |
    | `IDLE (28)`| `(ADAS) Pedestrian Collision Warning Alert (401)` |
    | `TOWING (29)`| `(DMS) Yawning Detection Alert (402)` |
    | `GPRS CONNECTIVITY (126)`| `(DMS) Seat Belt Detection Alert (404)` |
    | `VEHICLE BATTERY (129)`| `(DMS) Driver Fatigue (409)` |
    | `MILEAGE (133)`| `(MDVR) Camera Covering Alert (1102)` |
    | `GPS CONNECTIVITY (146)`| |
    | `DISTANCE COVERED (151)`| |
    | `INTERNAL BATTERY VOLTAGEE (161)`| |

## **Response Parameters**
- **`data`**
     - **`deviceId`**(number): The ID of the device that generated the alarm. (Will come only in case of /alarmLog GET API response). 
     - **`timestamp`**(number): Time at which the alert got generated.    
     - **`latitude`**(number): The latitude of the alarm location.    
     - **`longitude`**(number): The longitude of the alarm location.
     - **`address`**(string): Location address at which the alarm got generated.
     - **`alarmType`**(integer): The type of alarm triggered (e.g., 28 for IDLE). 
     - **`limit`**(integer): Alarm limit as set in the config. For example, if an OVERSPEED alarm set on limit of 44 km/hr in the alarm config setting, then this attribute will return 44 km/hr     
     - **`duration`**(integer): Alarm duration limit as set in the alarm config section. For example, if duration of OVERSPEED alarm is set as 20 secs, then the alarm will generate when the vehicle OVERSPEEDs for a duration of 20 secs.     
     - **`actualLimit`**(integer): The actual data received from the device at that particular moment when the alarm got generated.
     - **`actualDuration`**(integer): The actual duration for which the device breached the alarm limits.
     - **`severity`**(integer): The severity of the alarm.
          - `0` : Low Severity
          - `1` : High Severity     
     - **`data`**(integer): The state of the alarm.
          - `IGNITION(type = 21)`
             - 0: OFF
             - 1: ON
          - `AC(type=25)`
          - `0` : OFF
          - `1` : ON
          - `GEOFENCE(type=26)`
            - `1` : Entry & Exit Geofence
            - `2` : Entry Geofence
            - `3` : Leaving Geofence
            - `4` : Long Stay In Geofence     
     - **`geofenceId`**(number): This is the ID of the geofence for which the alarm got generated. This will come only when the 'type' field return 26 i,e geofence.
     - **`eventFileName`**(string): Evidence File Names (comma separated). Files can be downloaded from the https://iotstreaming.mappls.com/videos `<fileName>`


## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/alarms/alarmlogs?deviceId=10757178&startTime=1752211271&endTime=1752230839' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{
  "data": [
    {
      "deviceId": 10757178,
      "timestamp": 1752230678,
      "latitude": 13.000255,
      "longitude": 79.991168,
      "address": "Bangalore High Road, Irungattukottai, Sriperumbudur, Kancheepuram District, Tamil Nadu. 190 m from Bharat Petroleum Petrol Pump, Pin-602105 (India)",
      "alarmType": 1102,
      "limit": 0,
      "actualLimit": 0,
      "data": 0,
      "severity": 0,
      "eventFileName": "2025/07/11/02_64_6507_00_06051157000000010207250711161438_1.mp4,2025/07/11/02_02_6507_01_06051157000000010207250711161438_2.mp4,2025/07/11/02_65_6507_02_06051157000000010207250711161438_3.mp4,2025/07/11/02_04_6507_03_06051157000000010207250711161438_4.mp4"
    },
    {
      "deviceId": 10757178,
      "timestamp": 1752227866,
      "latitude": 13.06198,
      "longitude": 80.048283,
      "address": "Tiruvallur High Road, Thirumazhisai, Chennai, Tamil Nadu. 99 m from NMZ Enterprises, Pin-600124 (India)",
      "alarmType": 1102,
      "limit": 0,
      "actualLimit": 0,
      "data": 0,
      "severity": 0,
      "eventFileName": "2025/07/11/02_02_6507_01_06051157000000000207250711152746_2.mp4,2025/07/11/02_65_6507_02_06051157000000000207250711152746_3.mp4,2025/07/11/02_64_6507_00_06051157000000000207250711152746_1.mp4,2025/07/11/02_04_6507_03_06051157000000000207250711152746_4.mp4"
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

