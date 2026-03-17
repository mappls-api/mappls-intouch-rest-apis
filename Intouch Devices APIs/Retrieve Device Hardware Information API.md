
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Retrieve Device Hardware Information API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**

The `Retrieve Device Hardware Information API` is used to fetch hardware details of registered devices in your InTouch account. It returns information such as IMEI number, GSM number, device type, tracking code, installation details, and expiry information. 

This API helps in managing and monitoring device inventory, validating hardware mappings, and tracking device lifecycle information. Hardware details can be retrieved for a specific device, multiple devices, or all active devices in the account.

### **Device Identification Requirements**
- Certain APIs require a device identifier (such as `deviceId` or physical `id`) to be passed as part of the path or query parameters.
- If the deviceId is not already available, developers can retrieve a list of registered devices by invoking the [Retrieve Basic Information of Device API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Devices%20APIs/Retrieve%20Basic%20Information%20of%20Device%20API.md).
- The retrieved device details can then be used for subsequent API calls that require device-specific identifiers.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**


## **Input Method** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices/hardwareInfo

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**

- `200(OK)`: Successful operation. The API call was processed successfully and content is returned.
- `204(No content found)`: No content found. This occurs when the device ID does not exist or no hardware information matches the query.
- `400(Bad Request)`: Invalid device ID supplied, missing, or invalid data type.
- `401(Unauthorized)`: Access to the API is forbidden due to missing or invalid authorization credentials.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**
All parameters are `optional`. If no parameter is passed, the API returns hardware information for all active devices associated with the account.
| **Parameter** | **Type** | **Location** | **Description** |
| --- | --- | --- | --- |
| `id` | Array[long] | query | Physical entity ID(s) associated with the device hardware. Used to fetch hardware details for specific physical devices. |
| `deviceId` | Array[long] | query | Mapped device ID(s). Used to retrieve hardware information based on mapped device identifiers. |

> **Note:** Either `id` or `deviceId` can be passed. If both are provided, `id` will be prioritized. And if neither is passed, the API returns hardware details of all active devices under the authenticated account.

## **Response Parameters**
- **`data`**(array): Contains hardware details of the device(s).
    - **`id`**(integer): ID of the physical hardware device.
    - **`name`**(string): The name of the physical hardware device.       
    - **`deviceType`**(integer): Specifies the type of device (e.g., Drivmate, VT, Beacon, etc.).
    - **`deviceTypeName`**(string): Name of the type of device.
    - **`trackingCode`**(string): Tracking code/unique code number of the device.
    - **`deviceCode`**(string): Another unique number, generally the same as the tracking code.
    - **`active`**(boolean): Indicates whether the device is active.
        - `true`: Active device
        - `false`: Inactive device
    - **`mappedDeviceIds`**(array[number]): IDs of the entities linked to the physical hardware device.
    - **`odometerType`**(integer): Specifies the type of odometer used by the device.
        - `0`: Odometer not supported
        - `1`: GPS-based odometer (comes from the device)
        - `2`: CAN-based odometer (comes from vehicle's CAN bus)
    - **`installDate`**(number): Timestamp representing when the device was installed.
    - **`expiryDate`**(number): Timestamp representing when the device will expire or no longer be valid.

## **Sample cURL Request**  
```bash
curl --location 'https://intouch.mappls.com/iot/api/devices/hardwareInfo?id=4734899' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response** 
```json
{
    "data": [
        {
            "id": 4734899,
            "name": "pixel 7",
            "deviceType": 35,
            "deviceTypeName": "Beacon",
            "trackingCode": "9835012644DB5D66BC004231A4732F61D330E2AF83D7FCA0",
            "deviceCode": "a9cb09062e7002b3",
            "active": true,
            "mappedDeviceIds": [
                8801670
            ],
            "odometerType": 0,
            "expiryDate": 1749298148,
            "beacon": {
                "platform": "android",
                "platformVersion": "34",
                "make": "google",
                "model": "Pixel 7"
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

