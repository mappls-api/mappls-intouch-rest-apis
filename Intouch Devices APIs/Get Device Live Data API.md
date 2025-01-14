
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Get Device Live Data

## **Introduction**

The *`Get Device Live Data API`* provides accurate, real-time location and related *data of vehicles*, *assets*, and people using *connected devices*, *sensors*, or *mobiles*. This API enables your app to have real-time visibility of tracked objects, offering not only location information but additional valuable metrics. This API is ideal for various use cases, including transport logistics and personnel tracking services, and can be used in both web and mobile platforms.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- `200(OK)`: The operation was successful.

- `203(Device Not Found)`: The specified device could not be located.

- `400(Bad Request)`: The request is invalid due to incorrect device ID or data type.
- `401(Unauthorized)`: The request is forbidden. Authentication or valid authorization is required.
- `404(Not Found)`: The requested URL could not be found on the server.

## **Response Header**
-  ***content-type***: *`application/json;charset=UTF-8`*

## **Request Parameters**

1. **`id`**(Integer): This is the device's ID, a non-mandatory parameter. If not passed then by default the API will return the list of all active devices in the account.

2. **`includeInActive`**(Boolean): Non mandatory boolean field. If this field is not sent then by default API response will send all active devices. If `true` then API reponse will have inactive devices along with active devices. If `false` then API will return only active devices

3. **`ignoreBeacon`**(Boolean): INon mandatory field. If set to true then API will return all devices except those whose device type is beacon(mobile).

4. **`state`**(Number): Non mandatory field. Input timestamp in this field to fetch only those live locations of devices which have come after the input timestamp. If `state` is sent then by default only active devices will be fetched irrespective of the status of `includeInActive` attribute.

## **Response Parameter**

- **`DeviceData`**
    - **`id`**(integer)($int64): Unique identifier for the device.

    - **`active`**(string): Indicates if the device is active. `Example: true`  
         - **`Enum Value`s**: [ true, false ]

    - **`status`**(number) : Represents the device's movement status:
         - `1`: moving
         - `2` : idle i.e. ignition is on and speed <= 7km/hr
         - `3` : stopped i.e. engine is off
         - `4` : towing i.e. ignition is off, but vehicle speed
         - `5` : no data i.e. no communication of device with intouch server or no    GPRS signal
         - `6` : power off
         - `7` : no gps i.e. satellite count is less than 4
         - `8` : on trip i.e. device is currently on an active trip
         - `9` : free vehicle i.e. device is not on any active trip

    - **vehicleBattery**(number): Battery voltage of the vehicle. `Example: 13568.98`

- **`location`**
    - **`gpsTime`**(number): GPS timestamp. Example: `1574736922`  
    
    - **`gprsTime`**(number): GPRS timestamp. `Example: 1574736922` 

    - **`latitude`**: `number` Device's latitude. `Example: 28.551255163434`  
        

    - **`longitude`**: `number`  Device's longitude. `Example: 77.2687`      

    - **`address`**: `string` Location address of the device. `Example: "244, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 2 m from Usha Exim Pvt Ltd pin-110020"`  
      

    - **`altitude`** (number): Device altitude in meters. `Example: 234`   
      
    - **`heading`** (number): Direction of movement in degrees.` Example: 196.868` 
       
    - **`speedKph`** (number): Speed in kilometers per hour. `Example: 27.85`  
        
    - **`odometer`**(number): Total distance covered by the vehicle. `Example: 12548.22`  
      
