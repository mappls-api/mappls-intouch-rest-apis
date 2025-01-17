
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

2. **`startTime`**(number): Start Epoch timestamp in seconds from which the events need to be fetched. `Example: 1736411146`

3. **`endTime`**(number): End Epoch timestamp in seconds till which the events need to be fetched. `Example: 1736416846`

4. *`skipPeriod`*(integer): Defined in minutes. For example, if 2 is passed then the returned data packet will have a minimum difference of 2 mins else 0. `Example: 2`

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
    - *`address`*(string): Address of the location event. `Example: 213, 1st Cross Road, HAL Stage 2, Bengaluru, Karnataka. 15 m from The Bodhi Tree pin-560038 (India)`
    - *`timestamp`*(number): Epoch timestamp of the event. `Example: 1574937348`
    - *`longitude`*(number): Longitude. `Example: 77.74937348`
    - *`latitude`*(number): Latitude. `Example: 55.74937348`
    - *`heading`*(number): Device heading direction in degrees from North. `Example: 298`
    - *`speed`*(number): Device speed at the particular location. `Example: 33.33`
    - *`ignition`*(number): Whether vehicle ignition is On or Off. 0 means ignition is OFF and 1 means ignition is ON. `Example: 0`
    - *`powerSupplyVoltage`*(number): Battery voltage value in millivolts. `Example: 12769`
    - *`gpsFix`*(boolean): GPS is fix or not for the device. true meanse GPS is fixed and false means GPS is not fixed. `Example: true`
    - *`validGPS`*(boolean): Checks whether GPS is valid or not. `Example: true`
    - *`accOff`*(boolean): Checks for whether adaptive cruise control is enabled or not. `Example: true`
    - *`movementStatus`*(integer): Checks the movement status of the device. `Example: 1`
        - `1` : Moving
        - `2` : Idle
        - `3` : Stopped
        - `4` : Towing
        - `5` : No Data
        - `6` : Power Off
        - `7` : No Gps
        - `8` : On Trip
        - `9` : Free Vehicle 
    - *`durationTime`*(number): Time spent at the current location in seconds. `Example: 670`
    - *`greenDriveType`*(string): Driving behavior type. `Example: HA`
        - `HA` : Harsh acceleration
        - `HB` : Harsh Breaking
        - `HC` : Harsh Cornering
    - *`tripStatus`*(integer): Trip status. `Example: 0`
        - `0` : On Trip
        - `1` : Free Vehicle.
- **`mobileInfo parameters:`**
    - *`locationSource`*(number): Returns the source of the location. `Example: 0`
        - `1` : GPS connected, accuracy < 50 meters.
        - `2` : GPRS connected, accuracy > 50 meters.
    - *`mockLocation`*(integer): Indicates if the location being sent is real or a mock location. `Example: 1`
        - `0` : Real location being sent by the user.
        - `1` : Mock location beng sent by the user.
    - *`isAirplanemode`*(boolean): Checks whether the mobile's airplane mode is ON or OFF. `Example: true`
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
    - *`deviceId`*(number): ID of the device associated with the alert..Will come only in case of /alarmLog GET API response `Example: 8989`

    - *`timestamp`*(number): Time at which the alert was generated. `Example: 1577589789`
    - *`latitude`*(number): Latitude of the location where the alert was generated. `Example: 28.550962381896`   
    - *`longitude`*(number): Longitude of the location where the alert was generated. `Example: 77.26890675033`
    - *`address`*(string): Address of the location where the alert was generated. `Example: 237, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 19 m from Wipro BPO Corporate Office pin-110020`
    - *`alarmType`*(integer): Type of alarm to create. Following are the alarm types & their corresponding IDs. `Example: 28`
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
    - *`actualLimit`*(integer): The actual data received from the device at that particular moment when the alarm got generated. `Example: 57`
    - *`actualDuration`*(integer): Actual duration for which the device breached the alarm config limit. `Example: 25`
    - *`severity`*(integer): Indicates the severity level of the alarm. `Example: 1`
        - `0` : Low Severity.
        - `1` : High Severity.   
    - *`data`*(integer): Describes the state of the alarm. `Example: 1`
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
    - *`geofenceId`*(number):This is the ID of the geofence for which the alarm got generated. This will come only when the 'type' field return 26 i,e geofence. `Example: 987876`

## **Sample Input**

```
https://intouch.mappls.com/iot/api/device/10647019/events?startTime=1736861445&endTime=1736864985&skipPeriod=2
```

## **Sample ouput**

