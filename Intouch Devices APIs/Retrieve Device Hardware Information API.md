
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Retrieve Device Hardware Information API

## **Introduction**

This API returns hardware-related information of devices, including their IMEI numbers, GSM numbers, device types, and more. It provides essential hardware details for managing and monitoring devices.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/devices/hardwareInfo

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- `200(OK)`: Successful operation, the API call was processed successfully and content is returned.
- `204(No content found)`: No content found, this occurs when the device ID does not exist or no hardware information matches the query.
- `400(Bad Request)`: Invalid device ID supplied or device id is missing or invalid data type. For example, input attribute id is integer but string value gets passed.
- `401(Unauthorized)`: Access to the API is forbidden due to missing or invalid authorization credentials.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**

| Parameter | Type | Location | Description | Example |
| --- | --- | --- | --- | --- |
| `id` | integer | query | This is the physical device's ID, a non-mandatory parameter. If not passed, the API will return hardware info of all active devices in the account. | `1363489` |

## **Response Parameters**
- ***`devicehardwareinfoobject`***
  - **`data`**(array): Contains hardware details of the device(s).
      - **`id`**(integer): Id of the physical hardware device. `Example: 0`

      - **`name`**(string): The name of the physical hardware device. `Example: MMI314295`
        
      - **`deviceType`**(integer): type of device for eg; drivate, vt etc. `Example: 868728030749458`

      - **`deviceTypeName`**(string): Name of the type of device. `Example: drive mate pro`

      - **`trackingCode`**(string): Tracking code/unique code number of the device. `Example: 868728030749458`

      - **`deviceCode`**(string): Another unique number, genrally same as tracking code. `Example: 868728030749458`

      - **`active`**(boolean): Indicates whether the device is active. `Example: true`
           - `true`: nactive
           - `false`: inactive

      - **`mappedDeviceIds`**(number): The ids of the entities which are linked to the id of the physical hardware device. `Example: 887876`

      - **`odometerType`**(integer): Specifies the type of odometer used by the device. `Example: 2`
          - `0`: Odometer not supported
          - `1`: GPS-based odometer (comes from the device)
          - `2`: CAN-based odometer (comes from vehicle's CAN bus)

      - **`installDate`**(number): Timestamp representing when the device was installed. `Example: 1581273000`

      - **`expiryDate`**(number): Timestamp representing when the device will expire or no longer be valid. `Example: 1600713000`

## **Sample Input**  

```
https://intouch.mappls.com/iot/api/devices/hardwareInfo?id=4734899
```

## **Sample Output** 

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




<div align="center">@ Copyright 2025 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

