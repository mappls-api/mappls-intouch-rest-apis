
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Retrieve Basic Information of Device API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/vandana-gupta8020/Intouch-APIs/tree/main/InTouch%20Fleet%20Management%20APIs).**

## **Introduction**
The `Retrieve Basic Information of Device API` is used to fetch the basic details of a registered device. It returns essential information such as device ID, registration number, manufacturer, model, color, type, activation status, and other related attributes including tyre size, chassis number, and initial odometer reading. You can use this API to retrieve details for a specific device or for all active devices.

### **Device Identification Requirements**
- Many InTouch APIs require a valid device `id` to retrieve device-specific data.
- If the device `id` is not available, this API can be used to fetch the list of registered devices.
- The `id` returned in the response can then be used in other APIs that require a device identifier.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method:** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices/info

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**

- `200(OK)`: The operation was successful, and the requested information is returned.
- `204(No Content)`: The request was successful, but no data was found for the given parameters.
- `400(Bad Request)`: Request - Invalid device ID supplied or an incorrect data type was passed (e.g., string instead of integer).
- `401(Unauthorized)`: The request is forbidden due to missing or invalid authentication credentials.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**
| **Parameter** | **Type** | **Location** | **Description** | **Example** |
| --- | --- | --- | --- | --- |
| `id` | integer | query | The unique identifier of the device. This parameter is `optional`. If not provided, the API returns information for all active devices. | `53450`, `53451`, `7095391` |

## **Response Parameters**
- **`data`**(array): Contains the basic details of the device(s).
  - **`id`**(integer): Description: Unique identifier for the device.
  - **`name`**(string): Name of the device.
  - **`type`** (integer): Indicates the type of device. Possible values are:  
       - `0`: Car  
       - `1`: Person  
       - `2`: Asset  
       - `3`: Bike  
       - `4`: Bus  
       - `5`: Truck  
       - `6`: Tractor  
  - **`creationOn`**(number): Timestamp (date) representing when the device was created.
  - **`updationOn`**(number): Timestamp (date) representing when the device was updated.
  - **`expiryDate`**(number): Timestamp (date) representing when the device will expire or no longer be valid.
  - **`active`**(boolean): Indicates whether the device is active.
       - `true`: Device is active  
       - `false`: Device is inactive 
  - **`registrationNumber`**(string): The registration number associated with the device.
  - **`manufacturer`**(string): Name of the manufacturer of the device.
  - **`model`**(string): Model type of the device.
  - **`color`**(string): Color of the device.
  - **`geofenceIds`** (array of numbers): IDs of the geofences associated with the device.
  - **`tag`**(array of strings): Tag a vehicle with custom string value.
  - **`chasisNo`**(string): The chassis number of the device.
  - **`initialOdometer`**(number): Initial odometer reading of the device.
  - **`vehicleType`** (string): Indicates the specific category or body type of the vehicle.
  - **`makeYear`** (integer): The manufacturing year of the vehicle/device.
  - **`tyreSize`** (integer): Represents the size of the vehicle's tyres (in inches).
  - **`city`** (string): The city associated with the device or vehicle (if available).



## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/devices/info?id=53450%2C%2053451%2C%207095391' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response**
```json
{
    "data": [
        {
            "id": 53450,
            "name": "HR26BN0666-I20",
            "type": 5,
            "creationOn": 1516364087,
            "updationOn": 1768219821,
            "expiryDate": 1645122600,
            "active": true,
            "registrationNumber": "HR26BN0666",
            "manufacturer": "Hyundai",
            "model": "Elite i20",
            "vehicleType": "Tanker",
            "color": "White",
            "makeYear": 2022,
            "tyreSize": 15,
            "geofenceIds": [
                438141
            ],
            "chasisNo": "",
            "initialOdometer": 0.0
        },
        {
            "id": 53451,
            "name": "KA03MX6275_GPS",
            "type": 0,
            "creationOn": 1769000459,
            "updationOn": 1769000459,
            "expiryDate": 1547857126,
            "active": true,
            "registrationNumber": "2343434343",
            "manufacturer": "Aprilia",
            "model": " Tuono 150 ",
            "vehicleType": "SUV",
            "color": "Blue",
            "makeYear": 2019,
            "tyreSize": 16,
            "chasisNo": "MA3EJKD1S00895885",
            "initialOdometer": 95279.5
        },
        {
            "id": 7095391,
            "name": "<a href=\"http://evil.com\">hello2</a>",
            "type": 1,
            "updationOn": 1704452464,
            "active": true,
            "registrationNumber": "7685",
            "manufacturer": "Mahindra ",
            "model": "QUANTO",
            "vehicleType": "Move",
            "color": "black",
            "makeYear": 2020,
            "tyreSize": 14,
            "geofenceIds": [
                438127
            ],
            "tag": [
                "kaveesh"
            ],
            "chasisNo": "7890456",
            "city": "<a href=\"http://evil.com\">hell",
            "initialOdometer": 78999.0
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




