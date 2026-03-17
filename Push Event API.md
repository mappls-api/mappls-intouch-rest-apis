
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Push Event API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

The `Push Event API` allows customers to ingest real-time telemetry data from third-party service providers directly into Intouch, enabling a unified and centralized fleet view.
This API is designed for organizations that operate devices managed by multiple vendors and want to consolidate all fleet data into a single monitoring platform. Customers can push event-driven data from external tracking systems, IoT platforms, or telematics providers into Intouch for seamless aggregation and visualization.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method** 
- POST

## **Input URL**
> https://intouch.mappls.com/iot/api/events/pushData/

## Response Type
- JSON

## **Response Codes (HTTP Status Codes)**
| **HTTP Status Code** | **Reason** | **Response Model** |
| --- | --- | --- |
| 202 | Accepted | |
| 400 | Bad Request  | **{“error”:”Error Type”}** |
| 401 | Unauthorized | |
| 403 | Forbidden | |
| 404 | Not Found | |
| 500 | Internal Server Error | |


## **Header Parameter:**

| **Content-Type** | **Data Type** | **Application/JSON** |
| --- | --- | --- |
| `trackingCode` | String | Unique identifier of the device. |


## **Mandatory Fields**

| **S.No** | **Attributes** | **Description** | **Data Type** |
| --- | --- | --- | --- |
| 1 | **`timestamp`** | Time stamp of the time when the data packet was generated on the device. | Long |
| 2 | **`latitude`** | Latitude from the GNSS | Double |
| 3 | **`longitude`** | Longitude from the GNSS | Double |
| 4 | **`speed`** | GPS/ CAN speed from the device. Required for Trip processing. In Kmph | Double |
| 5 | **`numberOfSatellites`** | Number of satellites used for tracking which are currently in the visibility range of the tracker. | Integer |
| 6 | **`heading`** | GPS Heading or Gyro/ Magnetometer heading from the hardware. Better visualization. In degrees | Double |
| 7 | **`analogInput1`** | External Power Voltage of the device in volts | Double |


## **Optional fields for Mobile**

| **S.no** | **Attribute**  | **Description** | **Data Type** |
| --- | --- | --- | --- |
| 1  | *`deviceId`*  | ID of the device  | Required String  |
| 2 | *`token`* | Token generated | Required String |
| 3 | *`imei`* | IMEI of the device | Required String |
| 4 | *`simNo`* | SIM number of the device | Required String |
| 5 | *`batteryLevel`* | Battery level of the device | Optional Integer |
| 6 | *`gpsLat`* | Latitude Value | Optional Double |
| 7 | *`gpsLong`* | Longitude Value| Optional Double|
| 8 | *`imei2`* | IMEI (if device has multiple SIM slots)| Optional String|
| 9 | *`powerState`* | State of power on device (ON/OFF)| Optional Integer|
| 10 | *`sos`* | Panic button pressed| Optional Integer|
| 11 | *`package`* | Package name | Required String |
| 12 | *`phone`* | Phone number of the developer | Required String |
| 13 | *`version`* | Version of application | Optional String |
| 14 | *`deviceOs`* | Operating System of the device | Optional String |
| 15 | *`appVersion`* | Version of the app | Optional String |
| 16 | *`displayId`* | Display ID of device | Required String |
| 17 | *`deviceModel`* | Model of the device | Optional String |
| 18 | *`language`* | Language preference of developer | Optional String |
| 19 | *`lastUsed`* | Last used timestamp | Optional String |
| 20 | *`createdDate`* | Date of device creation | Optional String |
| 21 | *`updatedDate`* | Last update date | Optional String |
| 22 | *`ipAddress`* | Device's current IP address | Optional String |
| 23 | *`deviceStatus`* | Status of the device (Online/Offline) | Optional String |
| 24 | *`message`* | Message to be shown in app | Optional String |
| 25 | *`plan`* | developer's current plan | Optional String |


## **Optional fields for Vehicles**

