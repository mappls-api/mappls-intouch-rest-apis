
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Nearby Device Locator API

## **Introduction**

This API retrieves the live location and associated data of all nearby vehicles, assets, and people within a specified buffer range. Leveraging connected devices, sensors, and mobile technology, the API ensures precise location awareness for app users. It provides real-time visibility of tracked objects, delivering not only location data but also various additional fields that enhance application functionality. This API is suitable for multiple use cases, including transportation, logistics, and personnel information services, across web and mobile development platforms.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices/nearby

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- `200(OK)`: Successful operation.
- `203(Device Not Found)`: No devices found within the specified buffer.
- `400(Bad Request)`: Invalid device ID supplied or invalid data type. For example, input attribute "buffer" is of type number but string value gets passed or invalid coordinates location for location type "polygon" in geometry geojson object etc.
- `401(Unauthorized)`: Access to the API is forbidden due to missing or invalid authorization.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**

The **“bold”** one’s are mandatory, and the *“italic”* one’s are optional.

- *`buffer`* (number): The buffer distance in meters within which nearby vehicles/assets will be returned. This parameter is optional, with a default value of 50 meters if not provided.

- **`geometry`** (object): GeoJSON-formatted location coordinates. Vehicles/assets are fetched around this location based on the configured buffer distance.
Example:-

```json
{
  "type": "Point",
  "coordinates": [
    77.4567,
    28.2345
  ]
}
```

## **Response Parameters**

- **`data`** (array): Contains details of all nearby devices.

- **`DeviceData`**:

- **`id`** (integer): Unique identifier for the device.
- **`active`** (string): Indicates whether the device is active. Possible values: true, false. `Example: true`
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
- **`vehicleBattery`** (number): Battery level of the vehicle. `Example: 13568.98`

- **`location`** (object): Location details. 
    - **`gpsTime`** (number): GPS timestamp. `Example: 1574736922`
    - **`gprsTime`** (number): GPRS timestamp. `Example: 1574736922`
    - **`latitude`** (number): Latitude of the device. `Example: 28.551255163434`
    - **`longitude`** (number): Longitude of the device. `Example: 77.2687`
    - **`address`** (string): Physical address of the location. `Example: 244, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 2 m from Usha Exim Pvt Ltd pin-110020`
    - **`altitude`** (number): Altitude above sea level. `Example: 234`
    - **`heading`** (number): Direction of movement in degrees. `Example: 196.868`
    - **`speedKph`** (number): Speed in kilometers per hour. `Example: 27.85`
    - **`odometer`** (number): Total distance covered by the device. `Example: 12548.22`
    
- **`deviceDetails`** (object): Details of the device.
    - **`name`** (string): Name of the device. `Example: DL3CCM8097`
    - **`registrationNumber`** (string): Registration number of the device. `Example: DL3CCM8097`
    - **`deviceType`** (string): Type of the device(i.e., car, truck, bus, bike, tracktor, JCB, excavator). `Example: car`
    
