
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Get Device Live Data

## **Introduction**

The *`Get Device Live Data API`* provides accurate, real-time location and related *data of vehicles*, *assets*, and people using *connected devices*, *sensors*, or *mobiles*. This API enables your app to have real-time visibility of tracked objects, offering not only location information but additional valuable metrics. This API is ideal for various use cases, including transport logistics and personnel tracking services, and can be used in both web and mobile platforms.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
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

1. *`id`*(Integer): This is the device's ID, a non-mandatory parameter. If not passed then by default the API will return the list of all active devices in the account.

2. *`includeInActive`*(Boolean): Non mandatory boolean field. If this field is not sent then by default API response will send all active devices. If `true` then API reponse will have inactive devices along with active devices. If `false` then API will return only active devices.

3. *`ignoreBeacon`*(Boolean): Non mandatory field. If set to true then API will return all devices except those whose device type is beacon(mobile).

4. *`state`*(Number): Non mandatory field. Input timestamp in this field to fetch only those live locations of devices which have come after the input timestamp. If `state` is sent then by default only active devices will be fetched irrespective of the status of `includeInActive` attribute.

## **Response Parameter**

- **`DeviceData`**
    - **`id`**(integer): Unique identifier for the device.

    - **`active`**(string): Indicates if the device is active.
         - **`Enum Value`s**: [ true, false ]

    - **`status`**(number): Represents the device's movement status:
         - `1` : Moving
         - `2` : Idle i.e. ignition is on and speed <= 7km/hr
         - `3` : Stopped i.e. engine is off
         - `4` : Towing i.e. ignition is off, but vehicle speed
         - `5` : No data i.e. no communication of device with intouch server or no    GPRS signal
         - `6` : Power off
         - `7` : No GPS i.e. satellite count is less than 4
         - `8` : On trip i.e. device is currently on an active trip
         - `9` : Free vehicle i.e. device is not on any active trip

    - **vehicleBattery**(number): Battery voltage of the vehicle.

- **`location`**:
    - **`gpsTime`**(number): GPS timestamp.
    
    - **`gprsTime`**(number): GPRS timestamp.

    - **`latitude`**(number): Device's latitude.
        
    - **`longitude`**(number):  Device's longitude.

    - **`address`**(string): Location address of the device.
      
    - **`altitude`**(number): Device altitude in meters.  
      
    - **`heading`**(number): Direction of movement in degrees.
       
    - **`speedKph`**(number): Speed in kilometers per hour.
        
    - **`odometer`**(number): Total distance covered by the vehicle.
      
- **`deviceDetails`**:
    - **`name`**(string): Name of the Device.

    - **`registrationNumber`**(string): Vehicle registration number.

    - **`deviceType`**(string): Type of device.
    - **`Enum Values`**: `[ car, truck, bus, bike, tractor, JCB, excavator ]`

-  **``AlertObject``**
   - **`deviceId`**(number): Device ID that generated the alert(Will come only in case of /alarmLog GET API response).

   - **`timestamp`**(number): Time at which the alert got generated.

   - **`latitude`**(number): Latitude at the time of alert.
    
   - **`longitude`**(number): Longitude at the time of alert.  
    
   - **`address`**(string): Location address at which the alarm got generated.
   
   - **`alarmType`**(integer): Type of alarm to create. Following are the alarm types & their corresponding IDs:
       - `IGNITION` : `21`
       - `OVERSPEED` : `22`
       - `UNPLUGGED` : `23`
       - `PANIC` : `24`
       - `GEOFENCE` : `26`
       - `STOPPAGE` : `27`
       - `IDLE` : `28`
       - `TOWING` : `29`
       - `GPRS CONNECTIVITY` : `126`
       - `VEHICLE BATTERY` : `129, MILEAGE: 133`
       - `GPS CONNECTIVITY` : `146`
       - `DISTANCE COVERED` : `151`
       - `INTERNAL BATTERY VOLTAGE` : `161`.

   - **`limit`**(integer): Alarm limit as set in the config. For example, if an overspeed alarm set on limit of 44 km/hr in the alarm config setting, then this attribute will return 44 km/hr. 
  
   - **`duration`**(integer): Alarm duration limit as set in the alarm config section. For example, if duration of overspeed alarm is set as 20 secs, then the alarm will generate when the vehicle overspeeds for a duration of 20 secs. 
   
   - **`actualLimit`**(integer): The actual data received from the device at that particular moment when the alarm got generated. 

   - **`actualDuration`**(integer): Actual duration for which the device breached the alarm config limit. 

   - **`severity`**(integer): Indicates the level of seriousness of an alarm, where `0` is low severity and `1` is high severity, helping classify how critical the alarm event is.

   - **`data`**:(integer) Describes the state of the alarm. 
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

   - **`geofenceId`**(number): This is the ID of the geofence for which the alarm got generated. This will come only when the 'type' field return 26 i,e geofence. 
