
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Device Historical Events API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
This API enables `retrieval of comprehensive historical location data for a vehicle` over a specified time range, along with associated telemetry attributes that provide deeper operational context. In addition to core positional information such as latitude, longitude, and timestamp, the response may include parameters like `speed`, `heading`, `altitude`, `ignition status`, and other `sensor-derived metrics` captured during the selected interval. The structured time-series dataset supports advanced analytical and reporting workflows, allowing consumers to generate customized insights tailored to various business needs. For example, the data can be used to reconstruct and visualize past routes on an interactive map, analyze travel patterns, detect route deviations, evaluate stop durations, or produce graphical representations of altitude changes over time. This capability makes the API suitable for fleet monitoring, compliance verification, performance analysis, and detailed historical reporting use cases.

### **Device Identification Requirements**
- Certain APIs require a deviceId to be passed as part of the path parameters or query parameters.
- If the deviceId is not already available, developers can retrieve a list of registered devices by invoking the [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md).
- The device details obtained from the Retrieve Basic Information of Device API can then be used to make subsequent API calls that depend on device-specific identifiers.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices/{deviceId}/events

## **Response Type**
- JSON

## **Response Messages (as HTTP response messages)**

1. `200` (Success): Historical location events retrieved successfully.
2. `203` (Device Not Found): The specified deviceId was not found (e.g., `{"error": "Device not allowed"}`).
3. `400` (Bad Request): Invalid time range, or incorrect parameter format (e.g., `{"error": "future date selected"}`).
4. `401` (Unauthorized): Missing or invalid authentication credentials.
5. `404` (Not Found): The requested URL was not found.
6. `500` (Internal Server Error): An unexpected server error occurred.


## **Request Parameters**
The **`“bold”`** one's are mandatory, and the *`“italic”`* one's are optional.
1. **`deviceId`** (long): ID of the device for which the location data needs to be fetched.
2. **`startTime`** (long): Start Epoch timestamp in seconds from which the events need to be fetched.
3. **`endTime`** (long): End Epoch timestamp in seconds till which the events need to be fetched.
4. *`fields`* (string): A comma-separated list of telemetry attributes to include in the response (e.g., positionList, mobileInfo, alerts). If not specified, the default fields are returned.
5. *`skipPeriod`* (integer): Defined in minutes. For example, if 2 is passed then the returned data packet will have a minimum difference of 2 mins else 0.
6. *`filterEvent`* (boolean): If set to `true`, it removes mock (fake) location data such as beacon-based locations. Default value is `false`.
7. *`filterDistance`* (integer): Removes location records where the distance between two points is less than the specified value (in meters).

## **Response Parameters** 

- **`drivingBehaviourCount parameters`**: Driving behavior count in the selected device.
    - *`haCount`*(integer): Count of harsh acceleration events. `Example: 2`
    - *`hbCount`*(integer): Count of harsh braking events. `Example: 1`
    - *`hcCount`*(integer): Count of harsh cornering events. `Example: 3`
- **`summary parameters:`**
    - *`distance`*(number): Total drive distance in kilometers. `Example: 23.67`
    - *`duration`*(number): Total drive duration in seconds. `Example: 300`
    - *`avgSpeed`*(number): Average speed in km/h. `Example: 45.54`
    - *`startAddress`*(string): Start Epoch time of the event. i.e. the time at which the data first came from the device for the selected day. `Example: 213, 1st Cross Road, HAL Stage 2, Indiranagar, Bengaluru, Karnataka.`
    - *`endAddress`*(string): End Epoch time of the event. i.e. the time at which the last data came from the device for the selected day. `Example: 3645, 13th F Main Road, Indiranagar, Bengaluru, Karnataka.`
    - *`startTimestamp`*(number): Start time of the device i.e. the time at which the data first came from the device for the selected day. `Example: 1577644204`
    - *`endTimestamp`*(number): End time of the device i.e. the time at which the last data came from the device for the selected day. `Example: 1577684913`