| **S.no** | **Attribute** | **Description** | **Data Type** |
| --- | --- | --- | --- |
| 1 | *`digitalInput2`* | Any additional digital input | Optional Integer |
| 2 | *`digitalOutput1`* | Immobilizer status whether '1' or '0' | Optional Integer |
| 3 | *`analogInput1`* | Main power of vehicle | Optional Double |
| 4 | *`analogInput2`* |  | Optional Double |
| 5 | *`analogInput3`* |  | Optional Double |
| 6 | *`analogInput4`*  |  | Optional Double |
| 7 | *`digitalOutput1`* | Mobilization status | Optional Integer |
| 8 | *`digitalOutput2`* |  | Optional Integer |
| 9 | *`digitalOutput3`* |  | Optional Integer |
| 10 | *`digitalOutput4`* |  | Optional Integer |
| 11 | *`detectedEvent`* | Detected Event | Optional Integer |
| 12 | *`dallasId`* | Used live RFID Accessorize Id | Optional String |
| 13 | *`altitude`* |  | Optional Double |
| 14 | *`fuelLiters`* | Fuel in Liters | Optional Double |
| 15 | *`powerSupplyVoltage`* | Vehicle Power volt | Optional Double |
| 16 | *`internalBatteryVoltage`* | Device internal battery volt | Optional Double |
| 17 | *`internalBatteryLevel`* | Device internal battery in percentage | Optional Integer |
| 18 | *`pulseInput`* |  | Optional Integer |
| 19 | *`enginerpm`* | Engine rpm value  | Optional Integer |
| 20 | *`temperatureSensor`* |  | Optional Integer |
| 21 | *`power`* | Plugged-1 / unplugged-0 | Optional Integer |
| 22 | *`movementSensor`* | Movement in device | Optional Integer |
| 23 | *`gsmlevel`* | SIM signal level, vary from 0-31 | Optional Integer |
| 24 | *`frequencyInput`* | No device Data | Optional Integer |
| 25 | *`accuracyLevel`* | No device Data | Optional Integer |
| 26 | *`accelerometerX`* | Device Orientation Value in X | Optional Double |
| 27 | *`accelerometerY`*  | Device Orientation Value in Y | Optional Double |
| 28 | *`accelerometerZ`* | Device Orientation Value in Z | Optional Double |
| 29 | *`maxAccelX`* | At the time of Harsh Breaking | Optional Double |
| 30 | *`maxAccelY`* |  | Optional Double |
| 31 | *`maxAccelZ`* |  | Optional Double |
| 32 | *`locationSource`* | GPS-0/1 - Need to confirm | Optional Integer |
| 33 | *`accuracy`* | No device Data | Optional Integer |
| 34 | *`serviceProvider`* | Airtel / Voda Used only in SIM | Optional String |
| 35 | *`wifissid`* | No device Data | Optional String |
| 36 | *`wifiapn`* | No device Data | Optional Integer |
| 37 | *`gpsSpeed`* | GPS Speed | Optional Double |
| 38 | *`canSpeed`* | CAN Speed | Optional Double |
| 39 | *`dtcCount`* | Fault code count (CAN DATA) | Optional Integer |
| 40 | *`dtcDistance`* | Distance after Fault code occurs | Optional Integer |
| 41 | *`coolantTemp`* | CAN DATA (Temperature) | Optional Integer |
| 42 | *`greenDriveType`* | HA/HB/HC Type- 1/2/3 resp... | Optional Integer |
| 43 | *`greenDriveValue`* | Value for HA/HB/HC | Optional Integer |
| 44 | *`unplugged`* | Device unplugged from external Battery source | Optional Integer |
| 45 | *`sos`* | Panic | Optional Integer |
| 46 | *`version`* | Firmware version | Optional String |
| 47 | *`calcEngineVal`* | Calculated Engine Load Value (CAN Data) | Optional Integer |
| 48 | *`shortTermFuel`* | CAN Data | Optional Integer |
| 49 | *`fuelPressure`* | CAN Data | Optional Integer |
| 50 | *`intakeabsolutePress`* | CAN Data | Optional Integer |
| 51 | *`timingAdv`* | CAN Data | Optional Integer |
| 52 | *`airFlowRate`* | Same as massAirFlow(CAN Data) | Optional Double |
| 53 | *`runTimeEngileStart`* | Same as engOnTime, engRunTime (CAN Data) | Optional Double |
| 54 | *`fuelRailPressure`* | CAN data | Optional Integer |
| 55 | *`dirFuelRailPress`* | CAN data | Optional Integer |
| 56 | *`cmdEGR`* | CAN data | Optional Integer |
| 57 | *`egrError`* | CAN data | Optional Integer |
| 58 | *`disTravelCodes`* | Same as dtcDistance | Integer |
| 59 | *`barometricPressure`* | CAN data | Integer |
| 60 | *`ctrlModleVol`* | Control Module Voltage | Integer |
| 61 | *`absLoadVal`* | Absolute load value- Helps to measure fuel efficiency | Integer |
| 62 | *`ambientAirTemp`* | CAN data | Integer |
| 63 | *`timeRunMil`* | Runtime time after dtc code occurred | Integer |
| 64 | *`timetroubleCodes`* | Time | Integer |
| 65 | *`absFuelRailPress`* | ABS Fuel rail pressure | Integer |
| 66 | *`hybridBattryRemain`* | Hybrid Battery Remaining | Integer |
| 67 | *`engineOilTemp`* | Temp of engine oil | Intege |
| 68 | *`fuelInjTime`* | Fuel injection time | Integer |
| 69 | *`engineFuelRate`* | CAN data | Integer |
| 70 | *`fuelConsAVG`* | Avg fuel consumption | Integer |
| 71 | *`gpsOdometer`* | Odometer value calculated from GPS | Double |
| 72 | *`deviceOdometer`* | Device Odometer | Double |
| 73 | *`canOdometer`* | CAN odometer | Double |
| 74 | *`accelPedal`* | Pressed percentage of Accelerator pedal | Double |
| 75 | *`driverSeatBelt`* | Driver Seat Belt on off | Double |
| 76 | *`headLights`* | Headlights on off | Double |
| 77 | *`parkBrake`* | Hand brake on off | Double |
| 78 | *`canAc`* | CAN data for AC ON/OFF | Double |
| 79 | *`intakeAirTemp`* | CAN data | Double |
| 80 | *`realGrndVehiSpeed`* | Speed of vehicle in centimeter per speed | Double |
| 81 | *`blinker`* | Parking light on off-0- Off 1- Left 2- Right 3- Both  | Double |
| 82 | *`breakPedal`* | Is pressed brake pedal pressed or not | Double |
| 83 | *`driverDoor`* | Open or Closed driver door | Double |
| 84 | *`hazardLights`* | Parking light on off | Double |
| 85 | *`highBeam`* | High Beam is on off | Double |
| 86 | *`dPFLed`* | No Device Data | Double |
| 87 | *`engIngectorLed`* | Engine injector Led (CAN Data) | Double |
| 88 | *`checkEngLed`* | MIL light on off (MIL Means Malfunction light) | Double |
| 89 | *`oilLedStatus`* | In trucks CAN data | Double |
| 90 | *`tilt`* | Position of device if tilt | Integer |
| 91 | *`SOC`* | Status of charge (Electric cars) | Double |
| 92 | *`fullCapacity`* | Full capacity of charge/ max level developer can charge | Double |
| 93 | *`battryCurrent`* | Current value coming from battery | Double |
| 94 | *`stackVolt`* | CAN data for electric vehicle () | Double |
| 95 | *`lowestCelVolt`* | Lowest cell voltage from all cell of battery | Double |
| 96 | *`highestCelVolt`* | Highest cell voltage from all cell | Double |
| 97 | *`lowestTemp`* | Lowest cell temp from all cell | Double |
| 98 | *`highestTemp`* | Highest cell temp from all cell | Double |
| 99 | *`heatSinkTemp`* | Temp of heat sink of battery | Double |
| 100 | *`leftCtrlNextServiceErr`* | CAN data for electric vehicle | String |
| 101 | *`logErr`* | CAN data for electric vehicle | String |
| 102 | *`nextServiceDate`* | Next service date | String  |
| 103 | *`driverName`* | Driver Name | String |
| 104 | *`stopFor`* | Where to stop | String |
| 105 | *`remarks`* | Remarks | String |

## **Sample curl Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/events/pushData/' \
--header 'Accept: application/json' \
--header 'Authorization: bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'trackingCode: 355412119692406' \
--header 'Content-Type: application/json' \
--header 'Cookie: HttpOnly; HttpOnly' \
--data '[
    {
        "analogInput1": 0,
        "analogInput2": 0,
        "gsmlevel": 0,
        "heading": 0,
        "ignition": 0,
        "panic": 0,
        "ac": 0,
        "latitude": 0,
        "longitude": 0,
        "numberOfSatellites": 0,
        "timestamp": 0
    }
]'
```

> **Note:** API supports multiple packets of the same device in a single request.

## **Response Parameters**
The response of this API would be empty. Success would be denoted by the response codes and error would be denoted with the response codes while information on what went wrong with the request in-case of a 400: bad request would be a part of the response headers message.





<br>


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

