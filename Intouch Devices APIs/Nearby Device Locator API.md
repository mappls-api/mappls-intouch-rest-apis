
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Nearby Device Locator API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Nearby Device Locator API` retrieves the live location and associated data of all nearby vehicles, assets, or personnel tracking devices within a specified buffer range. Leveraging connected devices, sensors, and mobile technology, the API ensures precise location awareness for app developers. It provides real-time visibility of tracked objects, delivering not only location data but also additional attributes that enhance application functionality. This API is suitable for multiple use cases, including transportation, logistics, and personnel information services, across web and mobile development platforms.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. The developer must send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices/nearby

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**

- `200(OK)`: Successful operation.
- `203(Device Not Found)`: No devices found within the specified buffer.
- `400(Bad Request)`: Invalid device ID supplied or invalid data type. For example, input attribute "buffer" is of type number but string value gets passed or invalid coordinates location for location type "polygon" in geometry geojson object etc.
- `401(Unauthorized)`: Access to the API is forbidden due to missing or invalid authorization.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**
**`Bold`** parameters are mandatory, and *`italic`* parameters are optional.
- **`geometry`** (string): GeoJSON-formatted location coordinates. Vehicles or assets are retrieved around this location based on the specified buffer distance.
    - Example:-
        ```json
        {
        "type": "Point",
        "coordinates": [
            77.4567,
            28.2345
        ]
        }
        ```
- *`buffer`* (integer): The buffer distance in meters within which nearby vehicles/assets will be returned. This parameter is optional, with a default value of 50 meters if not provided (max limit = 10000 m).
- *`fields`* (string): Specifies an additional device attribute to be included in the response. Only one field can be requested per API call. If not specified, the default fields are returned. Example: `canInfo`, `deviceDetails`, or `location`.
- *`ignoreBeacon`* (boolean): If set to `true`, devices reporting beacon-based or proximity-derived locations are excluded from the response. Default value is `false`.
- *`ignoreLiveData`* (boolean): If set to `true`, devices with live data updates are excluded from the result set. Default value is `false`.
- *`includeInActive`* (boolean): If set to `true`, inactive devices are also included in the response. By default, only active devices are returned.
- *`state`* (integer): Filters devices based on their movement status. Accepted values are the same as the `status` codes returned in the response (e.g., `1` for Moving, `2` for Idle, `3` for Stopped).

## **Response Parameters**
- **`data`** (array): Contains a list of nearby devices and their associated information.
    - **`id`** (integer): Unique identifier for the device.
    - **`active`** (boolean): Indicates whether the device is active. Possible values: `true`, `false`.
    - **`status`** (number): Movement status of the device.
        - `1`: Moving
        - `2`: Idle (ignition on, speed <= 7 km/hr)
        - `3`: Stopped (engine off)
        - `4`: Towing (ignition off, speed > 0)
        - `5`: No data (no communication or GPRS signal)
        - `6`: Power off
        - `7`: No GPS (satellite count < 4)
        - `8`: On trip (device on active trip)
        - `9`: Free vehicle (not on active trip)
    - **`vehicleBattery`** (number): Battery level of the vehicle.
    - **`location`** (object): Location details. 
        - **`gpsTime`** (number): GPS timestamp.
        - **`gprsTime`** (number): GPRS timestamp.
        - **`latitude`** (number): Latitude of the device.
        - **`longitude`** (number): Longitude of the device.
        - **`address`** (string): Physical address of the location.
        - **`altitude`** (number): Altitude above sea level.
        - **`heading`** (number): Direction of movement in degrees.
        - **`speedKph`** (number): Speed in kilometers per hour.
        - **`odometer`** (number): Total distance covered by the device.
        - **`gpsSignal`** (integer): Number of GPS satellites detected by the device. A higher value indicates better GPS accuracy.
    - **`deviceDetails`** (object): Details of the device.
        - **`name`** (string): Name of the device.
        - **`registrationNumber`** (string): Registration number of the device.
        - **`deviceType`** (string): Type of the device (e.g., car, truck, bus, bike, tractor, JCB, excavator).
        - **`chassisNumber`** (string): Unique chassis number of the vehicle associated with the device.
        - **`trackingCode`** (string): Unique tracking identifier assigned to the device for monitoring and identification.
    - **`canInfo`** (object): CAN (Controller Area Network) data.
        - **`canTimestamp`** (number): Exact time at which the CAN data got generated by the device.
        - **`disTravelCodes`** (number): Device-specific travel code value used internally to represent travel distance or related CAN data.
        - **`chargingStatus`** (integer): Indicates whether the battery is charging.
            - `0`: Not charging
            - `1`: Charging
        - **`battryCurrent`** (number): Battery current reported through CAN data.
        - **`fuelLevel`** (integer): Level of the fuel in liters.
        - **`data`** (integer): Describes the state/value of the alarm.
            - `IGNITION` (type = 21): Ignition status of the vehicle.
                - `0`: Ignition OFF
                - `1`: Ignition ON
            - `AC` (type = 25):
                - `0`: OFF
                - `1`: ON
            - `GEOFENCE` (type = 26):
                - `1`: Entry & Exit Geofence
                - `2`: Entry Geofence
                - `3`: Leaving Geofence
                - `4`: Long Stay In Geofence
        - **`calcEngineVal`** (integer): Calculated engine value.
        - **`engineFuelRate`** (number): Fuel consumption rate of the engine.
        - **`greenDriveType`** (string): Eco-driving metrics (e.g., Harsh Acceleration).
                - `HA`: Harsh acceleration
                - `HB`: Harsh Breaking
                - `HC`: Harsh Cornering
        - **`coolantTemp`** (number): Engine coolant temperature.
        - **`engineRPM`** (integer): Engine revolutions per minute.
        - **`accelPedal`** (number): Accelerator pedal position expressed as a percentage.
        - **`parkBrake`** (number): This is parking brake.
                - `0`: Parking brake disengaged
                - `1`: Parking brake engaged
        - **`breakPedal`** (number): Brake pedal status.
                - `0`: Brake pedal not pressed
                - `1`: Brake pedal pressed
        - **`driverDoor`** (number): Driver door status.
                - `0`: Door closed
                - `1`: Door open
        - **`headLights`** (number): Headlight status.
                - `0`: Off
                - `1`: On
        - **`blinker`** (number): Blinker status.
                - `0`: Off
                - `1`: On
        - **`gearState`** (number): Current gear state.
                - `0`: Neutral 
                - `1`: Drive
                - `2`: Sport
                - `3`: Reverse
        - **`intakeAirTemp`** (number): This is the intake air temperature of the engine.
        - **`intakeabsolutePress`** (number): This is the intake absolute pressure of the engine. It is measured in Pa(Pascal)
        - **`ac`** (integer): Air conditioner status.
                - `0`: Off
                - `1`: On
        - **`fuelConsAVG`** (integer): Average fuel consumption calculated by the device.
    - **`currentGeofence`** (array): List of active geofence IDs associated with the device.
    - **`alerts`** (object): Alert details, if any.
        - **`deviceId`** (number): Unique ID of the device that generated the alert.
        - **`timestamp`** (number): Time at which the alert got generated.
        - **`latitude`** (number): Latitude of the alert location.
        - **`longitude`** (number): Longitude of the alert location.
        - **`address`** (string): Location address at which the alarm got generated.
        - **`alarmType`** (integer): Type of alarm to create. Following are the alarm types & their corresponding IDs.
            - `IGNITION`: 21
            - `OVERSPEED`: 22
            - `UNPLUGGED`: 23
            - `PANIC`: 24
            - `GEOFENCE`: 26
            - `STOPPAGE`: 27
            - `IDLE`: 28
            - `TOWING`: 29
            - `GPRS CONNECTIVITY`: 126
            - `VEHICLE BATTERY`: 129
            - `MILEAGE`: 133
            - `GPS CONNECTIVITY`: 146
            - `DISTANCE COVERED`: 151
            - `INTERNAL BATTERY VOLTAGE`:161       
        - **`duration`** (integer): Alarm duration limit as set in the alarm config section. For example, if duration of overspeed alarm is set as 20 secs, then the alarm will generate when the vehicle overspeeds for a duration of 20 secs.
        - **`actualDuration`** (integer): Actual duration for which the device breached the alarm config limit.
        - **`data`** (integer): Alarm-specific data value. The meaning of this field depends on the `alarmType`.
        - **`startTimestamp`** (long): Timestamp when the alarm condition started.
        - **`endTimestamp`** (long): Timestamp when the alarm condition ended.
        - **`limit`** (integer): Alarm limit as set in the config. For example, if an overspeed alarm set on limit of 44 km/hr in the alarm config setting, then this attribute will return 44 km/hr.
        - **`actualLimit`** (integer): The actual data received from the device at that particular moment when the alarm got generated.
        - **`severity`** (integer): Severity of the alarm.
            - `0`: Low Severity
            - `1`: High Severity
        - **`geofenceId`** (number): This is the ID of the geofence for which the alarm got generated. This field is returned only when the `alarmType` is `26` (Geofence).
    - **`todaysDrive`** (object): Driving statistics for the day.
        - **`todayKms`** (number): Total kilometers driven today.
        - **`todayMovementTime`** (number): Total time in motion today (in seconds).
        - **`todayIdleTime`** (number): Total idle time today (in seconds).
        - **`todayDriveCount`** (integer): Number of trips today.
    - **`links`** (object):
        - **`embedUrl`** (string):
    - **`geofenceDetails`** (array): List of geofence details in which the device is currently present.
        - **`entryTime`** (number): Timestamp when the device entered the geofence.
        - **`name`** (string): Name of the geofence.
        - **`id`** (number): Unique identifier of the geofence.
    - **`dinputs`** (object): Represents digital inputs received from the device for additional parameters. Keys `1` to `7` represent the digital input ports, and the value shows the input state.
        - `0`: Input OFF
        - `1`: Input ON
        - `null`: Input not available


## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/devices/nearby?geometry=%7B%22type%22%3A%22Point%22%2C%22coordinates%22%3A%5B77.50567833333334%2C12.886303333333334%5D%7D&buffer=15000&ignoreBeacon=false&ignoreLiveData=false&includeInActive=false&fields=location&state=5' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```
## **Sample Output Response**
```json
{
    "data": [
        {
            "id": 122403,
            "active": true,
            "status": 3,
            "vehicleBattery": 12402.0,
            "location": {
                "gpsTime": 1773138377,
                "gprsTime": 1773138398,
                "latitude": 28.5510583,
                "longitude": 77.2687716,
                "altitude": 225.0,
                "heading": 232.0,
                "speedKph": 0.0,
                "address": "244, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 28 m from HRX, Pin-110020 (India)",
                "odometer": 273121.11399495485,
                "gpsSignal": 11
            },
            "deviceDetails": {
                "name": "DL8CAG1009",
                "registrationNumber": "DL8CAG1009",
                "deviceType": "Car",
                "chassisNumber": "",
                "trackingCode": "357454075208957"
            },
            "canInfo": {
                "canTimestamp": 1773138377,
                "chargingStatus": 0,
                "ignition": 0,
                "ac": 0
            },
            "currentGeofence": [
                601352,
                606140,
                622595,
                657633,
                657634,
                659479,
                659906,
                667192,
                674104,
                676070,
                1219344,
                595902,
                616829,
                616834,
                616980,
                644136,
                644138,
                1120285,
                1470473
            ],
            "alerts": {
                "deviceId": 122403,
                "timestamp": 1773112276,
                "latitude": 28.5510583,
                "longitude": 77.2687716,
                "address": "244, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 28 m from HRX, Pin-110020 (India)",
                "alarmType": 27,
                "duration": 73,
                "actualDuration": 901,
                "data": 0,
                "startTimestamp": 1773111375,
                "endTimestamp": 1773112276
            },
            "todaysDrive": {
                "todayKms": 100.98,
                "todayMovementTime": 5354,
                "todayIdleTime": 924,
                "todayDriveCount": 1
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/live/devices/#/122403?access_token=73b5c6c2-0529-40b5-870d-e85a23f760c8"
            },
            "geofenceDetails": [
                {
                    "entryTime": 1773111217,
                    "name": "MapmyIndia 150036",
                    "id": 601352
                },
                {
                    "entryTime": 1773111134,
                    "name": "new1",
                    "id": 606140
                },
                {
                    "entryTime": 1773111217,
                    "name": "mmi",
                    "id": 622595
                },
                {
                    "entryTime": 1773111217,
                    "name": "Test",
                    "id": 657633
                },
                {
                    "entryTime": 1773111217,
                    "name": "z",
                    "id": 657634
                },
                {
                    "entryTime": 1773111134,
                    "name": "mapmyindia geofence",
                    "id": 659479
                },
                {
                    "entryTime": 1773111134,
                    "name": "testing",
                    "id": 659906
                },
                {
                    "entryTime": 1773110461,
                    "name": "Resw",
                    "id": 667192
                },
                {
                    "entryTime": 1773111217,
                    "name": "Office",
                    "id": 674104
                },
                {
                    "entryTime": 1773110967,
                    "name": "Testing only",
                    "id": 676070
                },
                {
                    "entryTime": 1773110967,
                    "name": "MMI_test1",
                    "id": 1219344
                },
                {
                    "entryTime": 1773111217,
                    "name": "AAAAA",
                    "id": 595902
                },
                {
                    "entryTime": 1773111268,
                    "name": "Route Point 1 184253",
                    "id": 616829
                },
                {
                    "entryTime": 1773111268,
                    "name": "Route Point 1 184254",
                    "id": 616834
                },
                {
                    "entryTime": 1773111268,
                    "name": "Route Point 5 184481",
                    "id": 616980
                },
                {
                    "entryTime": 1773111268,
                    "name": "Route Point 1 312105",
                    "id": 644136
                },
                {
                    "entryTime": 1773111268,
                    "name": "Route Point 1 312110",
                    "id": 644138
                },
                {
                    "entryTime": 1773111268,
                    "name": "Route Point 2 2064244",
                    "id": 1120285
                },
                {
                    "entryTime": 1773111104,
                    "name": "MMI Office",
                    "id": 1470473
                }
            ],
            "dinputs": {
                "1": 0,
                "2": 0,
                "4": null,
                "5": null,
                "6": null,
                "7": null
            }
        },
        {
            "id": 9018959,
            "active": true,
            "status": 5,
            "vehicleBattery": 0.0,
            "location": {
                "gpsTime": 1719231612,
                "gprsTime": 1719231616,
                "latitude": 28.5508783,
                "longitude": 77.2688133,
                "altitude": 242.0,
                "heading": 14.0,
                "speedKph": 0.0,
                "address": "237, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 25 m from MapmyIndia Head Office New Delhi, Pin-110020 (India)",
                "odometer": 7.380239003461167,
                "gpsSignal": 8
            },
            "deviceDetails": {
                "name": "MMI526441",
                "registrationNumber": "MMI526441",
                "deviceType": "Car"
            },
            "canInfo": {
                "canTimestamp": 1719231612,
                "disTravelCodes": 899110230,
                "chargingStatus": 0,
                "battryCurrent": 0.0,
                "fuelLevel": 130,
                "ignition": 0,
                "engineFuelRate": 76
            },
            "currentGeofence": [
                601352,
                606140,
                622595,
                657633,
                657634,
                659479,
                659906,
                667192,
                674104,
                676070,
                595902,
                616829,
                616834,
                616980,
                644136,
                644138
            ],
            "alerts": {
                "deviceId": 9018959,
                "timestamp": 1719231483,
                "latitude": 28.550745,
                "longitude": 77.2687066,
                "address": "236, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 23 m from MapmyIndia Head Office New Delhi, Pin-110020 (India)",
                "alarmType": 23,
                "limit": 0,
                "severity": 0
            },
            "todaysDrive": {
                "todayKms": 0.0,
                "todayMovementTime": 0,
                "todayIdleTime": 669,
                "todayDriveCount": 0
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/live/devices/#/9018959?access_token=73b5c6c2-0529-40b5-870d-e85a23f760c8"
            },
            "geofenceDetails": [
                {
                    "entryTime": 1719231459,
                    "name": "MapmyIndia 150036",
                    "id": 601352
                },
                {
                    "entryTime": 1719231459,
                    "name": "new1",
                    "id": 606140
                },
                {
                    "entryTime": 1719231459,
                    "name": "mmi",
                    "id": 622595
                },
                {
                    "entryTime": 1719231459,
                    "name": "Test",
                    "id": 657633
                },
                {
                    "entryTime": 1719231459,
                    "name": "z",
                    "id": 657634
                },
                {
                    "entryTime": 1719231459,
                    "name": "mapmyindia geofence",
                    "id": 659479
                },
                {
                    "entryTime": 1719231459,
                    "name": "testing",
                    "id": 659906
                },
                {
                    "entryTime": 1719231459,
                    "name": "Resw",
                    "id": 667192
                },
                {
                    "entryTime": 1719231459,
                    "name": "Office",
                    "id": 674104
                },
                {
                    "entryTime": 1719231459,
                    "name": "Testing only",
                    "id": 676070
                },
                {
                    "entryTime": 1719231459,
                    "name": "AAAAA",
                    "id": 595902
                },
                {
                    "entryTime": 1719231459,
                    "name": "Route Point 1 184253",
                    "id": 616829
                },
                {
                    "entryTime": 1719231459,
                    "name": "Route Point 1 184254",
                    "id": 616834
                },
                {
                    "entryTime": 1719231459,
                    "name": "Route Point 5 184481",
                    "id": 616980
                },
                {
                    "entryTime": 1719231523,
                    "name": "Route Point 1 312105",
                    "id": 644136
                },
                {
                    "entryTime": 1719231523,
                    "name": "Route Point 1 312110",
                    "id": 644138
                }
            ],
            "dinputs": {
                "1": 0,
                "2": null,
                "4": null,
                "5": null,
                "6": null,
                "7": null
            }
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

