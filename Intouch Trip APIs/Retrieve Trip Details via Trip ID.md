[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Retrieve Trip Details via Trip ID

## **Introduction**

*`Retrieve Trip Details via Trip ID API`* allows users to access detailed information about *`a specific trip`* using its unique trip ID. It provides insights into the trip’s status, location, route, and associated metadata, making it useful for real-time tracking and trip analysis.


## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL:**

 > https://intouch.mappls.com/iot/api/v2.0/trips/{id}

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- 200 `OK` - The request was successfully processed, and the operation was successful.
- 203 `Invalid ID` - The provided Trip ID is either invalid or does not exist in the system.
- 400 `Bad Request` - The request contains invalid data or an incorrect data type.
- 401 `Unauthorized` - Access to the API is restricted, and the request is not authorized.
- 404 `URL Not Found` - The requested resource could not be located on the server.

## **Request Parameters**

The **`“bold”`** one’s are mandatory, and the *`“italic”`* one’s are optional.

1. **`id`** (string):Represents the unique identifier of the trip you want to fetch.
2. *`polyline`* (boolean): Includes the entire polyline route of the trip if set to true.
3. *`deviceLocation`* (boolean): Returns the last known location details of the device if set to true.
4. *`event`* (boolean): Retrieves all the position events associated with the device if set to true.
  
 ## **Response Parameters** 

- *`tripId`*(string): the unique identifier of the trip. `Example: 5ef5a9e98a92df3a4a894db0`

- *`deviceId`*(number): The id of the device which is associated with the trip

- *`status`*(integer): Indicates the current status of the trip, i.e. 1 for active trip & 2 for completed trip. `Example: 1`

- *`closureType`*(integer): Type of closure. `1` - trip will get closed based on the planned end time, `2` - trip will close when the device enters the destination area/geofence, and `3` - trip will get closed manually by the user. `Example: 1`

- *`forceClose`*(boolean):-Indicates if true then trip will get automatically closed as soon as the device gets associated with another trip. `Example: false`

- *`name`* (string): Name of the trip `Example: my trip`

- *`polylinePoints`*(object): This is the route polyline. It Will get returned for single trip only if polyline query param is set to true in the API.
    - *`coordinates`*(array): A list of latitude and longitude coordinates defining the route of the trip.
        - `example`:  [
                          {
                            "lng": 0,
                            "lat": 0
                          }
                        ]          
          
- *`location`*(object): location data of the device. This will get returned only for a single trip when the 'deviceLocation' query param is set to true in the API.
    - *`gpsTime`*(number): gps time of the device.
       
    - *`gprsTime`*(number): gprs time of the device.
       
    - *`latitude`*(number): latitude of the device.
       
       
    - *`longitude`*(number): longitude of the device.
    - *`address`*(string): last location address of the device.
    - *`status`*(number): movement status of the device
                          `1` is Moving, `2` is idle, `3` is stopped, `4` is towing, `5` is No Data, `6` is power off i.e. the device's battery is disconnected from the vehicle battery, `7` is No GPS, `12` is Activation Pending i.e. the device is not yet active and is yet to send the first ping. `Example: 3`
  
- *`positionEvents`* (array): Position events data of the device. This will get returned only for a single trip when the event query param is set to true in the API.
    - *`timestamp`*(number): The timestamp of the position event. `example: 1593261`
    - *`longitude`*(number): Longitude of the event. `example: 28.876`
    - *`latitude`*(number): Latitude of the event. `example: 77.87`
- *`destination`*(object): This will only get returned in case this object was explicitly defined while creating a trip.
    - *`geometry`* (object): This is standard geo json format.
       - *`type`* (string): supports the following geometry types - Point, Polygon.". `example: Point`
       -  *`coordinates`*(array): Latitude and longitude of the destination point.
    - *`radius`*(number): Radius of the point. `example: 100`
    - *`plannedTime`*(number): planned timestamp at which device reach the destination.
    - *`name`* (string): Name of the geofence point.
    - *`arrivalTime`*(number): actual timestamp at which device reach the destination.
    - *`departureTime`*(number): departure timestamp at which device leaves the destination.
    - *`address`*(string): address of the desntination point.
    - *`time`*(number): planned timestamp taken to reach the destination from previous point.
    - *`distance`*(number): planned distance taken to reach the destination from previous point.
    - *`pointName`*(string): name given to the destination point..
    - *`jobId`*(string): unique ID of the jobId. `example: 638f1045cc3758363bc89437`
    - *`links`*(string): Contains URLs related to the destination.
        - *`embedUrl`*(string): embeddable URL of the job or trip widget depending on within which object the link object is present. (type maybe `job` or `trip`). `Example: example: https://intouch.mappls.com/widget/{type}/#/638f1045cc3758363bc89437?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6`
    - *`metadata`*(object): will get returned only if it was mentioned while creating a trip.
       - `myattribute`(string): Dummy meta data value. this can be any key-value data pair. `example: sample text`
- *`geofences`*(array):A trip may have various points. This will only get returned in case the these geofence points were explicitly mentioned while creating a trip
    - This will only get returned in case this object was explicitly defined while creating a trip.
    - *`geometry`*(object): This is standard geo json format.
        - `type`(string): supports the following geometry types - Point, Polygon. `Example: Point`
        - `coordinates`(number): Latitude and longitude of the destination point. `example: List [ 77.234, 28.456 ]`
- *`radius`*(number): radius of the point. `example: 100`
- *`plannedTime`*(number): planned timestamp at which device reach the destination.
- *`name`*(string): name of the geofence point.
- *`arrivalTime`*(number): actual timestamp at which device reach the destination.
- *`departureTime`*(number): departure timestamp at which device leaves the destination.
- *`address`*(string): address of the desntination point.
- *`time`*(number): planned timestamp taken to reach the destination from previous point.
- *`distance`*(number): planned distance taken to reach the destination from previous point.
-*`pointName`*(string): name given to the destination point.
- *`jobId`*(string): Unique ID of the jobId. `example: 638f1045cc3758363bc89437`
- *`links`*(string): Contains URLs related to the destination.
        - *`embedUrl`*(string): embeddable URL of the job or trip widget depending on within which object the link object is present. (type maybe `job` or `trip`). `Example: example: https://intouch.mappls.com/widget/{type}/#/638f1045cc3758363bc89437?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6`
    - *`metadata`*(object): will get returned only if it was mentioned while creating a trip.
       - `myattribute`(string): Dummy meta data value. this can be any key-value data pair. `example: sample text`
- *`start`*(object): This will only get returned in case this object was explicitly defined while creating a trip.
    - *`geometry`*(string): This is standard geo json format.
          - `type`(string): supports the following geometry types - Point, Polygon. `Example: Point`
          - `coordinates`(number): Latitude and longitude of the destination point. `example: List [ 77.234, 28.456 ]`
    - *`radius`*(number): radius of the point. `example: 100`
    - *`plannedTime`*(number): planned timestamp at which device reach the destination.
    - *`name`*(string): name of the geofence point.
    - *`arrivalTime`*(number): actual timestamp at which device reach the destination.
    - *`departureTime`*(number): departure timestamp at which device leaves the destination.
    - *`address`*(string): address of the desntination point.
    - *`time`*(number): planned timestamp taken to reach the destination from previous point.
    - *`distance`*(number): planned distance taken to reach the destination from previous point.
    -*`pointName`*(string): name given to the destination point.
    - *`jobId`*(string): Unique ID of the jobId. `example: 638f1045cc3758363bc89437`
    - *`links`*(string): Contains URLs related to the destination.
      - *`embedUrl`*(string): embeddable URL of the job or trip widget depending on within which object the link object is present. (type maybe `job` or `trip`). `Example: example: https://intouch.mappls.com/widget/{type}/#/638f1045cc3758363bc89437?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6`
      - *`metadata`*(object): will get returned only if it was mentioned while creating a trip.
       - `myattribute`(string): Dummy meta data value. this can be any key-value data pair. `example: sample text`
- *`summary`*(object): Provides a summary of the trip’s overall details.
    - *`startedOn`*(number): imestamp when the trip started.
    - *`duration`*(number): The actual duration time (in seconds) of the trip.
    - *`distance`*(number): The actual distance (in meters) covered in the trip. `example: 7876.33`
    -*`endedOn`*(number): The actual end timestamp of the trip. `example: 1593157994`
    - *`delayedBy`*(number): The actual timestamp by which the trip got delayed.
    - *`plannedEndTime`*(number): The planned end timestamp of the trip. `example: null`
    - *`plannedStartTime`*(number): The planned start timestamp of the trip. `example: 1593157994`
    - *`plannedDuration`*(number): The planned duration time (in seconds) of the trip.
    - *`plannedDistance`*(number): The planned distance (in meters) of the trip.

## **Sample Input**

```
https://intouch.mappls.com/iot/api/v2.0/trips/5ef5a9e98a92df3a4a894db0?polyline=true&deviceLocation=true&event=true
```

## **Sample Output**

```json
    {
  "data": {
    "tripId": "5ef5a9e98a92df3a4a894db0",
    "deviceId": 0,
    "status": 1,
    "closureType": 1,
    "forceClose": false,
    "name": "my trip",
    "polylinePoints": {
      "coordinates": [
        {
          "lng": 0,
          "lat": 0
        }
      ]
    },
    "location": {
      "gpsTime": 1593261959,
      "gprsTime": 1593261959,
      "latitude": 29.507586,
      "longitude": 79.507586,
      "address": "string",
      "status": 3
    },
    "positionEvents": [
      {
        "timestamp": 1593261,
        "longitude": 28.876,
        "latitude": 77.87
      }
    ],
    "destination": {
      "geometry": {
        "type": "Point",
        "coordinates": [
          77.234,
          28.456
        ]
      },
      "radius": 100,
      "plannedTime": 0,
      "name": "string",
      "arrivalTime": 0,
      "departureTime": 0,
      "address": "string",
      "time": 0,
      "distance": 0,
      "pointName": "string",
      "jobId": "638f1045cc3758363bc89437",
      "links": {
        "embedUrl": "https://intouch.mappls.com/widget/{type}/#/638f1045cc3758363bc89437?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
      },
      "metadata": {
        "myattribute": "sample text"
      }
    },
    "geofences": [
      {
        "geometry": {
          "type": "Point",
          "coordinates": [
            77.234,
            28.456
          ]
        },
        "radius": 100,
        "plannedTime": 0,
        "name": "string",
        "arrivalTime": 0,
        "departureTime": 0,
        "address": "string",
        "time": 0,
        "distance": 0,
        "pointName": "string",
        "jobId": "638f1045cc3758363bc89437",
        "links": {
          "embedUrl": "https://intouch.mappls.com/widget/{type}/#/638f1045cc3758363bc89437?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
        },
        "metadata": {
          "myattribute": "sample text"
        }
      }
    ],
    "start": {
      "geometry": {
        "type": "Point",
        "coordinates": [
          77.234,
          28.456
        ]
      },
      "radius": 100,
      "plannedTime": 0,
      "name": "string",
      "arrivalTime": 0,
      "departureTime": 0,
      "address": "string",
      "time": 0,
      "distance": 0,
      "pointName": "string",
      "jobId": "638f1045cc3758363bc89437",
      "links": {
        "embedUrl": "https://intouch.mappls.com/widget/{type}/#/638f1045cc3758363bc89437?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
      },
      "metadata": {
        "myattribute": "sample text"
      }
    },
    "links": {
      "embedUrl": "https://intouch.mappls.com/widget/{type}/#/638f1045cc3758363bc89437?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
    },
    "summary": {
      "startedOn": 0,
      "duration": 0,
      "distance": 7876.33,
      "endedOn": 1593157994,
      "delayedBy": 0,
      "plannedEndTime": null,
      "plannedStartTime": 1593157994,
      "plannedDuration": 0,
      "plannedDistance": 0
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


