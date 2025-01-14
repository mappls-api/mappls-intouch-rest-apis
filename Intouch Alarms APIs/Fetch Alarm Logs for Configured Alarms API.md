
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch Alarm Logs for Configured Alarms API

## **Introduction**

The *`Fetch Alarm Logs for Configured Alarms API`* enables users to retrieve alarm logs for configured alarms within a specified time range. By providing a valid start time and end time, along with optional parameters such as device ID and alarm type, this API allows users to filter and fetch detailed alarm log information. *The API returns a list of alarm configurations, and the logs contain key details about each alarm event, such as the alarm type, device ID, location, severity, and actual data received.* This facilitates efficient monitoring, troubleshooting, and management of devices and alarm configurations.


## **Security Type**

This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
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
     - **`deviceId`**(number): The ID of the device that generated the alarm. (Will come only in case of /alarmLog GET API response). `Example: 8989`
     
     - **`timestamp`**(number): Time at which the alert got generated. `Example: 1577589789`
     
     - **`latitude`**(number): The latitude of the alarm location. `Example: 28.550962381896`
     
     - **`longitude`**(number): The longitude of the alarm location. `Example: 77.26890675033`
     
     - **`address`**(string): Location address at which the alarm got generated. `Example: "237, Okhla Industrial Estate Phase 3, New Delhi"`
     
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
     
     - **`actualLimit`**(integer): The actual data received from the device at that particular moment when the alarm got generated. `Example: 57`
     
     - **`actualDuration`**(integer): The actual duration for which the device breached the alarm limits. `Example: 25 seconds`
     
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
     
     - **`geofenceId`**(number): This is the ID of the geofence for which the alarm got generated. This will come only when the 'type' field return 26 i,e geofence. `Example: 987876`


## **Sample Input**

```
https://intouch.mappls.com/iot/api/alarm/alarmLog/?deviceId=8989&alarmType=28&startTime=1577589789&endTime=1577589988
```

## **Sample Output**

```json
{
  "data": [
    {
      "deviceId": 8989,
      "timestamp": 1577589789,
      "latitude": 28.550962381896,
      "longitude": 77.26890675033,
      "address": "237, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 19 m from Wipro BPO Corporate Office pin-110020",
      "alarmType": 28,
      "limit": 44,
      "duration": 20,
      "actualLimit": 57,
      "actualDuration": 25,
      "severity": 1,
      "data": 1,
      "geofenceId": 987876
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