- **`alertsObject`** (object): Alert details, if any.
    - **`deviceId`** (number): Id for the device that generates the alert. This parameter appears only in the response of the /alarmLog GET API. `Example: 8989`
    - **`timestamp`** (number): Time at which the alert got generated. `Example: 1577589789`
    - **`latitude`** (number): Latitude of the alert location. `Example: 28.550962381896`
    - **`longitude`** (number): Longitude of the alert location. `Example: 77.26890675033`
    - **`address`** (string): Location address at which the alarm got generated. `Example: 237, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 19 m from Wipro BPO Corporate Office pin-110020`
    - **`alarmType`** (integer): Type of alarm to create. Following are the alarm types & their corresponding IDs. `Example: 28`
         - `IGNITION`: 21
         - `OVERSPEED`: 22
         - `UNPLUGGED`: 23
         - `PANIC`: 24
         - `GEOFENCE`: 26,
         - `STOPPAGE`: 27
         - `IDLE`: 28
         - `TOWING`: 29
         - `GPRS CONNECTIVITY`: 126
         - `VEHICLE BATTERY`: 129
         - `MILEAGE`: 133
         - `GPS CONNECTIVITY`: 146
         - `DISTANCE COVERED`: 151
         - `INTERNAL BATTERY VOLTAGE`:161
         
    - **`limit`** (integer): Alarm limit as set in the config. For example, if an overspeed alarm set on limit of 44 km/hr in the alarm config setting, then this attribute will return 44 km/hr. `Example: 44`
    - **`duration`** (integer): Alarm duration limit as set in the alarm config section. For example, if duration of overspeed alarm is set as 20 secs, then the alarm will generate when the vehicle overspeeds for a duration of 20 secs. `Example: 20`
    - **`actualLimit`** (integer): The actual data received from the device at that particular moment when the alarm got generated. `Example: 57`
    - **`actualDuration`** (integer): Actual duration for which the device breached the alarm config limit. `Example: 25`
    - **`severity`** (integer): Severity of the alarm. `Example: 1`
         - `0` - Low Severity
         - `1` - High Severity
    - **`data`** (integer): Describes the state of the alarm. `Example: 1`
        - `IGNITION` (type = 21):
          - `0`: OFF
          - `1`: ON
        - `AC` (type = 25):
          - `0`: OFF
          - `1`: ON
        - `GEOFENCE` (type = 26):
          - `1`: Entry & Exit Geofence
          - `2`: Entry Geofence
          - `3`: Leaving Geofence
          - `4`: Long Stay In Geofence
    - **`geofenceId`** (number): This is the ID of the geofence for which the alarm got generated. This will come only when the *'type'* field return `26` i,e geofence. `Example: 987876`
    
- **`canInfo`** (object): CAN (Controller Area Network) data.
    - **`calcEngineVal`** (integer): Calculated engine value. `Example: 0`
    - **`greenDriveType`** (string): Eco-driving metrics (e.g., Harsh Acceleration). `Example: HA`
         - `HA`: Harsh acceleration
         - `HB`: Harsh Breaking
         - `HC`: Harsh Cornering
    - **`canTimestamp`** (number): Exact time at which the CAN data got generated by the device. `Example: 1568362645`
    - **`coolantTemp`** (number): Coolant temperature. `Example: 87`
    - **`engineRPM`** (integer): Engine revolutions per minute. `Example: 796`
    - **`accelPedal`** (number): This is accelerator pedal value in *percentage*. `Example: 8.4`
    - **`parkBrake`** (number): This is parking break. `Example: 0`
         - `0` means parking break is disengaged
         - `1` means parking break is engaged.
    - **`breakPedal`** (number): Brake pedal status. `Example: 0`
         - `0` means break pedal is disengaged
         - `1` means break pedal is engaged
    - **`fuelLevel`** (integer): Level of the fuel in liters. `Example: 14`
    - **`driverDoor`** (number): Driver door status. `Example: 0`
         - `1` means door is open
         - `0` means door is closed
    - **`headLights`** (number): Headlight status. `Example: 1`
         - `0`: Off
         - `1`: On
    - **`blinker`** (number): Blinker status. `Example: 0`
         - `0`: Off
         - `1`: On
    - **`gearState`** (number): Current gear state. `Example: 0`
         - `0`: Neutral 
         - `1`: Drive
         - `2`: Sports
         - `3`: Reverse
    - **`intakeAirTemp`** (number): This is the intake air temperature of the engine. `Example: 62`
    - **`intakeabsolutePress`** (number): This is the intake absolute pressure of the engine. It is defined in Pa(Pas*cal). `Example: 42`
    - **`ac`** (integer): Air conditioner status. `Example: 0`
         - `0`: Off
         - `1`: On
    - **`fuelConsAVG`** (integer): Fuel constant average. `Example: 99`
    
