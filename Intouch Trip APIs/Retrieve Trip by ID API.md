[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Retrieve Trip by ID API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Retrieve Trip by ID API` allows users to access complete details of a specific trip using its unique `tripId`. It provides insights into the trip’s status, route, timing, destination, geofences, device location, and associated metadata, making it ideal for real-time tracking, monitoring, and trip analysis. This API is particularly useful for verifying trip completion, analyzing deviations, and integrating precise trip information into fleet management systems or dashboards.

> **Note:** Ensure the trip exists before invoking this API. You can use the [Trip Retrieval API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Trip%20APIs/Trip%20Retrieval%20API.md) to list all trips and obtain the corresponding tripId.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method** 
- GET

## **Input URL**
`https://intouch.mappls.com/iot/api/v2.0/trips/{tripId}`

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
- `200` (OK): The request was successfully processed, and the operation was successful.
- `203` (Invalid Trip ID): The provided Trip ID is either invalid or does not exist in the system.
- `400` (Bad Request): The request contains invalid data or an incorrect data type.
- `401` (Unauthorized): Access to the API is restricted, and the request is not authorized.
- `404` (Not Found): The requested resource (trip) could not be found.

## **Request Parameters**
Parameters marked in **`bold`** are mandatory, and those in *`italics`* are optional:
1. **`tripId`** (string): The unique identifier for the trip you want to fetch.
2. *`polyline`* (boolean): Includes the polyline route of the trip if set to `true`.
3. *`deviceLocation`* (boolean): Returns the last known location details of the device if set to `true`.
4. *`event`* (boolean): Retrieves all the position events associated with the device if set to `true`.
  
 ## **Response Parameters** 
- *`tripId`*(string): the unique identifier of the trip.
- *`deviceId`*(number): The id of the device which is associated with the trip
- *`status`*(integer): Indicates the current status of the trip, i.e. `1` for active trip & `2` for completed trip.
- *`closureType`*(integer): Type of closure.
    - `1`: trip will get closed based on the planned end time
    - `2`: trip will close when the device enters the destination area/geofence
    - `3`: trip will get closed manually by the user.

- *`forceClose`*(boolean): Indicates if true, the trip will be automatically closed as soon as the device gets associated with another trip.
- *`name`* (string): Name of the trip.
- *`polylinePoints`* (object): This is the route polyline. It will be returned for single trip only if polyline query param is set to true in the API.
    - *`coordinates`* (array): A list of latitude and longitude coordinates defining the route of the trip.
        - `example`:
            ```json
            [
                {
                    "lng": 0,
                    "lat": 0
                }
            ]
            ```              
- *`location`*(object): location data of the device. This will be returned only for a single trip when the 'deviceLocation' query param is set to true in the API.
    - *`gpsTime`*(number): gps time of the device.       
    - *`gprsTime`*(number): gprs time of the device.       
    - *`latitude`*(number): latitude of the device.       
    - *`longitude`*(number): longitude of the device.
    - *`address`*(string): last location address of the device.
    - *`status`*(number): movement status of the device
        - `1`: Moving
        - `2`: idle
        - `3`: stopped
        - `4`: towing
        - `5`: No Data
        - `6`: power off (i.e., the device's battery is disconnected from the vehicle battery).
        - `7`: No GPS
        - `12`: Activation Pending (i.e. the device is not yet active and is yet to send the first ping).  
- *`positionEvents`* (array): Position events data of the device. This will be returned only for a single trip when the event query param is set to `l` in the API.
    - *`timestamp`*(number): The timestamp of the position event.
    - *`longitude`*(number): Longitude of the event.
    - *`latitude`*(number): Latitude of the event.
- *`destination`*(object): This will only get returned in case this object was explicitly defined while creating a trip.
    - *`geometry`* (object): This is standard geo json format.
       - *`type`* (string): supports the following geometry types - Point, Polygon.
       -  *`coordinates`*(array): Latitude and longitude of the destination point.
    - *`radius`*(number): Radius of the point.
    - *`plannedTime`*(number): planned timestamp at which device reach the destination.
    - *`name`* (string): Name of the geofence point.
    - *`arrivalTime`*(number): actual timestamp at which device reach the destination.
    - *`departureTime`*(number): departure timestamp at which device leaves the destination.
    - *`address`*(string): address of the destination point.
    - *`time`*(number): planned timestamp taken to reach the destination from previous point.
    - *`distance`*(number): planned distance taken to reach the destination from previous point.
    - *`pointName`*(string): name given to the destination point..
    - *`jobId`*(string): unique ID of the job.
    - *`links`*(string): Contains URLs related to the destination.
        - *`embedUrl`*(string): embeddable URL of the job or trip widget depending on within which object the link object is present. (type maybe `job` or `trip`).
    - *`metadata`*(object): will be returned only if it was mentioned while creating a trip.
       - `myattribute`(string): Dummy meta data value. this can be any key-value data pair.
- *`geofences`*(array):A trip may have various points. This will only get returned in case the these geofence points were explicitly mentioned while creating a trip
    - This will only get returned in case this object was explicitly defined while creating a trip.
    - *`geometry`*(object): This is standard geo json format.
        - `type`(string): supports the following geometry types - Point, Polygon.
        - `coordinates`(number): Longitude and latitude of the destination point.
- *`radius`*(number): radius of the point.
- *`plannedTime`*(number): planned timestamp at which device reach the destination.
- *`name`*(string): name of the geofence point.
- *`arrivalTime`*(number): actual timestamp at which device reach the destination.
- *`departureTime`*(number): departure timestamp at which device leaves the destination.
- *`address`*(string): address of the destination point.
- *`time`*(number): planned timestamp taken to reach the destination from previous point.
- *`distance`*(number): planned distance taken to reach the destination from previous point.
-*`pointName`*(string): name given to the destination point.
- *`jobId`*(string): Unique ID of the Job.
- *`links`*(string): Contains URLs related to the destination.
        - *`embedUrl`*(string): embeddable URL of the job or trip widget depending on within which object the link object is present. (type maybe `job` or `trip`).
    - *`metadata`*(object): will be returned only if it was mentioned while creating a trip.
       - `myattribute`(string): Dummy meta data value. this can be any key-value data pair.
- *`start`*(object): This will only get returned in case this object was explicitly defined while creating a trip.
    - *`geometry`*(string): This is standard geo json format.
          - `type`(string): supports the following geometry types - Point, Polygon.
          - `coordinates`(number): Latitude and longitude of the destination point.
    - *`radius`*(number): radius of the point.
    - *`plannedTime`*(number): planned timestamp at which device reach the destination.
    - *`name`*(string): name of the geofence point.
    - *`arrivalTime`*(number): actual timestamp at which device reach the destination.
    - *`departureTime`*(number): departure timestamp at which device leaves the destination.
    - *`address`*(string): address of the destination point.
    - *`time`*(number): planned timestamp taken to reach the destination from previous point.
    - *`distance`*(number): planned distance taken to reach the destination from previous point.
    -*`pointName`*(string): name given to the destination point.
    - *`jobId`*(string): Unique ID of the job.
    - *`links`*(string): Contains URLs related to the destination.
      - *`embedUrl`*(string): embeddable URL of the job or trip widget depending on within which object the link object is present. (type maybe `job` or `trip`).
      - *`metadata`*(object): will be returned only if it was mentioned while creating a trip.
       - `myattribute`(string): Dummy meta data value. this can be any key-value data pair.
- *`summary`*(object): Provides a summary of the trip’s overall details.
    - *`startedOn`*(number): Timestamp when the trip started.
    - *`duration`*(number): The actual duration time (in seconds) of the trip.
    - *`distance`*(number): The actual distance (in meters) covered in the trip.
    -*`endedOn`*(number): The actual end timestamp of the trip.
    - *`delayedBy`*(number): The actual timestamp by which the trip got delayed.
    - *`plannedEndTime`*(number): The planned end timestamp of the trip.
    - *`plannedStartTime`*(number): The planned start timestamp of the trip.
    - *`plannedDuration`*(number): The planned duration time (in seconds) of the trip.
    - *`plannedDistance`*(number): The planned distance (in meters) of the trip.

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/v2.0/trips/67932d2ee1b7d91042866e25?polyline=true&deviceLocation=true&event=true' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{
    "data": {
        "tripId": "67932d2ee1b7d91042866e25",
        "deviceId": 10647019,
        "deviceName": "Vandana-test",
        "destination": {
            "geometry": {
                "type": "Point",
                "coordinates": [
                    77.234,
                    28.456
                ]
            },
            "radius": 100,
            "plannedTime": 1591891234,
            "metadata": {
                "myattribute": "sample text"
            },
            "address": "unnamed road, asola, new delhi, delhi. pin-110074 (india)",
            "time": 3597,
            "distance": 23.1108,
            "name": "string"
        },
        "geofences": [
            {
                "geometry": {
                    "type": "Polygon",
                    "coordinates": [
                        [
                            [77.26823336070498,28.55580522473032],
                            [77.27371718795376,28.54945215626816],
                            [77.26906334536983,28.545806779996497],
                            [77.26784801068226,28.54570262453474],
                            [77.26429093354909,28.54424443725499],
                            [77.26212704495794,28.54929592844502],
                            [77.26570430916473,28.55509008319774],
                            [77.26831283239613,28.555845140648714],
                            [77.26823336070498,28.55580522473032]
                        ]
                    ]
                },
                "radius": 100,
                "plannedTime": 1737698606,
                "metadata": {
                    "myattribute": "sample text"
                },
                "address": "60, unnamed road, okhla industrial estate phase 3, new delhi, delhi. 17 m from precision pipes and profile company ltd, pin-110020 (india)",
                "time": 0,
                "distance": 0.0,
                "name": "string",
                "status": 0,
                "jobId": "67932d2ee1b7d91042866e26",
                "links": {
                    "embedUrl": "https://intouch.mapmyindia.com/widget/jobs/#/67932d2ee1b7d91042866e26?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
                }
            }
        ],
        "status": 1,
        "location": {
            "id": 10647019,
            "gpsTime": 1737690147,
            "gprsTime": 1737690150,
            "latitude": 28.5510184,
            "longitude": 77.2688553,
            "heading": 258.0,
            "speedKph": 1.0,
            "address": "237, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 19 m from Heera Cigarette Shop, Pin-110020 (India)",
            "name": "Vandana-test",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    77.2688553,
                    28.5510184
                ]
            },
            "status": 5
        },
        "metadata": {
            "myattribute": "sample text"
        },
        "positionEvents": [],
        "closureType": 1,
        "forceClose": true,
        "name": "Vandana-test",
        "summary": {
            "startedOn": null,
            "duration": null,
            "distance": null,
            "endedOn": null,
            "delayedBy": null,
            "plannedEndTime": 1591891234,
            "plannedStartTime": 1737698606,
            "plannedDuration": 3597,
            "plannedDistance": 23.110799999999998
        },
        "start": {
            "plannedTime": 1737698606
        },
        "links": {
            "embedUrl": "https://intouch.mapmyindia.com/widget/trips/#/67932d2ee1b7d91042866e25?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
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


