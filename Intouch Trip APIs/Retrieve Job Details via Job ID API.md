
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Retrieve Job Details via Job ID API

## **Introduction**

The *`Retrieve Job Details via Job ID API`* allows users to fetch detailed information about a specific job using its unique Job ID. This API provides essential data related to the job, such as its status, distance information, associated trip details, and the device's location. It is primarily used for tracking and managing job progress, retrieving real-time data, and performing analysis on the job's performance. By using the Job ID, users can access comprehensive insights into a particular job's current status and related attributes.


## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://www.mapmyindia.com/api/advanced-maps/doc/authentication-api.php).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET


## **Input URL:**
 > https://intouch.mappls.com/iot/api/v2.0/trips/job/{jobId}


## **Request Mandatory Parameters**

| **Parameter** | **Type** | **Location** | **Description** |
| --- | --- | --- | --- |
| `jobId` | Number | Path | This is the unique ID of the job you want to retrieve details for. Example: `2345` |

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**
1. 200(`OK Successful operation`): The request was processed successfully, and the job details are returned in the response.
2. 203(`Invalid ID`): The provided job ID is invalid or does not exist. Please verify the job ID and try again.
3. 400(`Bad Request`): Invalid ID supplied or invalid data type. Check the request for incorrect parameters or data formats.
4. 401(`Unauthorized Request`):	Access to the API is forbidden due to unauthorized access. Ensure that you have valid authorization credentials.
5. 404(`URL Not Found`): The requested resource could not be found. The job ID may be incorrect or the resource is unavailable.

## **Response Parameters**

- **`jobobjresponse`**
    - **`jobId`** (string): ID of the job. `Example: 638f1045cc3758363bc89437`

    - **`distanceRemaining`** (number): Remaining distance in the job in kilometers. `Example: 58.6`

    - **`status`** (integer): Status of the job.  `1`: Active trip &  `2`: Completed trip. `Example: 1`

    - **`plannedDistance`** (number): Planned distance of the job in kilometers. `Example: 30`

    - **`actualDistance`** (number): Actual distance traveled on the job in kilometers. `Example: 30`

    - **`actualStartTime`** (number): Actual start time of the job in epoch. Example: 1670492866`

    - **`eta`** (number): Estimated time of arrival at the job location in epoch. `Example: 1670532853`

    - **`actualEndTime`** (number): Actual end time of the job in epoch. `Example: 1670492866`

    - **`etaSec`** (number): Estimated time of arrival at the job location in seconds from the current time (time of API request). `Example: 39832`

    - **`tripId`** (string): ID of the trip. `Example: 638f1045cc3758363bc89436`

    - **`tripStatus`** (integer): Status of the trip. `1`: Active trip &  `2`: Completed trip. `Example: 1`

- **`deviceLocation`**: Last known location data of the device. This will only be returned for a single job.

    - **`id`** (number): ID of the device. `Example: 364371`

    - **`gpsTime`** (number): GPS time of the device in epoch. Example: 1593261959`

    - **`gprsTime`** (number): GPRS time of the device in epoch. Example: 1593261959`

    - **`heading`** (number): Heading or bearing of the device in degrees Example: 133.27`

    - **`speedKph`** (number) Speed of the device in kilometers per hour. Example: 35.7`

    - **`address`** (string): Last location address of the device. `Example: 16-3-991/10/A, Nalgonda Cross Road, Chanchalguda, Hyderabad, Telangana. 36 m from Meridian Function Hall, Pin-500036 (India)`

    - **`name`** (string): Name of the device. `Example: TS 16 ET 7668`

    - **`status`** (number): Movement status of the device:`1`: Moving,`2`: Idle,`3`: Stopped,`4`: Towing, `5`: No Data,`6`: Power Off (device battery disconnected from vehicle battery),`7`: No GPS, and `12`: Activation Pending (device is not yet active and hasn't sent its first ping). `Example: 3`

    - **`geometry`** (object): Standard GeoJSON format.  
        - **`type`** (string): Supports the following geometry types: `Point`, `Polygon`. `Example: Point`  
        - **`coordinates`** (array): List of latitude and longitude defining the device's location. `Example: [77.234, 28.456]`

- **`destination`**: Destination of the job.

    - **`geometry`** (object): Standard GeoJSON format.  
        - **`type`** (string): Supports the following geometry types: `Point`, `Polygon`. `Example: Point`  
        - **`coordinates`** (array): List of latitude and longitude defining the destination. `Example: [77.234, 28.456]`

    - **`radius`** (number): Radius of the point in meters. Example: 100`

    - **`name`** (string): Name of the geofence/point.

    - **`plannedTime`** (number): Planned time (in epoch) at which the device is expected to reach the job destination.

    - **`metadata`**-*`myattribute`* (string): Dummy meta data value. this can be any key-value data pair.`Example: sample text`
    - **`status`** (number): Status of the job in the trip.  `1`: Active job & `0`: Inactive job. `Example: 0`

    - **`sequence`** (number): Sequence of this job in the entire trip (if the trip contains multiple jobs). `Example: 2`


## **Sample Input**

```
https://intouch.mappls.com/iot/api/v2.0/trips/job/676cef71f7b03b1054a1cf8ba
```

## **Sample Output**

```json
{
    "data": {
        "jobId": "676cef71f7b03b1054a1cf8b",
        "status": 0,
        "plannedDistance": 0.0,
        "deviceLocation": {
            "id": 10647019
        },
        "destination": {
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
            "name": "string",
            "status": 0,
            "sequence": 1
        },
        "tripId": "676cef71f7b03b1054a1cf8a",
        "tripStatus": 2
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




<div align="center">@ Copyright 2022 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

