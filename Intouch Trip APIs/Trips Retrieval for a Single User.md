[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Trips Retrieval for a Single User

## **Introduction**


The ***`Trips Retrieval for a User API`*** allows you to fetch a comprehensive list of trips associated with a specific user. By providing a token key, this API returns detailed information about each trip, including `status`, `destination`, `geofence data`, `start and end details`, and the `associated device information`. It enables users to retrieve active or completed trips within a specified time frame and filter the data based on various parameters such as device ID and trip status.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET


## **Input URL:**

 > https://intouch.mappls.com/iot/api/v2.0/trips

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

200 - `OK(Successful operation)` - The trips are returned as expected.

203 - `Device Not Found` - The specified device ID could not be found.

400 - `Bad Request` - Invalid ID supplied or invalid data type.
Ensure the correct data type is used for the query parameters.

401 - `Unauthorized` - Unauthorized request. API access is forbidden due to invalid or missing credentials.

404 - `Not Found` - URL not found or endpoint does not exist.


## **Request Parameter**

1. *`limit`*(integer) - Limits the number of records returned. Pass an integer to specify the limit.

2. *`status`*(integer) - Filter trips based on their status: pass `1` for active trips, `2` for completed trips.

3. *`deviceId`*(string/number) - Filter trips by device ID. Pass the device IDs to get trips associated with particular devices.

4. *`startTime`*(number) - Retrieve trips that occurred after the specified start timestamp.

5. *`endTime`*(number)Retrieve trips that occurred before the specified end timestamp.

## **Response Parameters**

- **`tripId`**(string): A unique id of the trip. `example: 5ef5a9e98a92df3a4a894db0` 
- **`deviceId`(number)**: The ID of the device associated with the trip. It can refer to a vehicle or tracking device.
- **`status`**(integer): The current status of the trip. It likely refers to whether the trip is active`1`, or completed trip `2`.
- **`closureType`**(integer): type of trip closure. 1 - trip will get closed based on the planned end time. 2 - trip will close when the device enters the destination area/geofence. 3 - trip will get closed manually by the user. `example: 1`
- **`forceClose`**(boolean): boolean value - if `true` then trip will get automatically closed as soon as the device gets associated with another trip. `example: false`
- **`polylinePoints`**:This is the route polyline. It Will get returned for single trip only if polyline query param is set to true in the API.
    - `coordinates`: *`lng`*(number): Longitude point.
                          *`lat`*(number): Latititude point.  
- **`location`**(object): location data of the device. This will get returned only for a single trip when the 'deviceLocation' query param is set to true in the API.
    - `gpsTime`(number): gps time of the device. *`example: 1593261959`*
    - `gprsTime`(number): gps time of the device. *`example: 1593261959`*
    - `latitude`(number): Latitude of the trip's location. *`example: 29.507586`*
    - `longitude`(number): Longitude of the trip's location. *`example: 79.507586`*
    - `address`(string): Address corresponding to the location.
    - `status`(number): movement status of the device
                        `1` is Moving, `2` is idle, `3` is stopped, `4` is towing, `5` is No Data, `6` is power off i.e. the device's battery is disconnected from the vehicle battery, `7` is No GPS, `12` is Activation Pending i.e. the device is not yet active and is yet to send the first ping. *`example: 3`*
- **`positionEvents`**(array of object): Position events data of the device. This will get returned only for a single trip when the event query param is set to true in the API.
    - `timestamp`(number): The timestamp of the position event. *`example: 1593261`*
    -  `longitude`(number): Longitude of the trip's location. *`example: 28.876`*
    -  `latitude`(number): Latitude of the trip's location. *`example: 77.87`*
- **`destination`**: This will only get returned in case this object was explicitly defined while creating a trip.
    - `geometry`(number): Coordinates represented in standard GeoJSON format. `example: List [ 77.234, 28.456 ]`
         - `type`(string): supports the following geometry types - Point, Polygon.`example: Point`
    - `radius`(number): Radius of the point. `Example: 100`
    - `plannedTime`(number): planned timestamp at which device reach the destination.
    - `name`(string): Name of the geofence point.
    - `arrivalTime`(number): actual timestamp at which device reach the destination.
    - `departureTime`(number): departure timestamp at which device leaves the destination
    - `time`(number): planned timestamp taken to reach the destination from previous point.
    - `distance`(number): planned distance taken to reach the destination from previous point
    - `pointName`(string): name given to the destination point.
    - `jobId`(string): unique ID of the jobId. `example: 638f1045cc3758363bc89437`
    - `address`(string): Address of the destination point.
    - `links`-Embed URL(string): embeddable URL of the job or trip widget depending on within which object the link object is present. (type maybe `job` or `trip`). `example: https://intouch.mappls.com/widget/{type}/#/638f1045cc3758363bc89437?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6`
    - `metadata`: will get returned only if it was mentioned while creating a trip.
      - `myattribute`(string): Dummy meta data value. This can be any key-value data pair. `example: sample text`

- **`geofences`**: List of geofences, which are virtual boundaries set around a specific location.
- **`start`**: Information about the starting point of the trip, similar to the destination.
- **`links`**: Contains URLs for embedding the trip data, typically a map or detailed view.
- **`summary`**: A summary of the trip, including start and end times, duration, distance, etc.
    - **`Fields`**:-
        - `startedOn`(number): The actual start timestamp of the trip.
        - `endedOn`(number): The actual end timestamp of the trip.
        - `duration`(number): The actual duration time (in seconds) of the trip.
        - `distance`(number): The actual distance (in meters) covered in the trip.
        - `delayedBy`(number): The actual timestamp by which the trip got delayed.
        - `plannedStartTime`(number): The planned start timestamp of the trip.
        - `plannedEndTime`(number): The planned end timestamp of the trip.
        - `plannedDuration`(number): the planned duration time (in seconds) of the trip.
        - `plannedDistance`(number): The planned distance (in meters) of the trip.


## **Sample Input**

```
https://intouch.mappls.com/iot/api/v2.0/trips?limit=5&status=1&deviceId=10647019&startTime=1735251900&endTime=1735255800
```

## **Sample Output**

```json
{
    "data": [
        {
            "tripId": "676cdea677ccd110137e8aa6",
            "deviceId": 1363489,
            "deviceName": "oneplus6",
            "destination": {
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        77.26887236686416,
                        28.550937774376667
                    ]
                },
                "radius": 30,
                "plannedTime": 1735343337,
                "metadata": {
                    "myattribute": "MapmyIndia"
                },
                "address": "237, unnamed road, okhla industrial estate phase 3, new delhi, delhi. 21 m from mapmyindia head office new delhi, pin-110020 (india)",
                "time": 0,
                "distance": 0.0,
                "name": "string"
            },
            "geofences": [
                {
                    "geometry": {
                        "type": "Point",
                        "coordinates": [
                            77.26887236686416,
                            28.550937774376667
                        ]
                    },
                    "radius": 30,
                    "plannedTime": 1735343337,
                    "metadata": {
                        "myattribute": "68 Okhla Pahse 3"
                    },
                    "address": "237, unnamed road, okhla industrial estate phase 3, new delhi, delhi. 21 m from mapmyindia head office new delhi, pin-110020 (india)",
                    "time": 0,
                    "distance": 0.0,
                    "name": "68 Okhla Pahse 3"
                },
                {
                    "geometry": {
                        "type": "Point",
                        "coordinates": [
                            77.26887236686416,
                            28.550937774376667
                        ]
                    },
                    "radius": 30,
                    "plannedTime": 1735343337,
                    "metadata": {
                        "myattribute": "HDFC xing"
                    },
                    "address": "237, unnamed road, okhla industrial estate phase 3, new delhi, delhi. 21 m from mapmyindia head office new delhi, pin-110020 (india)",
                    "time": 0,
                    "distance": 0.0,
                    "name": "HDFC xing"
                }
            ],
            "status": 1,
            "metadata": {
                "myattribute": "MapmyIndia Head office"
            },
            "closureType": 2,
            "forceClose": false,
            "name": "oneplus6",
            "summary": {
                "startedOn": null,
                "duration": null,
                "distance": null,
                "endedOn": null,
                "delayedBy": null,
                "plannedEndTime": 1735343337,
                "plannedStartTime": 1735188134,
                "plannedDuration": 0,
                "plannedDistance": 0.0
            },
            "start": {
                "plannedTime": 1735188134
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/trip/#/676cdea677ccd110137e8aa6?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
            }
        },
        {
            "tripId": "676ced2f77ccd110137e8c2c",
            "deviceId": 1363489,
            "deviceName": "oneplus6",
            "destination": {
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        77.23536941846578,
                        28.62717564791904
                    ]
                },
                "radius": 30,
                "plannedTime": 1734023748,
                "metadata": {
                    "myattribute": "MapmyIndia"
                },
                "address": "1, sikandra lane, abul fazal road area, connaught place, new delhi, delhi. 103 m from mahavir nethralaya, pin-110001 (india)",
                "time": 0,
                "distance": 0.0,
                "name": "string"
            },
            "geofences": [
                {
                    "geometry": {
                        "type": "Point",
                        "coordinates": [
                            77.23536941846578,
                            28.62717564791904
                        ]
                    },
                    "radius": 30,
                    "plannedTime": 1734023748,
                    "metadata": {
                        "myattribute": "68 Okhla Pahse 3"
                    },
                    "address": "1, sikandra lane, abul fazal road area, connaught place, new delhi, delhi. 103 m from mahavir nethralaya, pin-110001 (india)",
                    "time": 0,
                    "distance": 0.0,
                    "name": "68 Okhla Pahse 3"
                },
                {
                    "geometry": {
                        "type": "Point",
                        "coordinates": [
                            77.23536941846578,
                            28.62717564791904
                        ]
                    },
                    "radius": 30,
                    "plannedTime": 1734023748,
                    "metadata": {
                        "myattribute": "HDFC xing"
                    },
                    "address": "1, sikandra lane, abul fazal road area, connaught place, new delhi, delhi. 103 m from mahavir nethralaya, pin-110001 (india)",
                    "time": 0,
                    "distance": 0.0,
                    "name": "HDFC xing"
                }
            ],
            "status": 1,
            "metadata": {
                "myattribute": "MapmyIndia Head office"
            },
            "closureType": 2,
            "forceClose": false,
            "name": "oneplus6",
            "summary": {
                "startedOn": null,
                "duration": null,
                "distance": null,
                "endedOn": null,
                "delayedBy": null,
                "plannedEndTime": 1734023748,
                "plannedStartTime": 1735191855,
                "plannedDuration": 0,
                "plannedDistance": 0.0
            },
            "start": {
                "plannedTime": 1735191855
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/trip/#/676ced2f77ccd110137e8c2c?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
            }
        },
        {
            "tripId": "676cef71f7b03b1054a1cf8a",
            "deviceId": 10647019,
            "deviceName": "Vandana-test ",
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
                "time": 0,
                "distance": 0.0,
                "name": "string"
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
                    "plannedTime": 1735192433,
                    "metadata": {
                        "myattribute": "sample text"
                    },
                    "address": "unnamed road, asola, new delhi, delhi. pin-110074 (india)",
                    "time": 0,
                    "distance": 0.0,
                    "name": "string"
                }
            ],
            "status": 1,
            "metadata": {
                "myattribute": "sample text"
            },
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
                "plannedStartTime": 1735192433,
                "plannedDuration": 0,
                "plannedDistance": 0.0
            },
            "start": {
                "plannedTime": 1735192433
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/trip/#/676cef71f7b03b1054a1cf8a?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
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








