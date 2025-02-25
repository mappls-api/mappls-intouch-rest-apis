
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Retrieve Basic Information of Device

## **Introduction**

This API allows you to retrieve basic information about devices, including their registration number, manufacturer details, and other attributes such as tyre size and additional specifications.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**
- **Content-Type: `application/json`**


## **Input Method:** 
- GET

## **Input URL**

> https://intouch.mappls.com/iot/api/devices/info

## **Response Type**
- JSON

## **Response Codes {as HTTP response code}**

- `200(OK)`: The operation was successful, and the requested information is returned.
- `204(No content found)`: The request was successful, but no data was found for the given parameters.
- `400(Bad Request)`: Request - Invalid device ID supplied or an incorrect data type was passed (e.g., string instead of integer).
- `401(Unauthorized)`: The request is forbidden due to missing or invalid authentication credentials.
- `404(Not Found)`: The specified URL was not found.

## **Request Parameters**

| Parameter | Type | Location | Description | Example |
| --- | --- | --- | --- | --- |
| `id` | integer | query | The unique identifier of the device. If not provided, the API returns the info for all active devices. | `10647019` |

## **Response Parameters**

- **`devicebasicinfoobject`**
- **`data`**(array): Contains the basic details of the device(s).
  - **`id`**(integer): Description: Unique identifier for the device. `Example: 10647019`
  - **`name`**(string): Name of the device. `Example: vandana-test`
  - **`type`** (integer): Indicates the type of device. `Example: 1` Possible values are:  
       - `0`: Car  
       - `1`: Person  
       - `2`: Asset  
       - `3`: Bike  
       - `4`: Bus  
       - `5`: Truck  
       - `6`: Tractor  
  - **`creationOn`**(number): Timestamp(date) representing when the device was created. `Example: 1734690896`
  - **`updationOn`**(number): Timestamp(date) representing when the device was updated. `Example: 1735035848`
  - **`expiryDate`**(number): Timestamp(date) representing when the device will expire or no longer be valid. `Example: 1766226895`
  - **`active`**(boolean): Indicates whether the device is active. `Example: true`    
       - `true`: Device is active  
       - `false`: Device is inactive 
  - **`registrationNumber`**(string): The registration number associated with the device. `Example: d0369b5adb381a23`
  - **`manufacturer`**(string): Name of the manufacturer of the device. `Example: BMW`
  - **`model`**(string): Model type of the device. `Example: X3`
  - **`color`**(string): Color of the device. `Example: Blue`
  - **`geofenceIds`** (array of numbers): IDs of the geofences associated with the device. `Example: 283044`
  - **`tag`**(array of strings): Tag a vehicle with custom string value. `Example: xyz_mytag`
  - **`chasisNo`**(string): The chassis number of the device. `Example: EXASDSSSSADC`
  - **`initialOdometer`**(number): Initial odometer reading of the device. `Example: 0`


## **Sample Input**

```
https://intouch.mappls.com/iot/api/devices/info?id=10647019
```

## **Sample Output**

```json
{
    "data": [
        {
            "id": 10647019,
            "name": "vandana-test",
            "type": 1,
            "creationOn": 1734690896,
            "updationOn": 1735035848,
            "expiryDate": 1766226895,
            "active": true,
            "registrationNumber": "d0369b5adb381a23"
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




