
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch Device Drive Details API

## **Introduction**

This API *`retrieves the drive details of a vehicle`* associated with an account on our telematics platform. A vehicle can be a device or sensor directly connected to the platform, or it could be linked via a third-party data aggregator that uses our telematics services. A "drive" consists of a list of geo-positions reported for any object (such as vehicles, assets, or people), based on pre-defined conditions.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL:**

 > https://intouch.mappls.com/iot/api/device/drive

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- 200 `OK` - The request was successfully processed, and the operation was successful.

- 203 `Device Not Found` - No device found with the provided ID.

- 400 `Bad Request` - Invalid device ID supplied or invalid data type. For example, input attribute "id" is integer but string value gets passed.

- 401 `Unauthorized` - Access to the API is restricted, and the request is not authorized.

- 404 `URL Not Found` - The requested resource could not be located on the server.

## **Request Parameters**

The **`“bold”`** one's are mandatory, and the *`“italic”`* one's are optional.

1. **`deviceId`**(integer): The ID of the device for which the drives need to be fetched. `Example: deviceId=12345`

2. **`startTime`**(number): The starting timestamp from which the drive details need to be fetched. `Example: startTime=1612135200`

3. **`endTime`**(number): The end timestamp up to which the drive details need to be fetched. `Example: endTime=1612140000`
  
 ## **Response Parameters** 

- **`DriveData parameters:`**: The `DriveData` encapsulates the details of a single drive instance, including location, movement metrics, and driving behavior counts.
     - **`deviceId`**(number): The unique identifier of the device for which the drive details are provided. `Example: 67790`
     - **`location parameters:`**: Details about the start and end points of the drive, along with the average speed.
          - `startAddress`(string): The address where the drive starts. `Example: 3605, 13th G Main Road, HAL Stage 2, Indiranagar, Bengaluru, Karnataka. 35 m from Supraja Meru pin-560038 (India)`
          - `startTimestamp`(number): The epoch timestamp indicating the start time of the drive. `Example: 1574913781`
          - `endAddress`(string): The address where the drive ends. `Example: 1139, Sweth Ambara, 1st Cross Road, HAL Stage 2, Indiranagar, Bengaluru, Karnataka. 32 m from AMC Cookware India Pvt Ltd pin-560038`
          - `endTimestamp`(number): Epoch timestamp indicating when the drive ended. `Example: 1574914046`
          - `avgSpeed`(number): The average speed during the drive in km/h. `Example: 45.34`
          
     - **`movement parameters:`**: Metrics related to the movement of the vehicle during the drive.
        - `duration`(number): Total duration of the drive in seconds.`Example: 265`
        - `distance`(number): The distance traveled in kilometers.`Example: 12.34`
        - `idleTime`(number): The time the vehicle was stationary in seconds`Example: 265`
        - `movementTime`(number): Time spent moving in seconds.`Example: 800`
        - `stoppageTime`(number): Stoppages time in seconds. `Example: 1300`
        
     - **`drivingBehaviourCount parameters:`**: Counts of specific driving behavior events observed during the drive.
        - `haCount`(integer): Count of harsh acceleration events. `Example: 2`
        - `hbCount`(integer): Count of harsh braking events. `Example: 5`
        - `hcCount`(integer): Count of harsh cornering events. `Example: 1`

## **Sample Input**

```
https://intouch.mappls.com/iot/api/device/drive?deviceId=10807208&startTime=1736312926&endTime=1736412886
```
## **Sample Output**

```json
{
    "data": [
        {
            "deviceId": 10807208,
            "location": {
                "startAddress": "Acharya Shree Tulsi Das Marg, Aravalli Biodiversity Park, Gurugram, Haryana. 2 m from Metro Pillar No 9, Pin-122002 (India)",
                "endAddress": "Lado Sarai, New Delhi, Delhi. 248 m from Delhi Jal Board Government of NCT (India)",
                "startTimestamp": 1736388443,
                "endTimestamp": 1736389221,
                "avgSpeed": 42.39,
                "startLat": 28.4816017,
                "startLon": 77.112845,
                "endlat": 28.515034,
                "endLon": 77.1923069
            },
            "movement": {
                "duration": 778,
                "distance": 12.71,
                "idleTime": 130,
                "movementTime": 466,
                "stoppageTime": 182
            },
            "drivingBehaviourCount": {
                "haCount": 0,
                "hbCount": 0,
                "hcCount": 0
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