- **`deviceDetails`**
    - **`name`**: `string` Device name.Example: `DL3CCM8097x

    - **`registrationNumber`**: `string`  Vehicle registration number. `Example: DL3CCM8097`  

    - **`deviceType`**(string): Type of device. `Example: car`  
    - **`Enum Values`**: `[ car, truck, bus, bike, tractor, JCB, excavator ]`

-  **``AlertObject``**
   - **`deviceId`**(number): Device ID that generated the alert(Will come only in case of /alarmLog GET API response). `Example: 8989`

   - **`timestamp`**(number): Time at which the alert got generated `Example: 1577589789`  

   - **`latitude`**(number): Latitude at the time of alert. `Example: 28.550962381896`  
    
   - **`longitude`**(number): Longitude at the time of alert. `Example: 77.26890675033`  
    
   - **`address`**(string): Location address at which the alarm got generated. `Example: "237, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 19 m from Wipro BPO Corporate Office pin-110020"`
   
   - **`alarmType`**(integer): Type of alarm to create. Following are the alarm types & their corresponding IDs. 
IGNITION: `21`, OVERSPEED: `22`, UNPLUGGED: `23`, PANIC: `24`, GEOFENCE: `26`, STOPPAGE: `27`, IDLE: `28`, TOWING: `29`, GPRS CONNECTIVITY: `126`, VEHICLE BATTERY: `129, MILEAGE: 133`, GPS CONNECTIVITY: `146`, DISTANCE COVERED: `151`, INTERNAL BATTERY VOLTAGE:`161`.  `Example: 28`

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
   
   - **`parkBrake`**(number): This is parking break. `0` means parking break is disengaged & `1` means parking break is engaged. `Example: 0`  
  
   - **`breakPedal`**(number): Indicates brake pedal status: `1` means break pedal is engaged & `0` means break pedal is disengaged. `Example: 0`
   
   - **`fuelLevel`**(integer): Fuel level in liters. `Example: 14` 
  
   - **`driverDoor`**(number): Driver door status:1 means door is open & 0 means door is closed. `Example: 0` 

   - **`headLights`**(number): Headlights status:  
       - `0`: OFF  
       - `1`: ON   `Example: 1`

   - **`blinker`**: `number` Blinker status:  
       - `0`: OFF  
       - `1`: ON   `Example: 0`  
  
   - **`gearState`**(number): Gear state:  
       - `0`: Neutral  
       - `1`: Drive  
       - `2`: Sports  
       - `3`: Reverse.  ` Example: 0`
       

   - **`intakeAirTemp`**(number): This is the intake air temperature of the engine in degrees Celsius. `Example: 62`  

   - **`intakeabsolutePress`**(number): This is the intake absolute pressure of the engine. It is defined in Pa(Pascal). `Example: 42`

   - **`ac`**(integer): Air conditioner status:  
       - `0`: OFF  
       - `1`: ON  `Example: 0`

   - **`fuelConsAVG`**(integer): Fuel constant average. `Example: 99`  

- **`deviceFaults`**
    - **`code`**(integer):Fault code. `Example: `1001`

    - **`timestamp`**(number): Timestamp when the fault was detected. `Example: 787654544` 

    - **`status`**(integer): Describes the status of the fault which was detected.
        - `0`: Open  
        - `1`: Closed  Example: `0`

    - **`closedOn`**(number): Timestamp when the fault was resolved. `Example: 556567872`  


- **`currentGeofence`**(number): Array of geofence IDs currently associated with the device.

- **`todaysDrive`**
    - **`todayKms`**(number): Total kilometers driven today.  
      Example: `55.67`  
      

    - **`todayMovementTime`**(number): Total movement time today in seconds.  
      Example: `67654`  
      

    - **`todayIdleTime`**(number): Total idle time today in seconds.  
      Example: `4444`  

    - **`todayDriveCount`**(integer): Number of drives completed today. `Example: 5`  

-  **`externalSensorObject`**
      - **`sensorId`**(string): Identifier for the external sensor. `Example: 1`

      - **`temperature`**(number): Temperature reading from the external sensor in degrees Celsius. `Example: 28.32`

- **`fuelLiters`**(number): Fuel level in liters, Value is calculated using external fuel sensor. `Example: 78.8`


## **Sample Input**

```
https://intouch.mappls.com/iot/api/devices?id=10647019&includeInActive=false&ignoreBeacon=false
```
## **Sample Output**

```json
{
    "data": [
        {
            "id": 10647019,
            "active": true,
            "status": 3,
            "location": {
                "gpsTime": 1735187301,
                "gprsTime": 1735187304,
                "latitude": 28.5507985,
                "longitude": 77.2689116,
                "altitude": 193.90000915527344,
                "heading": 219.0,
                "speedKph": 0.0,
                "address": "237, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 10 m from MapmyIndia Head Office New Delhi, Pin-110020 (India)",
                "gpsSignal": 51
            },
            "deviceDetails": {
                "name": "Vandana-test ",
                "registrationNumber": "d0369b5adb381a23",
                "deviceType": "Person",
                "trackingCode": "84829FA7405F25D8B815FD338AADE6A2D330E2AF83D7FCA0",
                "internalBatteryLevel": 69
            },
            "canInfo": {
                "canTimestamp": 1735187301,
                "chargingStatus": 0,
                "ignition": 0
            },
            "todaysDrive": {},
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/live/devices/#/10647019?access_token=f4b8474f-7d88-4271-bead-7a55b1854141"
            },
            "dinputs": {
                "1": 0,
                "2": 0,
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




<div align="center">@ Copyright 2025 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
