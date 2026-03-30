[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Trips Retrieval API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/vandana-gupta8020/Intouch-APIs/tree/main/InTouch%20Fleet%20Management%20APIs).**

## **Introduction**
The *`Trips Retrieval API`* allows you to fetch a comprehensive list of trips associated with one or more users. By providing a valid token key, this API returns detailed information about each trip, including `status`, `destination`, `geofence data`, `start and end details`, and the `associated device information`.

It enables users to retrieve active or completed trips within a specified time frame and filter the data based on various parameters such as device ID and trip status.

> **Note:**  Ensure that the trips already exist. If not, use the [Trip Creation API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Trip%20APIs/Trip%20Creation%20API.md) to create them.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/v2.0/trips

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
- `200` (OK(Successful operation)): The trips are returned as expected.
- `203` (Non-Authoritative Information): The specified device ID could not be found.
- `400` (Bad Request): Invalid ID supplied or invalid data type. Ensure the correct data type is used for the query parameters.
- `401` (Unauthorized): Unauthorized request. API access is forbidden due to invalid or missing credentials.
- `404` (Device not found): URL not found or endpoint does not exist.


## **Request Parameter**
All the parameters below are `optional`.
- *`deviceId`* (number, query): The ID(s) of the device(s) for which trips need to be retrieved. Pass the device IDs to get trips associated with particular devices. You can pass a single device ID or multiple device IDs as a comma-separated list or on new lines.
- *`startTime`* (long, query): Unix timestamp in seconds. Retrieve trips that occurred after the specified start timestamp.
- *`endTime`* (long, query): The end timestamp (in seconds). Retrieve trips that occurred before the specified end timestamp.
- *`status`* (integer): Filter trips based on their status:
    - `1`: Active Trips
    - `2`: Completed Trips.
- *`metadata`* (string, query): Optional metadata used to filter or customize the response based on additional criteria.
- *`limit`* (integer, query): Specifies the maximum number of trip records to be returned in the response.
- *`offset`* (integer, query): Specifies the starting point of the records to be fetched. Used for pagination along with the `limit` parameter.
- *`polyline`* (boolean, query): If set to `true`, the response will include polyline (route path) information. Default value is `false`.
- *`deviceLocation`* (boolean, query): If set to `true`, the response will include the latest device location details. Default value is `false`.
- *`event`* (boolean, query): If set to `true`, event-related data will be included in the response. Default value is `false`.


## **Response Parameters**
- **`tripId`**(string): A unique Id of the trip.
- **`deviceId`(number)**: The ID of the device associated with the trip. It can refer to a vehicle or tracking device.
- **`status`**(integer): The current status of the trip. It likely refers to whether the trip is active`1`, or completed trip `2`.
- **`closureType`**(integer): type of trip closure.
    - `1`: Trip will get closed based on the planned end time.
    - `2`: Trip will close when the device enters the destination area/geofence.
    - `3`: Trip will get closed manually by the user.
- **`forceClose`**(boolean): boolean value - If `true`, the trip will automatically close when the device is assigned to a new trip.
- **`polylinePoints`**:This is the route polyline. It will be returned for single trip only if polyline query param is set to true in the API.
    - `coordinates`: *`lng`*(number): Longitude point. *`lat`*(number): Latitude point.  
- **`location`**(object): location data of the device. These fields are returned only when the response contains a single trip. when the `deviceLocation` query param is set to true in the API.
    - `gpsTime`(number): gps timestamp of the device.
    - `gprsTime`(number): Server received time of the device.
    - `latitude`(number): Latitude of the trip's location.
    - `longitude`(number): Longitude of the trip's location.
    - `address`(string): Address corresponding to the location.
    - `status`(number): movement status of the device
        - `1` is Moving
        - `2` is idle
        - `3` is stopped
        - `4` is towing
        - `5` is No Data
        - `6` is power off i.e. the device's battery is disconnected from the vehicle battery
        - `7` is No GPS
        - `12` is Activation Pending i.e. the device is not yet active and is yet to send the first ping.
- **`positionEvents`**(array of object): Position events data of the device. This will get returned only for a single trip when the event query param is set to true in the API.
    - `timestamp`(number): The timestamp of the position event.
    -  `longitude`(number): Longitude of the trip's location.
    -  `latitude`(number): Latitude of the trip's location.