```json
{
    "data": {
        "deviceId": 10647019,
        "summary": {
            "distance": 13.76,
            "duration": 2890,
            "avgSpeed": 36.53,
            "startAddress": "237, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 10 m from MapmyIndia Head Office New Delhi, Pin-110020 (India)",
            "endAddress": "East Sapphire, Unnamed Road, Block E, Sector 42, Noida, Uttar Pradesh. 1 m from Green Empire Fruits and Vegetables, Pin-201303 (India)",
            "startTimestamp": 1736861501,
            "endTimestamp": 1736864391
        },
        "positionList": [
            {
                "address": "237, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 10 m from MapmyIndia Head Office New Delhi, Pin-110020 (India)",
                "timestamp": 1736861501,
                "longitude": 77.2689302,
                "latitude": 28.5508126,
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
                    "callStatus": 0
                }
            },
            {
                "address": "237, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 10 m from MapmyIndia Head Office New Delhi, Pin-110020 (India)",
                "timestamp": 1736861832,
                "longitude": 77.2689254,
                "latitude": 28.5508131,
                "heading": 331.0,
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
                    "callStatus": 0
                }
            },
            {
                "address": "237, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 10 m from MapmyIndia Head Office New Delhi, Pin-110020 (India)",
                "timestamp": 1736862163,
                "longitude": 77.2689352,
                "latitude": 28.5508265,
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
                    "callStatus": 0
                }
            },
            {
                "address": "237, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 21 m from MapmyIndia Head Office New Delhi, Pin-110020 (India)",
                "timestamp": 1736862464,
                "longitude": 77.2688886,
                "latitude": 28.5508783,
                "heading": 203.0,
                "speed": 3.0,
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
                "address": "64, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 26 m from Wadhwa International, Pin-110020 (India)",
                "timestamp": 1736862585,
                "longitude": 77.2679843,
                "latitude": 28.5497468,
                "heading": 156.0,
                "speed": 26.0,
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
                "address": "Sri Maa Anandamayee Ashram Marg, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 106 m from Banarsidas Chandiwala Institute of Medical Science, Pin-110020 (India)",
                "timestamp": 1736862705,
                "longitude": 77.2658245,
                "latitude": 28.5448512,
                "heading": 259.0,
                "speed": 15.0,
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
                "address": "281, Shri Maa Anandmai Marg, Okhla Industrial Estate Phase 2, New Delhi, Delhi. 37 m from Kalkaji Depot Bus Stop, Pin-110020 (India)",
                "timestamp": 1736862825,
                "longitude": 77.2664922,
                "latitude": 28.5393592,
                "heading": 158.0,
                "speed": 44.0,
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
                "address": "9/3, Tum Road, Block B, Okhla Industrial Estate Phase 2, New Delhi, Delhi. 14 m from Air Servo House, Pin-110020 (India)",
                "timestamp": 1736862945,
                "longitude": 77.2736562,
                "latitude": 28.5364293,
                "heading": 150.0,
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
            },
            {
                "address": "30, Okhla Estate Marg, Block E, Okhla Industrial Estate Phase 2, New Delhi, Delhi. 48 m from Uma Shanker Khandelwal and Company, Pin-110020 (India)",
                "timestamp": 1736863067,
                "longitude": 77.2784955,
                "latitude": 28.5328891,
                "heading": 70.0,
                "speed": 20.0,
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
                "address": "3,4, GD Birla Marg, Institutional Area, Jasola, New Delhi, Delhi. 63 m from Asia Pacific Institute of Management, Pin-110025 (India)",
                "timestamp": 1736863190,
                "longitude": 77.2932075,
                "latitude": 28.5392253,
                "heading": 66.0,
                "speed": 51.0,
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
                "address": "1, GD Birla Marg, Jasola, New Delhi, Delhi. 87 m from The Eden Hotel, Pin-110025 (India)",
                "timestamp": 1736863326,
                "longitude": 77.2996334,
                "latitude": 28.5418571,
                "heading": 71.0,
                "speed": 7.0,
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
                "address": "52, GD Birla Marg, Block G, Shaheen Bagh, New Delhi, Delhi. 18 m from Shaheen Bagh Bus Stop, Pin-110025 (India)",
                "timestamp": 1736863450,
                "longitude": 77.303003,
                "latitude": 28.5430659,
                "heading": 65.0,
                "speed": 15.0,
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
                "address": "86, GD Birla Marg, Block G, Shaheen Bagh, New Delhi, Delhi. 3 m from Kalindi Kunj Bus Stop, Pin-110025 (India)",
                "timestamp": 1736863575,
                "longitude": 77.305957,
                "latitude": 28.5451783,
                "heading": 18.0,
                "speed": 2.0,
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
                "address": "GD Birla Marg, Saidabad, New Delhi, Delhi. 119 m from Atlantic Water World, Pin-110076 (India)",
                "timestamp": 1736863695,
                "longitude": 77.308154,
                "latitude": 28.5450756,
                "heading": 133.0,
                "speed": 14.0,
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
                "address": "Kalindi Kunj Bridge, Saidabad, New Delhi, Delhi. 79 m from Madanpur Khadr Police Chowki, Pin-110076 (India)",
                "timestamp": 1736863815,
                "longitude": 77.3118731,
                "latitude": 28.5457547,
                "heading": 47.0,
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
            },
            {
                "address": "Amrapali Marg, Sector 95, Noida, Uttar Pradesh. 13 m from Puncture Shop, Pin-201301 (India)",
                "timestamp": 1736863935,
                "longitude": 77.3222445,
                "latitude": 28.5545551,
                "heading": 44.0,
                "speed": 37.0,
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
                "address": "Amrapali Marg, Sector 38 A, Noida, Uttar Pradesh. 30 m from Noida Sector 37 Bus Stop, Pin-201303 (India)",
                "timestamp": 1736864055,
                "longitude": 77.3374139,
                "latitude": 28.5613758,
                "heading": 64.0,
                "speed": 62.0,
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
                "address": "114, Dadri Main Road, Block C, Sector 40, Noida, Uttar Pradesh. 112 m from Delhi Lawyer, Pin-201303 (India)",
                "timestamp": 1736864175,
                "longitude": 77.3539658,
                "latitude": 28.5618688,
                "heading": 102.0,
                "speed": 44.0,
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
                "address": "193, Unnamed Road, Block E, Sector 42, Noida, Uttar Pradesh. 129 m from Cine Wedding Arts, Pin-201303 (India)",
                "timestamp": 1736864296,
                "longitude": 77.3568671,
                "latitude": 28.5566046,
                "heading": 192.0,
                "speed": 4.0,
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

