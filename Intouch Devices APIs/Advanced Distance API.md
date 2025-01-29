
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Advanced Distance API

## **Introduction**

The *`Advanced Distance API`* offers an accurate and precise view of the snapped distance between two geographical points. With the ability to define a time range and tweak several parameters, this API will allow you to retrieve and view the exact travel distance, including GPS coordinates and real-time address data.

This API is perfect for businesses that require precise distance measurement between two locations, especially for logistics, delivery tracking, and geographical analysis.

## **Security Type**
This API uses OAuth 2.0 for authentication. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Accept: `application/json`**
 

## **Input Method:** 
- GET

## **Input URL:**
 > https://intouch.mappls.com/iot/api/devices/advanceDistance

## **Request Parametrs**
The **`“bold”`** one’s are mandatory, and the *`“italic”`* one’s are optional.

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| **`deviceId`** | number | The unique ID of the device. |
| **`startTime`** | number | Start time in Unix timestamp (seconds). |
| **`endTime`** | number | End time in Unix timestamp (seconds). |
| *`skipSnaping`* | boolean | Flag to skip the snapping process. |
| *`skipDistanceMatrix`* | boolean | Flag to skip distance matrix. |
| *`includeGeometry`* | boolean | Include geometry details in the response. |

## **Response Codes**

| **Code** | **Description** |
| --- | --- |
| `200(Successful operation)` | The request was successful, returning trip data including summary details, GPS coordinates, and road-snapping metadata. |
| `203(Device Not Found)` | Non-Authoritative Information. {"error":"Device not allowed"} |
| `204(No Content)` | The request was successful, but there is no content to return. |
| `400(Bad Request)` | Invalid ID supplied or invalid data type. |
| `401(Unauthorized Request)` | The request is forbidden due to lack of proper authorization. |
| `404(Not Found)` | The URL was not found. |

 ## **Response Parameters** 

- **`data`**: Contains details related to the tracked device, including summary information, route geometry, and metadata.
    - *`deviceId`*(Integer): The unique ID of the device.
- **`summary`**: Provides an overview of the journey recorded by the device.
    - *`distance`*(Float): Total distance traveled (in kilometers).
    - *`duration`*(Integer): Total duration of the trip (in seconds).
    - *`avgSpeed`*(Float): Average speed (in km/h) during the trip.
    - *`noDataDuration`*(Integer): Duration (in seconds) for which no data was recorded.
    - *`startAddress`*(String): Address where the trip started.
    - *`endAddress`*(String): Address where the trip ended.
    - *`startTimestamp`*(Integer): Start time of the trip (Unix timestamp).
    - *`endTimestamp`*(Integer): End time of the trip (Unix timestamp).
- **`geometry`**: Contains the recorded and processed(snapped) route details.
    - *`features`*(Array of objects): Represents different versions of the recorded route. Each feature contains:
       - *`geometry`*(Object):
         - *`coordinates`*(Array of arrays [longitude, latitude]): Sequence of GPS points.
         - *`type`*(String): Type of geometry (always "LineString").
       - *`type`*(String): Defines this as a Feature.
       - *`properties`* (Object):
         - *`stroke-width`*(String): Thickness of the line when visualized on a map.
         - *`value`*(String): "Original" for raw GPS data, "Snapped" for adjusted route.
         - *`stroke`*(String): Color code for visualization.
- **`metaData`**: Contains additional technical details about the data processing.
    - *`snapToRoadErrorCount`*(Integer): Number of errors encountered while snapping the route to the road network.
    - *`distanceMatrixHitsCount`*(Integer): Number of successful hits when querying the distance matrix service.
    - *`snapToHitsCount`*(Integer): Number of successful snap-to-road hits.
    - *`snapToRoadHits`*(Array of objects): Details of the road-snapping process. Each hit contains:
         - *`timeTakenMillis`*(Integer): Time taken (in milliseconds) for the road-snapping process.
         - *`response`*(String): JSON response from the snapping service (encoded as a string).
         - *`params`*(String): Parameters used for the snapping request, including GPS points, timestamps, geometries, and other settings.
    - *`totalSnappingTimeSec`*(Integer): Total time (in seconds) taken for road-snapping.