-  **`canInfo`**
   - **`calcEngineVal`**(integer) 

   - **`greenDriveType`**(string): Driving behavior type.  Possible values:  
       - `HA` : Harsh Acceleration  
       - `HB` : Harsh Braking  
       - `HC` : Harsh Cornering.

   - **`canTimestamp`**(number): Exact time at which the CAN data got generated by the device. 
  
   - **`coolantTemp`**(number): Coolant temperature in degrees Celsius. 
 
   - **`engineRPM`**(integer): Revolutions per minute of the engine. 
    
   - **`accelPedal`**(number): This is accelerator pedal value as a percentage. 
   
   - **`parkBrake`**(number): This is parking break. 
       - `0` : means parking break is disengaged
       - `1` : means parking break is engaged.   
  
   - **`breakPedal`**(number): Indicates brake pedal status: `1` means break pedal is engaged & `0` means break pedal is disengaged. 
   
   - **`fuelLevel`**(integer): Fuel level in liters. 
  
   - **`driverDoor`**(number): Driver door status:1 means door is open & 0 means door is closed.  

   - **`headLights`**(number): Headlights status:  
       - `0` : OFF  
       - `1` : ON 

   - **`blinker`**: `number` Blinker status:  
       - `0` : OFF  
       - `1` : ON   
  
   - **`gearState`**(number): Gear state:  
       - `0` : Neutral  
       - `1` : Drive  
       - `2` : Sports  
       - `3` : Reverse.  

   - **`intakeAirTemp`**(number): This is the intake air temperature of the engine in degrees Celsius.   

   - **`intakeabsolutePress`**(number): This is the intake absolute pressure of the engine. It is defined in Pa(Pascal). 

   - **`ac`**(integer): Air conditioner status:  
       - `0` : OFF  
       - `1` : ON 

   - **`fuelConsAVG`**(integer): Fuel constant average. 

- **`deviceFaults`**
    - **`code`**(integer):Fault code. 

    - **`timestamp`**(number): Timestamp when the fault was detected. 

    - **`status`**(integer): Describes the status of the fault which was detected.
        - `0` : Open  
        - `1` : Closed 

    - **`closedOn`**(number): Timestamp when the fault was resolved.

- **`currentGeofence`**(number): Array of geofence IDs currently associated with the device.

- **`todaysDrive`**
    - **`todayKms`**(number): Total kilometers driven today.   

    - **`todayMovementTime`**(number): Total movement time today in seconds.

    - **`todayIdleTime`**(number): Total idle time today in seconds.  

    - **`todayDriveCount`**(integer): Number of drives completed today.

-  **`externalSensorObject`**
      - **`sensorId`**(string): Identifier for the external sensor.

      - **`temperature`**(number): Temperature reading from the external sensor in degrees Celsius.

- **`fuelLiters`**(number): Fuel level in liters, Value is calculated using external fuel sensor.


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
