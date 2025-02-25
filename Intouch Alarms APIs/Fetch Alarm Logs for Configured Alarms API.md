
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch Alarm Logs for Configured Alarms API

## **Introduction**

The *`Fetch Alarm Logs for Configured Alarms API`* enables users to retrieve alarm logs for configured alarms within a specified time range. By providing a valid start time and end time, along with optional parameters such as device ID and alarm type, this API allows users to filter and fetch detailed alarm log information. *The API returns a list of alarm configurations, and the logs contain key details about each alarm event, such as the alarm type, device ID, location, severity, and actual data received.* This facilitates efficient monitoring, troubleshooting, and management of devices and alarm configurations.


## **Security Type**

This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**

> https://intouch.mappls.com/iot/api/alarm/alarmLog/

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- `200(OK)`: Successful operation. Alarm logs retrieved successfully.
- `203(Device Not Found)`: The specified device ID(s) were not found in the system.
- `400(Bad Request)`: Invalid parameters or an incorrect data type was passed (e.g., string instead of integer).

```json
{
  "error": "futuredateselected"
}
```
- `401(Unauthorized)`: The request is forbidden due to lack of authentication or authorization.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**

The **`“bold”`** one’s are mandatory, and the *`“italic”`* one’s are optional.

- **`endTime`**(number): The end timestamp (in seconds) for the alarm log search. This is a required field.

- **`startTime`**(number): The start timestamp (in seconds) for the alarm log search. This is a required field.

- *`deviceId`*(number): The ID(s) of the device(s) for which the alarm log is need to be fetched. You can pass single device ID or multiple device IDs separated by commas.

- *`alarmType`*(integer): This is the type of alarm for which the alarm log need to be fetched. single or Multiple alarm types can be separated by commas. Alarm types and their corresponding IDs are as follows:
    - `IGNITION`: 21
    - `OVERSPEED`: 22
    - `UNPLUGGED`: 23
    - `PANIC`: 24
    - `GEOFENCE`: 26
    - `STOPPAGE`: 27
    - `IDLE`: 28
    - `TOWING`:	29
    - `GPRS CONNECTIVITY`: 126
    - `VEHICLE BATTERY`: 129
    - `MILEAGE`: 133
    - `GPS CONNECTIVITY`: 146
    - `DISTANCE COVERED`: 151
    - `INTERNAL BATTERY VOLTAGE`: 161

## **Response Parameters**

- **`AlertObject`**
     - **`deviceId`**(number): The ID of the device that generated the alarm. (Will come only in case of /alarmLog GET API response).
     
     - **`timestamp`**(number): Time at which the alert got generated.
     
     - **`latitude`**(number): The latitude of the alarm location. 
     
     - **`longitude`**(number): The longitude of the alarm location.
     
     - **`address`**(string): Location address at which the alarm got generated.
     
     - **`alarmType`**(integer): The type of alarm triggered (e.g., 28 for IDLE). Following are the alarm types & their corresponding IDs:
          - `IGNITION`: 21
          - `OVERSPEED`: 22
          - `UNPLUGGED`: 23
          - `PANIC`: 24
          - `GEOFENCE`: 26
          - `STOPPAGE`: 27
          - `IDLE`: 28
          - `TOWING`:	29
          - `GPRS CONNECTIVITY`: 126
          - `VEHICLE BATTERY`: 129
          - `MILEAGE`: 133
          - `GPS CONNECTIVITY`: 146
          - `DISTANCE COVERED`: 151
          - `INTERNAL BATTERY VOLTAGE`: 161
          
     - **`limit`**(integer): Alarm limit as set in the config. For example, if an overspeed alarm set on limit of 44 km/hr in the alarm config setting, then this attribute will return 44 km/hr
     
     - **`duration`**(integer): Alarm duration limit as set in the alarm config section. For example, if duration of overspeed alarm is set as 20 secs, then the alarm will generate when the vehicle overspeeds for a duration of 20 secs.
     
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


## **Sample Input**

```
https://intouch.mappls.com/iot/api/alarm/alarmLog/?deviceId=10647019&alarmType=26&startTime=1737687960&endTime=1737690120
```

## **Sample Output**

```json
{
    "data": [
        {
            "deviceId": 10647019,
            "timestamp": 1737689727,
            "latitude": 28.5435685,
            "longitude": 77.2646272,
            "address": "105, Shri Maa Anandmai Marg, Ami Chand Khand, Giri Nagar, Kalkaji, New Delhi, Delhi. 26 m from Metro Pillar No 167, Pin-110019 (India)",
            "alarmType": 26,
            "limit": 0,
            "data": 2,
            "geofenceId": 1192140,
            "severity": 0
        },
        {
            "deviceId": 10647019,
            "timestamp": 1737689743,
            "latitude": 28.5459278,
            "longitude": 77.2638532,
            "address": "Shri Maa Anandmai Marg, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 21 m from Metro Pillar No 162, Pin-110020 (India)",
            "alarmType": 26,
            "limit": 0,
            "data": 3,
            "geofenceId": 1192140,
            "severity": 0
        },
        {
            "deviceId": 10647019,
            "timestamp": 1737689858,
            "latitude": 28.5454886,
            "longitude": 77.264084,
            "address": "Shri Maa Anandmai Marg, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 23 m from Metro Pillar No 163, Pin-110020 (India)",
            "alarmType": 26,
            "limit": 0,
            "data": 2,
            "geofenceId": 1192140,
            "severity": 0
        },
        {
            "deviceId": 10647019,
            "timestamp": 1737689973,
            "latitude": 28.5458946,
            "longitude": 77.2690323,
            "address": "12C, Okhla Phase 3 Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 67 m from Mother Dairy, Pin-110020 (India)",
            "alarmType": 26,
            "limit": 0,
            "data": 3,
            "geofenceId": 1192140,
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