- **`destination`**: This will only get returned in case this object was explicitly defined while creating a trip.
    - `geometry`(object): 
        - `Coordinates`(array[number]): Coordinates are represented as `[longitude, latitude]`.
         - `type`(string): supports the following geometry types - Point, Polygon.
    - `radius`(number): Radius of the point.
    - `plannedTime`(number): planned timestamp at which device reach the destination.
    - `name`(string): Name of the geofence point.
    - `arrivalTime`(number): actual timestamp at which device reach the destination.
    - `departureTime`(number): departure timestamp at which device leaves the destination
    - `time`(number): planned timestamp taken to reach the destination from previous point.
    - `distance`(number): planned distance taken to reach the destination from previous point
    - `pointName`(string): Name assigned to the destination point.
    - `jobId`(string): unique ID of the jobId.
    - `address`(string): Address of the destination point.
    - `links` (object):
        - `embedUrl`(string): Embeddable URL for the trip or job widget.
    - `metadata`: will get returned only if it was mentioned while creating a trip.
      - `myattribute`(string): Dummy meta data value. This can be any key-value data pair.
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


## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/v2.0/trips?limit=3&polyline=false&deviceLocation=false&event=false' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
{
    "data": [
        {
            "tripId": "5f3141d8cc37586794baa078",
            "deviceId": 122403,
            "destination": {
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        28.515657,
                        77.226605
                    ]
                },
                "radius": 100,
                "metadata": {
                    "destination_shipment_id": "ABC123"
                },
                "address": " (Barents Sea)"
            },
            "geofences": [],
            "status": 2,
            "metadata": {
                "shift_id": "ABC123"
            },
            "closureType": 3,
            "forceClose": false,
            "summary": {
                "startedOn": 1597063639,
                "duration": null,
                "distance": null,
                "endedOn": 1605007806,
                "delayedBy": null,
                "plannedEndTime": null,
                "plannedStartTime": 1597063639,
                "plannedDuration": 0,
                "plannedDistance": 0.0
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/trip/#/5f3141d8cc37586794baa078?access_token=2c3bb162-f724-4507-9bde-8ec8d19cc699"
            }
        },
        {
            "tripId": "5f314262cc37586794baa079",
            "deviceId": 53452,
            "destination": {
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        28.515657,
                        77.226605
                    ]
                },
                "radius": 100,
                "metadata": {
                    "destination_shipment_id": "ABC123"
                },
                "address": " (Barents Sea)"
            },
            "geofences": [],
            "status": 2,
            "metadata": {
                "shift_id": "ABC123"
            },
            "closureType": 3,
            "forceClose": false,
            "summary": {
                "startedOn": 1597063777,
                "duration": null,
                "distance": null,
                "endedOn": 1597063962,
                "delayedBy": null,
                "plannedEndTime": null,
                "plannedStartTime": 1597063777,
                "plannedDuration": 0,
                "plannedDistance": 0.0
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/trip/#/5f314262cc37586794baa079?access_token=2c3bb162-f724-4507-9bde-8ec8d19cc699"
            }
        },
        {
            "tripId": "5f31431bcc37586794baa07a",
            "deviceId": 53452,
            "destination": {
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        28.515657,
                        77.226605
                    ]
                },
                "radius": 100,
                "metadata": {
                    "destination_shipment_id": "ABC123"
                },
                "address": " (Barents Sea)"
            },
            "geofences": [],
            "status": 2,
            "metadata": {
                "shift_id": "ABC123"
            },
            "closureType": 3,
            "forceClose": true,
            "summary": {
                "startedOn": 1597063962,
                "duration": null,
                "distance": null,
                "endedOn": 1597063991,
                "delayedBy": null,
                "plannedEndTime": null,
                "plannedStartTime": 1597063962,
                "plannedDuration": 0,
                "plannedDistance": 0.0
            },
            "links": {
                "embedUrl": "https://intouch.mappls.com/widget/trip/#/5f31431bcc37586794baa07a?access_token=2c3bb162-f724-4507-9bde-8ec8d19cc699"
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