- **`positionList parameters:`**
    - *`address`*(string): Address of the location event.
    - *`timestamp`*(number): Epoch timestamp of the event.
    - *`longitude`*(number): Longitude.
    - *`latitude`*(number): Latitude.
    - *`heading`*(number): Device heading direction in degrees from North.
    - *`speed`*(number): Device speed at the particular location.
    - *`ignition`*(number): Whether vehicle ignition is On or Off. 0 means ignition is OFF and 1 means ignition is ON.
    - *`powerSupplyVoltage`*(number): Battery voltage value in millivolts.
    - *`gpsFix`*(boolean): GPS is fix or not for the device. `true` means GPS is fixed and `false` means GPS is not fixed.
    - *`validGPS`*(boolean): Checks whether GPS is valid or not.
    - *`accOff`*(boolean): Checks for whether adaptive cruise control is enabled or not.
    - *`movementStatus`*(integer): Indicates the real-time movement state of the vehicle.
        - `1` : Moving
        - `2` : Idle
        - `3` : Stopped
        - `4` : Towing
        - `5` : No Data
        - `6` : Power Off
        - `7` : No Gps
        - `8` : On Trip
        - `9` : Free Vehicle 
    - *`durationTime`*(number): Time spent at the current location in seconds.
    - *`greenDriveType`*(string): Driving behavior type.
        - `HA` : Harsh acceleration
        - `HB` : Harsh Breaking
        - `HC` : Harsh Cornering
    - *`tripStatus`*(integer): Trip status.
        - `0` : On Trip
        - `1` : Free Vehicle.
- **`mobileInfo parameters:`**
    - *`locationSource`*(number): Returns the source of the location.
        - `1` : GPS connected, accuracy < 50 meters.
        - `2` : GPRS connected, accuracy > 50 meters.
    - *`mockLocation`*(integer): Indicates if the location being sent is real or a mock location.
        - `0` : Real location being sent by the developer.
        - `1` : Mock location being sent by the developer.
    - *`isAirplanemode`*(boolean): Checks whether the mobile's airplane mode is ON or OFF.
        - `true` : Airplane mode is ON.
        - `false` : Airplane mode is OFF.
    - *`callStatus`*(number): Current call status like:
        - `0` : CALL_STATE_IDLE
        - `1` : CALL_STATE_RINGING
        - `2` : CALL_STATE_ONCALL          
    - *`deviceStatus`*(integer): Indicates the detected movement/activity state of the beacon device at the current location.
        - `0` : IN_VEHICLE
        - `1` : ON_BICYCLE
        - `2` : ON_FOOT
        - `3` : STILL
        - `4` : UNKNOWN
        - `5` : TILTING
        - `6` : WALKING
        - `7` : RUNNING           
    - *`phoneEvent`*(integer): Checks the location permission that the developer enables/disables in the mobile phone.
        - `5` for location permission denied
        - `6` for location provider off etc
