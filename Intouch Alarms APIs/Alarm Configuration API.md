
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Alarm Configuration API
 
## **Introduction** 

The Alarm Configuration API allows the creation of alarms for single or multiple devices based on the provided input parameters. It supports a variety of alarm types and configurations for effective device monitoring. Some of the key alarms supported include *Geofence, Ignition, OverSpeed, Unplugged, Panic, Stoppage, Idle, Towing, GPRS Connectivity, Vehicle Battery, Mileage, GPS Connectivity, Distance Covered, and Internal Battery Voltage*.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}.`**

- **Content-Type: `multipart/form-data`**

## **Input Method:** 
- POST

## **Input URL**

> https://intouch.mappls.com/iot/api/alarm


## **Response Type**
- JSON

## **Response Codes**

| **Status Code** | **Description** |
| --- | --- |
| `201(OK)` | Alarm created successfully. |
| `203(Device Not Found)` | The specified device(s) could not be located. |
| `400(Bad Request)` | Invalid ID supplied or invalid data type. |
| `401(Unauthorized)` | Invalid token or Access to the API is forbidden. |
| `404(Not Found)` | Specified device or URL Not Found. |

## **Request Body Parameters**

- **`alarmType`**(integer): Type of alarm to create. Below are the alarm types and their corresponding IDs:
    - `IGNITION`: 21  
    - `OVERSPEED`: 22  
    - `UNPLUGGED`: 23  
    - `PANIC`: 24  
    - `GEOFENCE`: 26  
    - `STOPPAGE`: 27  
    - `IDLE`: 28  
    - `TOWING`: 29  
    - `GPRS CONNECTIVITY`: 126  
    - `VEHICLE BATTERY`: 129  
    - `MILEAGE`: 133  
    - `GPS CONNECTIVITY`: 146  
    - `DISTANCE COVERED`: 151  
    - `INTERNAL BATTERY VOLTAGE`: 161 

- **`deviceId`**(array): Device IDs of those devices for which the alarm configuration is done.

- **`type`**(integer): Specifies the type of alarm configuration. The values depend on the alarmType: 
    - For `Geofence(alarmType = 26)`:  
      - `2` : Entry  
      - `3` : Exit  
      - `1` : Entry & Exit  
      - `4` : Long stay in geofence  
    - For `Ignition(alarmType = 21)`:  
      - `1` : Both ON & OFF  
      - `2` : Ignition On  
      - `3` : Ignition Off  
      - `5` : Day's First Ignition ON  
    - For `Mileage(alarmType = 133)`:  
      - `0` : Daily  
      - `1` : Monthly  
    - For `Distance Covered(alarmType = 151)`:  
      - `1` : At Least  
      - `2` : At Most  

- **`duration`**(integer): Only required in case of *overspeed, stoppage, idle, towing, GPRS connectivity, vehicle battery, GPS connectivity, distance covered, internal battery alarm*.

- **`limit`**(integer):Only required in case of *overspeed, vehicle battery, mileage, distance covered, internal battery alarm*. 

- **`geofenceId`**(array): Only required when `alarmType` is `26` (Geofence). Accepts single or multiple geofence IDs separated by commas. 

- **`severity`**(integer): This basically defines the severity of the alarm. Use `0` for normal severity and `1` for high severity.

## **Sample curl resquest**

```bash
curl --location 'https://intouch.mappls.com/apis/api/alarm/' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Contant-type: multipart/form-data' \
--header 'Cookie: HttpOnly' \
--form 'alarmType="28"' \
--form 'entityIds="10647019"' \
--form 'severity="0"' \
--form 'duration="12324323"' \
--form 'description="\" Alerts when a vehicle is standing at a location for a prefixed time of 12324323 Sec. This time can be customized by you.\""'
```

## **Sample Output**

```json
{
    "id": 13400145
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