- **`deviceFaults`** (array): List of device faults.
    - **`code`** (integer): Fault code. `Example: 1001`
    - **`timetamp`** (number): Time the fault was recorded. `Example: 787654544`
    - **`status`** (integer): Describes the status of the fault which was detected. `Example: 0`
         - `0`: OPEN
         - `1`: Close
    - **`closedOn`** (number): Time the fault was resolved. `Example: 556567872`
    
- **`currentGeofence`** (number): List of active geofences.

- **`todaysDrive`** (object): Driving statistics for the day.
    - **`todayKms`** (number): Total kilometers driven today. `Example: 55.67`
    - **`todayMovementTime`** (number): Total time in motion today (in seconds). `Example: 67654`
    - **`todayIdleTime`** (number): Total idle time today (in seconds). `Example: 4444`
    - **`todayDriveCount`** (integer): Number of trips today. `Example: 5`

- **`externalSensors`** (object): External sensor data. 
    - **`sensorId`** (string): ID of the sensor. `Example: 1`
    - **`temperature`** (number): Temperature recorded by the sensor. `Example: 28.32`

- **`fuelLiters`** (number): Fuel level in liters, Value is calculated using external fuel sensor. `Example: 78.8`

## **Sample Input**

```
https://intouch.mappls.com/iot/api/devices/nearby?buffer=1000&geometry={"type": "Point", "coordinates": [77.2589114251555,28.55559861601342]}
```
## **Sample Output**

```json
{
    "data": [
        {
            "id": 1468319,
            "active": true,
            "status": 5,
            "location": {
                "gpsTime": 1698038797,
                "gprsTime": 1698152890,
                "latitude": 28.555276666666668,
                "longitude": 77.265755,
                "altitude": 210.3,
                "heading": 92.0,
                "speedKph": 0.0,
                "address": "Modi Mill Footover Bridge, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 73 m from Modi Mill Bus Stop, Pin-110020 (India)",
                "odometer": 455.48633027302105,
                "gpsSignal": 10
            },
            "deviceDetails": {
                "name": "uniposA5",
                "registrationNumber": "evoluteUniPOSa5",
                "deviceType": "Person",
                "trackingCode": "19C7BF937D3ABF498FB020696573AA55D330E2AF83D7FCA0",
                "internalBatteryLevel": 20
            },
            "canInfo": {
                "canTimestamp": 1698152817,
                "chargingStatus": 0,
                "ignition": 0
            },
            "todaysDrive": {
                "todayKms": 0.0,
                "todayMovementTime": 0,
                "todayIdleTime": 0,
                "todayDriveCount": 0
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/live/devices/#/1468319?access_token=13ddd950-48da-437c-938c-b928b2a9e814"
            },
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
            "id": 1414058,
            "active": true,
            "status": 5,
            "location": {
                "gpsTime": 1681358384,
                "gprsTime": 1681358460,
                "latitude": 28.551021,
                "longitude": 77.267559,
                "altitude": 224.4782,
                "heading": 160.25,
                "speedKph": 7.0,
                "address": "52, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 26 m from Orient Electric Ltd Corporate Office, Pin-110020 (India)",
                "odometer": 50.323753582483974,
                "gpsSignal": 4
            },
            "deviceDetails": {
                "name": "vishal123",
                "registrationNumber": "vishal123",
                "deviceType": "Person",
                "trackingCode": "A96FD607952F654A4C83424090140FC5C454D917AD1931834A55D6A2B6F2132A3D92DDF16F4AEED3612810C6682FD9DC",
                "internalBatteryLevel": 74
            },
            "canInfo": {
                "canTimestamp": 1681358384,
                "chargingStatus": 0,
                "ignition": 0
            },
            "todaysDrive": {
                "todayKms": 0.0,
                "todayMovementTime": 0,
                "todayIdleTime": 0,
                "todayDriveCount": 0
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/live/devices/#/1414058?access_token=13ddd950-48da-437c-938c-b928b2a9e814"
            },
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




<div align="center">@ Copyright 2022 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

