
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Get Distance Traveled of the Device

## **Introduction**

This API provides precise details about the distance traveled by devices such as vehicles, assets, and people. The data is gathered using connected devices, sensors, or mobile applications to ensure location awareness. The API calculates the distance traveled during a specified time range, along with other related metrics.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://www.mapmyindia.com/api/advanced-maps/doc/authentication-api.php).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**

> https://intouch.mappls.com/iot/api/device​/{deviceId}​/distance?

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- `200(OK)`: The operation was successful, and the requested information is returned.
- `204(No content found)`: The request was successful, but no data was found for the given parameters.
- `400(Bad Request)`: Request - Invalid device ID supplied or an incorrect data type was passed (e.g., string instead of integer).

```json
{
  "error": "futuredateselected"
}
```
- `401(Unauthorized)`: The request is forbidden due to missing or invalid authentication credentials.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**

The **`“bold”`** one’s are mandatory, and the *`“italic”`* one’s are optional.

- **`deviceId`**(integer):The unique ID of the device. If not provided, the API will return data for all active devices.

- **`startTime`**(integer): The epoch timestamp representing the start of the time range for which the distance is to be calculated.

- **`endTime`**(integer): The epoch timestamp reresenting the end of the time range for which the distance is to be calculated.

- *`driveDistance`*(integer): parameter representing specific drive distance data.

- *`eventsOnly`*(integer): Query parameter representing the count or nature of events to be returned.


## **Response Parameters**

- **`driveDistance`**(number): Distance traveled based on drive-specific metrics. `Example: 18.590760091268244`

- **`distance`** (number): Total distance traveled during the specified period. `Example: 18.590760091268244`

- **`totalEvents`** (integer): The total number of events recorded during the period. `Example: 4976`

- **`movementTime`**(integer): The total duration (in seconds) of device movement. `Example: 2086`

- **`nogps`** (integer): Number of instances where no GPS signal was available. `Example: 2611`

- **`type`** (integer): The type of device for which data is returned. `Example: 0`

- **`idleTime`** (integer): Total idle time (in seconds) during the period. `Example: 14636`

- **`duration`** (integer): Total duration (in seconds) of the time period. `Example: 19333`

- **`obdConnection`** (integer/null): Represents the state of OBD (On-Board Diagnostics) connection. `Example: null`

- **`idealEvents`**(integer): The number of ideal (expected) events recorded. `Example: 1944`

- **`startTime`**(integer): The epoch timestamp representing the start of the period. `Example: 1709619447`

- **`endTime`** (integer): The epoch timestamp representing the end of the period. `Example: 1709638780`

- **`nogpsDistance`**(number): Distance traveled when GPS signal was unavailable. `Example: 0.36677663593731297`

## **Sample Input**

```
https://intouch.mappls.com/iot/api/device/10647019/distance?startTime=1735183358&endTime=1735203194
```

## **Sample Output**

```json
{
    "driveDistance": 16.891951380075835,
    "distance": 16.891951380075835,
    "totalEvents": 1195,
    "movementTime": 1353,
    "nogps": 211,
    "type": 0,
    "idleTime": 18013,
    "duration": 19577,
    "obdConnection": null,
    "idealEvents": 1190,
    "startTime": 1735183361,
    "endTime": 1735202938,
    "nogpsDistance": 0.5468242487884609
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

