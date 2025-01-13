
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Trip Creation API

## **Introduction**

The ***`Create a Trip`*** API is designed to facilitate the creation of new trips within a system. By providing relevant parameters such as `device ID`, `destination`, `geofences`, and `trip details`, users can create and plan trips programmatically. This API allows businesses or applications to integrate trip creation functionalities seamlessly into their workflows, enabling real-time trip tracking, optimization, and reporting.

The API is highly customizable, allowing you to specify various parameters such as trip name, destination coordinates, geofence setup, and more. Additionally, it offers flexible options for trip closure and metadata management. With this API, users can not only create trips but also ensure that the trips are optimized and efficiently managed within the system.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://www.mapmyindia.com/api/advanced-maps/doc/authentication-api.php).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/json`**
 

## **Input Method:** 
- POST


## **Input URL:**

 > https://intouch.mappls.com/iot/api/v2.0/trips


## **Request Body Parametrs**

The request must have a JSON body with the below keys and their data types:

- **`deviceId`**(number): The ID of the device for which the trip is being created. `Example: 12345`

- **`name`**(string): Name of the trip. `Example: Business Trip`

- **`forceClose`**(boolean): Indicates if the trip should automatically close when the device is associated with another trip.  
  Example: true

- **`closureType`**(integer): Defines Type of closure. `1` - trip will get closed based on the planned end time, `2` - trip will close when the device enters the destination area/geofence, and `3` - trip will get closed manually by the user. `Example: 1`

- **`plannedEndTime`**(number): Tentative time when the trip is expected to end. Required if `closureType` is set to 1. `Example: 1591891234`

- **`metadata`**(string): Custom metadata for the trip in a key-value format. `Example: { "myattribute": "sample text" }`
- **`destination`**(object): Specifies the destination of the trip (optional). If omitted, the trip will still be created.  
  - **`geometry`**:  
    - **`type`**(string): The geometry type, either Point or Polygon. `Example: Point`  
    - **`coordinates`**(number): Latitude and longitude of the destination. `Example: [77.234, 28.456]` 
  - **`radius`**(number): The radius of the destination point. `Example: 100`  
  - **`name`**(string): Name of the destination point or geofence. `Example: Office` 
  - **`plannedTime`**(number): Planned time for the device to reach the destination. `Example: 1591895678`  
  - **`metadata`**(string): Custom metadata for the destination in a key-value format. `Example: { "myattribute": "sample text" }`
- **`geofences`**: Defines geofences for the trip (optional). Each geofence includes:  
  - **`geometry`**:  
    - **`type`**(string): The geometry type, either Point or Polygon. `Example: Point` 
    - **`coordinates`**(number): Latitude and longitude of the geofence. `Example: [77.234, 28.456]` 
  - **`radius`**(number): The radius of the geofence. `Example: 150` 
  - **`name`**(string): Name of the geofence. `Example: Warehouse`  
  - **`plannedTime`**(number): Planned time for the device to reach the geofence. `Example: null` 
  - **`metadata`**(string): Custom metadata for the geofence in a key-value format. `Example: { "myattribute": "sample text" }`

- **`isOptimizedTrip`**(boolean): Indicates whether route optimization (stop reordering) should be performed. This does not affect the start or destination if provided. `Example: true`

 
## **Response Type**
- JSON

## **Response Codes** {as HTTP response code}

### **Success**

1. 201 - *`Created`* - The trip was successfully created.
2. 203 - *`Device Not Found`* - The provided deviceId is not found or invalid.

### **Client-Side Issues**
3. 400 - *`Bad Request`* - Invalid request, possibly due to an invalid ID or data type.
    -  Example:
 ```json
{
  "status": "error",
  "message": "Invalid ID supplied",
  "error": "Invalid deviceId"
}
```

4. 401 - *`Unauthorized`* - The API request is forbidden, possibly due to missing or invalid authorization credentials.
5. 404 - *`Not Found`* - The requested URL endpoint does not exist.


## **Sample cURL**

```bash
curl --location 'https://intouch.mappls.com/iot/api/v2.0/trips' \
--header 'accept: */*' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Content-Type: application/json' \
--header 'Cookie: HttpOnly; HttpOnly' \
--data '{
    "deviceId": 10647019,
    "name": "Vandana-test",
    "forceClose": true,
    "closureType": 1,
    "plannedEndTime": 1591891234,
    "metadata": {
        "myattribute": "sample text"
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
        "name": "string",
        "plannedTime": 0,
        "metadata": {
            "myattribute": "sample text"
        }
    },
    "geofences": [
        {
            "geometry": {
                "type": "Point",
                "coordinates": [
                    77.234,
                    28.456
                ]
            },
            "radius": 100,
            "name": "string",
            "plannedTime": null,
            "metadata": {
                "myattribute": "sample text"
            }
        }
    ],
    "isOptimizedTrip": true
}'

```

## **Sample Output**

```json
{
    "tripId": "676cef71f7b03b1054a1cf8a",
    "deviceId": 10647019,
    "destination": {
        "geometry": {
            "type": "Point",
            "coordinates": [
                77.234,
                28.456
            ]
        },
        "radius": 100,
        "plannedTime": 1591891234,
        "metadata": {
            "myattribute": "sample text"
        },
        "name": "string",
        "sequence": 2
    },
    "geofences": [
        {
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
            "sequence": 1,
            "jobId": "676cef71f7b03b1054a1cf8b",
            "links": {
                "embedUrl": "https://intouch.mapmyindia.com/widget/jobs/#/676cef71f7b03b1054a1cf8b?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
            }
        }
    ],
    "metadata": {
        "myattribute": "sample text"
    },
    "closureType": 1,
    "plannedEndTime": 1591891234,
    "plannedStartTime": 1735192433,
    "forceClose": true,
    "name": "Vandana-test"
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

