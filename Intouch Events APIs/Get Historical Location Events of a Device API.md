
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Get Historical Location Events of a Device API

## **Introduction**

This API is used to *`get the historical location information as well as related additional information for a vehicle`*. This API can be used to create customized reports for users of your apps for different use cases, e.g.: plot the vehicle's past movements on map or get a historical graph of change in a vehicle's altitude.

## **Security Type**

This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL:**

 > https://intouch.mappls.com/iot/api/device/{deviceId}/events

## **Response Type**
- JSON

## **Response Code**

### **Success:**

1.  `200(success)`: To denote a successful API call.

### **Client-side issues:**

1.  `400(Bad Request)`: User made an error while creating a valid request.
2.  `401(Unauthorized)`: the Developer’s key is not allowed to send a request with restricted parameters.
3.  `403(Forbidden)`: the Developer’s key has hit its daily/hourly limit.

### **Server-Side Issues:**

1.  `500(Internal Server Error)`: the request caused an error in our systems.
2.  `503(Service Unavailable)`: during our maintenance break or server downtimes.

### **Response Messages (as HTTP response message)**

1. `200`: Success
2. `203`: Device Not Found
3. `400`: Bad Request - Invalid device ID supplied or invalid data type. For example, the input attribute "id" is an integer but string value gets passed.
```json
{
  "error": "future date selected"
}
```
4. `401`: Unauthorized Request. Access to API is forbidden.
5. `404`: Not Found - URL Not Found


## **Request Parameters**

The **`“bold”`** one's are mandatory, and the *`“italic”`* one's are optional.

1. **`deviceId`**(integer): Id of the device for which the location data need to be fetched. `Example: 10647019`

2. **`startTime`**(number): Start Epoch timestamp in seconds from which the events need to be fetched. `Example: 1737431640`

3. **`endTime`**(number): End Epoch timestamp in seconds till which the events need to be fetched. `Example: 1737433620`

4. *`skipPeriod`*(integer): Defined in minutes. For example, if 2 is passed then the returned data packet will have a minimum difference of 2 mins else 0. `Example: 2`

## **Response Parameters** 

- **`drivingBehaviourCount parameters`**: Driving behavior count in the selected device.
    - *`haCount`*(integer): Count of harsh acceleration events.

    - *`hbCount`*(integer): Count of harsh braking events.

    - *`hcCount`*(integer): Count of harsh cornering events.

- **`summary parameters:`**

    - *`distance`*(number): Total drive distance in kilometers.

    - *`duration`*(number): Total drive duration in seconds.

    - *`avgSpeed`*(number): Average speed in km/h.

    - *`startAddress`*(string): Start Epoch time of the event. i.e. the time at which the data first came from the device for the selected day.

    - *`endAddress`*(string): End Epoch time of the event. i.e. the time at which the last data came from the device for the selected day. 

    - *`startTimestamp`*(number): Start time of the device i.e. the time at which the data first came from the device for the selected day. 

    - *`endTimestamp`*(number): End time of the device i.e. the time at which the last data came from the device for the selected day. 

