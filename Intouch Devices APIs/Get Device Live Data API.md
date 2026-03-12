
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Get Device Live Data API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**

The *`Get Device Live Data API`* allows you to view a list of all available devices and provides accurate, real-time location and related data of vehicles, assets, and people using connected devices, sensors, or mobiles. It enables your app to have real-time visibility of tracked objects, offering not only location information but additional valuable metrics. This API is ideal for various use cases, including transport logistics and personnel tracking services, and can be used in both web and mobile platforms.

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


## **Input Method:** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
- `200(OK)`: The operation was successful.
- `203(Device Not Found)`: The specified device could not be located.
- `204(No Content)`: If device list is empty
- `400(Bad Request)`: The request is invalid due to incorrect device ID or data type.
- `401(Unauthorized)`: The request is forbidden. Authentication or valid authorization is required.
- `404(Not Found)`: The requested URL could not be found on the server.


## **Request Parameters**
All the parameters listed below are *`optional`*:
1. *`id`*(Integer/ Array[long]): This is the device's ID, a non-mandatory parameter. If not passed then by default the API will return the list of all active devices in the account.
2. *`fields`*(string): Non-mandatory. Specify the fields you want to be returned in the API response. If not sent, all default fields will be returned.
3. *`name`*(string): Non-mandatory. Filter devices by name. If not provided, devices of all names will be returned.
4. *`ignoreBeacon`*(Boolean): Non-mandatory field. If set to true then API will return all devices except those whose device type is beacon(mobile).
5. *`ignoreLiveData`*(boolean): Non-mandatory. If `true`, live data will not be included in the response.
6. *`includeInActive`*(Boolean): Non-mandatory boolean field. If this parameter is not provided, the API returns only active devices by default. If `true` then API reponse will have inactive devices along with active devices. If `false` then API will return only active devices
7. *`state`*(integer): Non-mandatory field. Input timestamp in this field to fetch only those live locations of devices which have come after the input timestamp. If `state` is sent then by default only active devices will be fetched irrespective of the status of `includeInActive` attribute.
8. *`groupId`*(Array[long]): Non-mandatory. Fetch devices belonging to the specified group(s).
9. *`isExtendedDataa`*(boolean): Non-mandatory. If true, extended device data will be included in the response.

## **Response Parameter**
- **`data`**: Represents the information associated with the devices.
    - **`id`**(integer)($int64): Unique identifier for the device.
    - **`active`**(boolean): Indicates if the device is active.
         - **`Enum Values`**: [ true, false ]
    - **`status`**(number) : Represents the device's movement status:
         - `1` : moving
         - `2` : idle i.e. ignition is on and speed <= 7km/hr
         - `3` : stopped i.e. engine is off
         - `4` : towing i.e. ignition is off, but vehicle speed
         - `5` : no data i.e. no communication of device with intouch server or no GPRS signal
         - `6` : power off
         - `7` : no gps i.e. satellite count is less than 4
         - `8` : on trip i.e. device is currently on an active trip
         - `9` : free vehicle i.e. device is not on any active trip
    - **vehicleBattery**(number): Battery voltage of the vehicle.
- **`location`**
    - **`gpsTime`**(number): GPS timestamp.     
    - **`gprsTime`**(number): GPRS timestamp.
    - **`latitude`**: `number` Device's latitude.
    - **`longitude`**: `number`  Device's longitude.
    - **`address`**: `string` Location address of the device.
    - **`altitude`** (number): Device altitude in meters.       
    - **`heading`** (number): Direction of movement in degrees.
    - **`speedKph`** (number): Speed in kilometers per hour.
    - **`odometer`**(number): Total distance covered by the vehicle.
- **`deviceDetails`**
    - **`name`**: `string` Device name.
    - **`registrationNumber`**: `string`  Vehicle registration number.
    - **`deviceType`**(string): Type of device.
    - **`Enum Values`**: `[ Car, Truck, Bus, Bike, Tractor, JCB, Excavator ]`
-  **``AlertObject``**
   - **`deviceId`**(number): Device ID that generated the alert(Will come only in case of /alarmLog GET API response). `Example: 8989`
   - **`timestamp`**(number): Time at which the alert got generated `Example: 1577589789`  
   - **`latitude`**(number): Latitude at the time of alert. `Example: 28.550962381896`      
   - **`longitude`**(number): Longitude at the time of alert. `Example: 77.26890675033`      
   - **`address`**(string): Location address at which the alarm got generated. `Example: "237, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 19 m from Wipro BPO Corporate Office pin-110020"`   
   - **`alarmType`**(integer): Type of alarm to create. Following are the alarm types & their corresponding IDs.
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
        - `161`: INTERNAL BATTERY VOLTAGEE
   - **`limit`**(integer): Alarm limit as set in the config. For example, if an overspeed alarm set on limit of 44 km/hr in the alarm config setting, then this attribute will return 44 km/hr. `Example: 44`  
   - **`duration`**(integer): Alarm duration limit as set in the alarm config section. For example, if duration of overspeed alarm is set as 20 secs, then the alarm will generate when the vehicle overspeeds for a duration of 20 secs. `Example: 20`   
   - **`actualLimit`**(integer): The actual data received from the device at that particular moment when the alarm got generated. `Example: 57`
   - **`actualDuration`**(integer): Actual duration for which the device breached the alarm config limit. `Example: 25`
   - **`severity`**(integer): 0 - Low Severity. 1 - High Severity. `Example: 1`
   - **`data`**:(integer) Describes the state of the alarm. `Example: 1`
        - `For IGNITION(type = 21)`
           - `0` : OFF
           - `1` : ON
        - `For AC(type=25)`
           - `0` : OFF
           - `1` : ON
        - `For GEOFENCE(type=26)`
           - `1` : Entry & Exit Geofence
           - `2` : Entry Geofence
           - `3` : Leaving Geofence
           - `4` : Long Stay In Geofence.
   - **`geofenceId`**(number): This is the ID of the geofence for which the alarm got generated. This will come only when the 'type' field return 26 i,e geofence. `Example: 987876`