## **Sample Input**
```
https://intouch.mappls.com/iot/api/devices/advanceDistance?deviceId=10647019&startTime=1738033320&endTime=1738034400&skipSnaping=false&skipDistanceMatrix=false&includeGeometry=true
```
## **Sample output**

```json
{
    "data": {
        "deviceId": 10647019,
        "summary": {
            "distance": 10.06,
            "duration": 0,
            "avgSpeed": 9.223372036854776E16,
            "noDataDuration": 0,
            "startAddress": "GD Birla Marg, Saidabad, New Delhi, Delhi. 25 m from Police Check Post, Pin-110076 (India)",
            "endAddress": "225, Unnamed Road, Okhla Industrial Estate Phase 3, New Delhi, Delhi. 6 m from Fareye, Pin-110020 (India)",
            "startTimestamp": 1738033414,
            "endTimestamp": 1738034350
        },
        "geometry": {
            "features": [
                {
                    "geometry": {
                        "coordinates": [
                            [77.3100799,28.5436051],
                            [77.3100799,28.5436051],
                            [77.3092483,28.5443917],
                            [77.3069867,28.5442383],
                            [77.30574,28.5442717],
                            [77.303545,28.54314],
                            [77.3016888,28.5431053],
                            [77.2977417,28.5408333],
                            [77.2956667,28.5400983],
                            [77.2936233,28.5393117],
                            [77.2928483,28.5392867],
                            [77.2922833,28.5392933],
                            [77.279745,28.533335],
                            [77.2786333,28.5327617],
                            [77.2779817,28.53291],
                            [77.277645,28.5323067],
                            [77.2768204,28.5325427],
                            [77.272205,28.5387017],
                            [77.2717017,28.5387283],
                            [77.2709217,28.5384063],
                            [77.270415,28.538315],
                            [77.266525,28.5398617],
                            [77.265357,28.5433416],
                            [77.26294,28.5482567],
                            [77.263485,28.5464567],
                            [77.264185,28.5449717],
                            [77.2663056,28.5444733],
                            [77.2675583,28.5443333],
                            [77.2676449,28.5450903],
                            [77.2677867,28.5455867],
                            [77.267485,28.54617],
                            [77.2680769,28.5474542],
                            [77.2691817,28.548965],
                            [77.2691817,28.548965]
                        ],
                        "type": "LineString"
                    },
                    "type": "Feature",
                    "properties": {
                        "stroke-width": "2",
                        "value": "Original",
                        "stroke": "#d90d0d"
                    }
                },
                {
                    "geometry": {
                        "coordinates": [
                            [77.31007,28.54359],
                            [77.30905,28.54418],
                            [77.30858,28.54452],
                            [77.30726,28.54559],
                            [77.30702,28.54568],
                            [77.30688,28.54566],
                            [77.30677,28.5456],
                            [77.30512,28.54424],
                            [77.30506,28.5443],
                            [77.30675,28.54574],
                            [77.30702,28.54584],
                            [77.30718,28.54578],
                            [77.30871,28.54453],
                            [77.30912,28.54425],
                            [77.30582,28.5442],
                            [77.30676,28.54501],
                            [77.30645,28.54533],
                            [77.30364,28.54314],
                            [77.29774,28.54084],
                            [77.27978,28.53328],
                            [77.27662,28.53167],
                            [77.27208,28.53864],
                            [77.27175,28.53864],
                            [77.26738,28.53683],
                            [77.26221,28.54938],
                            [7.2628,28.54822],
                            [77.26437,28.54438],
                            [77.26766,28.54501],
                            [77.26803,28.54506],
                            [77.2682,28.54585],
                            [77.26981,28.5463],
                            [77.26941,28.54705],
                            [77.26864,28.54695],
                            [77.26819,28.5475],
                            [77.26684,28.55004],
                            [77.2678,28.55013],
                            [77.26865,28.54849],
                            [77.26929,28.54878],
                            [77.26929,28.54878]
                        ],
                        "type": "LineString"
                    },
                    "type": "Feature",
                    "properties": {
                        "stroke-width": "1",
                        "value": "Snapped",
                        "stroke": "#000d0d"
                    }
                }
            ],
            "type": "FeatureCollection"
        },
        "metaData": {
            "snapToRoadErrorCount": 0,
            "distanceMatrixHitsCount": 2,
            "snapToHitsCount": 1,
            "snapToRoadHits": [
                {
                    "timeTakenMillis": 48,
                    "response": "{\"Server\":\"DE-5405\",\"version\":\"202401.221.5223\",\"results\":{\"matchings\":[{\"geometry\":\"m|emD}rzvMuBjEcA|AuEfGQn@BZJTnGhIKJ_HqISu@J_@xFqHv@qA\"},{\"geometry\":\"g`fmDkxyvMaD{D_A|@tLpPjMzc@fn@foB`IvRqj@j[?`AhJhZmmAh_@fFuB~VyH}BqSIiA}Ca@yAaIuCnARxCmBxA{NlGQ_EfIiDy@_C??\"}],\"snappedPoints\":[{\"distance\":2.282506,\"location\":[77.310071,28.543586],\"waypoint_index\":0},null,{\"distance\":20.349839,\"location\":[77.309119,28.544248],\"waypoint_index\":1},null,{\"distance\":11.61291,\"location\":[77.305824,28.544198],\"waypoint_index\":0},null,null,{\"distance\":1.254236,\"location\":[77.297736,28.540843],\"waypoint_index\":1},null,null,null,null,{\"distance\":7.235405,\"location\":[77.279783,28.533279],\"waypoint_index\":2},null,null,null,null,{\"distance\":13.807712,\"location\":[77.272082,28.538641],\"waypoint_index\":3},{\"distance\":10.902701,\"location\":[77.271754,28.538641],\"waypoint_index\":4},null,null,null,null,{\"distance\":14.194799,\"location\":[77.262803,28.548215],\"waypoint_index\":5},null,null,null,null,{\"distance\":9.470735,\"location\":[77.267655,28.545005],\"waypoint_index\":6},null,null,{\"distance\":12.185335,\"location\":[77.268189,28.547502],\"waypoint_index\":7},{\"distance\":22.766162,\"location\":[77.269292,28.548784],\"waypoint_index\":8},{\"distance\":22.766162,\"location\":[77.269292,28.548784],\"waypoint_index\":9}]},\"responseCode\":200}",
                    "params": "pts=77.3100799,28.5436051;77.3100799,28.5436051;77.3092483,28.5443917;77.3069867,28.5442383;77.30574,28.5442717;77.303545,28.54314;77.3016888,28.5431053;77.2977417,28.5408333;77.2956667,28.5400983;77.2936233,28.5393117;77.2928483,28.5392867;77.2922833,28.5392933;77.279745,28.533335;77.2786333,28.5327617;77.2779817,28.53291;77.277645,28.5323067;77.2768204,28.5325427;77.272205,28.5387017;77.2717017,28.5387283;77.2709217,28.5384063;77.270415,28.538315;77.266525,28.5398617;77.265357,28.5433416;77.26294,28.5482567;77.263485,28.5464567;77.264185,28.5449717;77.2663056,28.5444733;77.2675583,28.5443333;77.2676449,28.5450903;77.2677867,28.5455867;77.267485,28.54617;77.2680769,28.5474542;77.2691817,28.548965;77.2691817,28.548965&timestamps=1738033414;1738033425;1738033463;1738033480;1738033497;1738033513;1738033529;1738033561;1738033577;1738033593;1738033609;1738033641;1738033706;1738033722;1738033754;1738033771;1738033787;1738033884;1738033935;1738033967;1738033983;1738033998;1738034064;1738034127;1738034143;1738034159;1738034191;1738034238;1738034286;1738034301;1738034317;1738034333;1738034349;1738034350&geometries=polyline&radiuses=10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10;10&gaps=ignore&tidy=true"
                }
            ],
            "totalSnappingTimeSec": 0
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