- **`positionList parameters:`**
    - *`address`*(string): Address of the location event.
    - *`timestamp`*(number): Epoch timestamp of the event.
    - *`longitude`*(number): Longitude.
    - *`latitude`*(number): Latitude.
    - *`heading`*(number): Device heading direction in degrees from North.
    - *`speed`*(number): Device speed at the particular location.
    - *`ignition`*(number): Whether vehicle ignition is On or Off. 0 means ignition is OFF and 1 means ignition is ON.
    - *`powerSupplyVoltage`*(number): Battery voltage value in millivolts.
    - *`gpsFix`*(boolean): GPS is fix or not for the device. true meanse GPS is fixed and false means GPS is not fixed.
    - *`validGPS`*(boolean): Checks whether GPS is valid or not.
    - *`accOff`*(boolean): Checks for whether adaptive cruise control is enabled or not.
    - *`movementStatus`*(integer): Checks the movement status of the device.
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
        - `0` : Real location being sent by the user.
        - `1` : Mock location beng sent by the user.
    - *`isAirplanemode`*(boolean): Checks whether the mobile's airplane mode is ON or OFF.
        - `true` : Airplane mode is ON.
        - `false` : Airplane mode is OFF.
    - *`callStatus`*(number): Current call status like:
        - `0` : CALL_STATE_IDLE
        - `1` : CALL_STATE_RINGING
        - `2` : CALL_STATE_ONCALL
          
    - *`deviceStatus`*(integer): Status of the device in the current location.
        - `0` : IN_VEHICLE
        - `1` : ON_BICYCLE
        - `2` : ON_FOOT
        - `3` : STILL
        - `4` : UNKNOWN
        - `5` : TILTING
        - `6` : WALKING
        - `7` : RUNNING
           
    - *`phoneEvent`*(integer): Checks the location permission that the user enables/disables in the mobile phone.
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
        - `26` : GEOFENCE
        - `27` : STOPPAGE
        - `28` : IDLE
        - `29` : TOWING
        - `126` : GPRS CONNECTIVITY
        - `129` : VEHICLE BATTERY
        - `133` : MILEAGE
        - `146` : GPS CONNECTIVITY
        - `151` : DISTANCE COVERED
        - `161` : INTERNAL BATTERY VOLTAGE 
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
    - *`geofenceId`*(number):This is the ID of the geofence for which the alarm got generated. This will come only when the 'type' field return 26 i,e geofence.

## **Sample Input**

```
https://intouch.mappls.com/iot/api/device/10647019/events?startTime=1737431640&endTime=1737433620&skipPeriod=2
```

## **Sample ouput**

```json
{
    "data": {
        "deviceId": 10647019,
        "summary": {
            "distance": 3.27,
            "duration": 1148,
            "avgSpeed": 17.31,
            "startAddress": "1,2, Periyar Centre, GD Birla Marg, Sarita Vihar, New Delhi, Delhi. 58 m from Bhuvnesh Yadav Chaat Bhandar, Pin-110076 (India)",
            "endAddress": "19A, Okhla Phase 3 Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 102 m from Nigam Primary School, Pin-110020 (India)",
            "startTimestamp": 1737431645,
            "endTimestamp": 1737432793
        },
        "positionList": [
            {
                "address": "1,2, Periyar Centre, GD Birla Marg, Sarita Vihar, New Delhi, Delhi. 58 m from Bhuvnesh Yadav Chaat Bhandar, Pin-110076 (India)",
                "timestamp": 1737431645,
                "longitude": 77.2930207,
                "latitude": 28.5387681,
                "heading": 239.0,
                "speed": 35.0,
                "ignition": true,
                "gpsFix": false,
                "validGPS": true,
                "accOff": false,
                "movementStatus": "moving",
                "mobileInfo": {
                    "locationSource": 1,
                    "mockLocation": 0,
                    "isAirplanemode": false,
                    "callStatus": 0
                }
            },
            {
                "address": "23, Sarita Vihar Underpass, Block E, Okhla Industrial Estate Phase 2, New Delhi, Delhi. 51 m from Mahindra Genesis Cars Service Centre & Spare Parts, Pin-110020 (India)",
                "timestamp": 1737431863,
                "longitude": 77.2797926,
                "latitude": 28.5332643,
                "heading": 248.0,
                "speed": 6.0,
                "ignition": false,
                "gpsFix": false,
                "validGPS": true,
                "accOff": false,
                "movementStatus": "stopped",
                "mobileInfo": {
                    "locationSource": 1,
                    "mockLocation": 0,
                    "isAirplanemode": false,
                    "callStatus": 0
                }
            },
            {
                "address": "8, Unnamed Road, Block F, Okhla Industrial Estate Phase 2, New Delhi, Delhi. 15 m from One Direct, Pin-110020 (India)",
                "timestamp": 1737432193,
                "longitude": 77.272177,
                "latitude": 28.5385415,
                "heading": 327.0,
                "speed": 34.0,
                "ignition": true,
                "gpsFix": false,
                "validGPS": true,
                "accOff": false,
                "movementStatus": "moving",
                "mobileInfo": {
                    "locationSource": 1,
                    "mockLocation": 0,
                    "isAirplanemode": false,
                    "callStatus": 0
                }
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




<div align="center">@ Copyright 2025 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