-  **`canInfo`**
   - **`calcEngineVal`**(integer): `Example: 0`
   - **`greenDriveType`**(string): Driving behavior type. `Example: HA` Possible values:  
       - `HA` : Harsh Acceleration  
       - `HB` : Harsh Braking  
       - `HC` : Harsh Cornering.
   - **`canTimestamp`**(number): Exact time at which the CAN data got generated by the device. `Example: 1568362645`    
   - **`coolantTemp`**(number): Coolant temperature in degrees Celsius. `Example: 87`   
   - **`engineRPM`**(integer): Revolutions per minute of the engine. `Example: 796`      
   - **`accelPedal`**(number): This is accelerator pedal value as a percentage. `Example: 8.4`      
   - **`parkBrake`**(number): This is parking brake. `0` means parking brake is disengaged & `1` means parking brake is engaged.
   - **`brakePedal`**(number): Indicates brake pedal status: `1` means brake pedal is engaged & `0` means brake pedal is disengaged.
   - **`fuelLevel`**(integer): Fuel level in liters.
   - **`driverDoor`**(number): Driver door status:1 means door is open & 0 means door is closed.
   - **`headLights`**(number): Headlights status:  
       - `0`: OFF
       - `1`: ON
   - **`blinker`**: `number` Blinker status:  
       - `0`: OFF
       - `1`: ON
   - **`gearState`**(number): Gear state:  
       - `0`: Neutral  
       - `1`: Drive  
       - `2`: Sports  
       - `3`: Reverse.
   - **`intakeAirTemp`**(number): This is the intake air temperature of the engine in degrees Celsius.
   - **`intakeabsolutePress`**(number): This is the intake absolute pressure of the engine. It is defined in Pa(Pascal).
   - **`ac`**(integer): Air conditioner status:  
       - `0`: OFF
       - `1`: ON
   - **`fuelConsAVG`**(integer): Fuel constant average.
- **`deviceFaults`**
    - **`code`**(integer):Fault code.
    - **`timestamp`**(number): Timestamp when the fault was detected.
    - **`status`**(integer): Describes the status of the fault which was detected.
        - `0`: Open
        - `1`: Closed
    - **`closedOn`**(number): Timestamp when the fault was resolved.
- **`currentGeofence`**(array(number)): Array of geofence IDs currently associated with the device.
- **`todaysDrive`**
    - **`todayKms`**(number): Total kilometers driven today. 
    - **`todayMovementTime`**(number): Total movement time today in seconds.
    - **`todayIdleTime`**(number): Total idle time today in seconds.
    - **`todayDriveCount`**(integer): Number of drives completed today.
-  **`externalSensorObject`**
      - **`sensorId`**(string): Identifier for the external sensor.
      - **`temperature`**(number): Temperature reading from the external sensor in degrees Celsius.
- **`fuelLiters`**(number): Fuel level in liters, Value is calculated using external fuel sensor.

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/devices?id=53451&name=KA03MX6275_GPS&ignoreBeacon=false&ignoreLiveData=false&includeInActive=false' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer bd0279e8-3940-4e46-a5df-6a3cd13495c1' \
--header 'Cookie: HttpOnly'
```
## **Sample Output Response**
```json
{
    "data": [
        {
            "id": 53451,
            "active": true,
            "status": 3,
            "vehicleBattery": 12761.0,
            "location": {
                "gpsTime": 1770386043,
                "gprsTime": 1770386072,
                "latitude": 12.9625783,
                "longitude": 77.6485866,
                "altitude": 911.0,
                "heading": 174.0,
                "speedKph": 0.0,
                "address": "89/A, Anashwaram, 5th Cross Road, Kodihalli, Bengaluru, Karnataka. 36 m from Vishnuchitna Hostel, Pin-560038 (India)",
                "odometer": 29381.23301573239,
                "gpsSignal": 12
            },
            "deviceDetails": {
                "name": "KA03MX6275_GPS",
                "registrationNumber": "2343434343",
                "deviceType": "Car",
                "chassisNumber": "MA3EJKD1S00895885",
                "trackingCode": "352592573758752"
            },
            "canInfo": {
                "canTimestamp": 1770386043,
                "disTravelCodes": 899110240,
                "chargingStatus": 0,
                "ac": 0,
                "battryCurrent": 0.0,
                "fuelLevel": 87,
                "ignition": 0,
                "engineFuelRate": 93
            },
            "alerts": {
                "deviceId": 53451,
                "timestamp": 1770384241,
                "latitude": 12.9625783,
                "longitude": 77.6485866,
                "address": "89/A, Anashwaram, 5th Cross Road, Kodihalli, Bengaluru, Karnataka. 36 m from Vishnuchitna Hostel, Pin-560038 (India)",
                "alarmType": 27,
                "duration": 300,
                "actualDuration": 1059,
                "data": 0,
                "startTimestamp": 1770383182,
                "endTimestamp": 1770384241
            },
            "todaysDrive": {
                "todayKms": 12.06,
                "todayMovementTime": 2254,
                "todayIdleTime": 3793,
                "todayDriveCount": 9
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/live/devices/#/53451?access_token=bd0279e8-3940-4e46-a5df-6a3cd13495c1"
            },
            "fuelLiters": 32.19,
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
