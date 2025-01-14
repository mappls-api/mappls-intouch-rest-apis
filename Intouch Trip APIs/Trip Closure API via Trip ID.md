
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Trip Closure via Trip ID API

## **Introduction**

The *`Trip Closure via Trip ID`* API allows users to close a specific trip by providing the trip's unique ID. The trip is then marked as completed or closed within the system. This operation is essential for managing trips, particularly when a trip has been completed or needs to be officially closed for any other reason.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/json`**
 

## **Input Method:** 
- POST

## **Input URL:**

 > https://intouch.mappls.com/iot/api/v2.0/trips/{id}/close

## **Request Type**
- **Content-Type**: *`application/json`*

## **Response Type**
- **Content-Type**: *`application/json`*

## **Request Parameters**
- **Mandatory Parameter**

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| **`id`** | Number | This is the ID of the trip that you want to close. Example: `23545` |


## **Response Parameters**
- `200(OK)`: Successful operation.

- `203(Invalid Param)`: For eg; if trip id is not correct.

- `400(Bad Request)`: Invalid ID supplied or invalid data type.

- `401(Unauthorized)`: Access to API is forbidden.

- `404(Not Found)`: URL not found.

- `500 (Undocumented)`: Invalid ObjectId format.
- Example:-

```json
{
  "error": "invalid hexadecimal representation of an ObjectId: [1363489]"
}
```
>Note: Ensure ObjectId is a valid hexadecimal string.


## **Sample cURL Request**

 ```bash
curl --location --request POST 'https://intouch.mappls.com/iot/api/v2.0/trips/676cef71f7b03b1054a1cf8a/close' \
--header 'accept: */*' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly; HttpOnly'"
 ```
## **Sample Output**

```json
{
    "data": {
        "tripId": "676cef71f7b03b1054a1cf8a",
        "deviceId": 10647019,
        "deviceName": "Vandana-test ",
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
            "address": "unnamed road, asola, new delhi, delhi. pin-110074 (india)",
            "time": 0,
            "distance": 0.0,
            "name": "string"
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
                "address": "unnamed road, asola, new delhi, delhi. pin-110074 (india)",
                "time": 0,
                "distance": 0.0,
                "name": "string",
                "status": 0,
                "jobId": "676cef71f7b03b1054a1cf8b",
                "links": {
                    "embedUrl": "https://intouch.mappls.com/widget/jobs/#/676cef71f7b03b1054a1cf8b?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
                }
            }
        ],
        "status": 2,
        "metadata": {
            "myattribute": "sample text"
        },
        "closureType": 1,
        "forceClose": true,
        "name": "Vandana-test",
        "summary": {
            "startedOn": null,
            "duration": null,
            "distance": null,
            "endedOn": 1735195774,
            "delayedBy": null,
            "plannedEndTime": 1591891234,
            "plannedStartTime": 1735192433,
            "plannedDuration": 0,
            "plannedDistance": 0.0
        },
        "start": {
            "plannedTime": 1735192433
        },
        "links": {
            "embedUrl": "https://intouch.mappls.com/widget/trips/#/676cef71f7b03b1054a1cf8a?access_token=0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6"
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