- **`alerts parameters:`**
    - *`deviceId`*(number): ID of the device associated with the alert..Will come only in case of /alarmLog GET API response.
    - *`timestamp`*(number): Time at which the alert was generated.
    - *`latitude`*(number): Latitude of the location where the alert was generated.   
    - *`longitude`*(number): Longitude of the location where the alert was generated.
    - *`address`*(string): Address of the location where the alert was generated.
    - *`alarmType`*(integer): Type of alarm to create. Following are the alarm types & their corresponding IDs.
        - `21` : IGNITION
        - `22` : OVERSPEED
        - `23` : UNPLUGGED
        - `24` : PANIC
        - `25` : AC
        - `26` : GEOFENCE
        - `27` : STOPPAGE
        - `28` : IDLE
        - `29` : TOWING
        - `126` : GPRS CONNECTIVITY
        - `129` : VEHICLE BATTERY
        - `133` : MILEAGE
        - `146` : GPS CONNECTIVITY
        - `151` : DISTANCE COVERED
        - `161` : INTERNAL BATTERY VOLTAGEE 
    - *`limit`*(integer): Alarm limit as set in the config. For example, if an overspeed alarm set on limit of 44 km/hr in the alarm config setting, then this attribute will return 44 km/hr
    - *`duration`*(integer): Alarm duration limit as set in the alarm config section. For example, if duration of overspeed alarm is set as 20 secs, then the alarm will generate when the vehicle overspeeds for a duration of 20 secs.
    - *`actualLimit`*(integer): The actual data received from the device at that particular moment when the alarm got generated.
    - *`actualDuration`*(integer): Actual duration for which the device breached the alarm config limit.
    - *`severity`*(integer): Indicates the severity level of the alarm.
        - `0` : Low Severity.
        - `1` : High Severity.   
    - *`data`*(integer): Describes the state of the alarm.
        - `For IGNITION (Type = 21)`
          - `0` : OFF
          - `1` : ON
        - `For AC (Type = 25)`
          - `0` : OFF
          - `1` : ON
        - `For GEOFENCE (Type = 26)`
          - `1` : Entry & Exit Geofence.
          - `2` : Entry Geofence.
          - `3` : Leaving Geofence.
          - `4` : Long Stay In Geofence.
    - *`geofenceId`*(number):ID of the geofence for which the alarm was generated. This field is returned only when the `alarmType` is `26` (GEOFENCE).

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/devices/1346049/events?startTime=1773223151&endTime=1773227255&filterEvent=false&filterDistance=50' \
--header 'Accept: application/json' \
--header 'Authorization: bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response**
```json
{
    "data": {
        "deviceId": 1346049,
        "summary": {
            "distance": 0.08,
            "duration": 1341,
            "avgSpeed": 9.223372036854776E16,
            "startAddress": "Vishanu Kunj, Gopalpur, Motihari, Bihar. 14 m from Mathematics Study Centre pin-845401 (India)",
            "endAddress": "Shayam Shekhar Kirani Sector, SH 54, Gopalpur Chowk, Gopalpur, Motihari, Bihar. 18 m from Govinda Auto Spare, Pin-845401 (India)",
            "startTimestamp": 1773225914,
            "endTimestamp": 1773227255
        },
        "positionList": [
            {
                "address": "Vishanu Kunj, Gopalpur, Motihari, Bihar. 14 m from Mathematics Study Centre pin-845401 (India)",
                "timestamp": 1773225914,
                "longitude": 84.90414,
                "latitude": 26.6411583,
                "heading": 0.0,
                "speed": 0.0,
                "ignition": false,
                "gpsFix": false,
                "validGPS": true,
                "accOff": false,
                "movementStatus": "stopped",
                "mobileInfo": {
                    "locationSource": 1,
                    "mockLocation": 0,
                    "isAirplanemode": false,
                    "callStatus": 0,
                    "deviceStatus": 3
                },
                "accuracy": 2
            },
            {
                "address": "Vishnu Kunj, SH 54, Raza Bazar, Gopalpur, Motihari, Bihar. 13 m from Nikhar Boutique Rulers, Pin-845401 (India)",
                "timestamp": 1773227135,
                "longitude": 84.9040717,
                "latitude": 26.64106,
                "heading": 0.0,
                "speed": 0.0,
                "ignition": false,
                "gpsFix": false,
                "validGPS": true,
                "accOff": false,
                "movementStatus": "stopped",
                "mobileInfo": {
                    "locationSource": 1,
                    "mockLocation": 0,
                    "isAirplanemode": false,
                    "callStatus": 0,
                    "deviceStatus": 4
                },
                "accuracy": 2
            }
        ],
        "drivingBehaviourCount": {
            "haCount": 0,
            "hbCount": 0,
            "hcCount": 0
        }
    }
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

