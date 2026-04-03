
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Routes Retrieval API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Routes Retrieval API` allows you to retrieve route details associated with an InTouch user. By providing one or more route IDs, this API returns information such as the `route name`, `creation and update timestamps`, `route type,` and the list of associated `geofence IDs`. If no route ID is passed, the API will return all routes associated with the user. This API is useful for viewing, managing, or validating configured routes within the InTouch platform. 

> **Note:**  Ensure the required routes are already created. If not, Use the [Create Route API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Route%20APIs/Create%20Route%20API.md) to create them. .

## **Security Type**

This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**
- **Content-Type: `application/json`**

## **Input Method**
- GET

## **Input URL**
 > https://intouch.mappls.com/iot/api/route/

## **Response Type**
- JSON

## **Response Codes (HTTP Status Codes)**
| **HTTP Code** | **Message** | **Description** |
| :--- | :--- | :--- |
| `200` | OK | Route details fetched successfully. |
| `400` | Bad Request | The request is invalid or contains incorrect parameters.|
| `401` | Unauthorized | Invalid or missing access token. |
| `403` | Forbidden | API access not enabled for the provided CI/CS |
| `404` | Not Found | Route not found for the given ID(s) |
| `500` | Internal Server Error | Server-side error |


## **Request Parameters**
| **Parameter** | **Type**| **Required** | **Description** |  
| :--- | :--- | :--- | --- |
| *`id`* | Array[long] | No | One or more route IDs for which details need to be fetched. Multiple route IDs can be passed as a comma-separated list. |
| *`accountId`* | long | No | AcAccount ID associated with the user. If provided, the response is filtered for the specified account. |

## **Response Parameters**

| **Field** | **Type** | **Description** |
| :--- | :--- | :--- |
| **`id`** | long | Unique identifier of the route |
| **`name`** | string | Name of the route |
| **`createdOn`** | number | Route creation timestamp (epoch seconds) |
| **`updatedOn`** | number | Last updated timestamp (epoch seconds) |
| **`type`** | integer | Route category/type defined in the system |
| **`routeType`** | integer | Indicates the route behavior or classification |
| **`geofenceId`** | Array[long] | List of geofence IDs associated with the route |



## **Sample cURL Request**
```bash
curl --location 'https://intouch.mappls.com/iot/api/route/?id=74707%2C%2075074%2C%2075290' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly; HttpOnly'
```

## **Sample Output Response**
```json
[
    {
        "id": 74707,
        "name": "=Hyperlink(\"http://testphp.vulnweb.com/\",\"Free Coins\")",
        "createdOn": 1555481860,
        "updatedOn": 1735066096,
        "type": 0,
        "routeType": 1,
        "geofenceId": [
            438126,
            438127,
            438129,
            438135,
            438143,
            1090252,
            438129,
            1130662
        ]
    },
    {
        "id": 75074,
        "name": "Nitin_Test23",
        "createdOn": 1556004092,
        "updatedOn": 1738236902,
        "type": 2,
        "routeType": 1,
        "geofenceId": [
            438123,
            438125,
            438126
        ]
    },
    {
        "id": 75290,
        "name": "For_Test_Route_3",
        "createdOn": 1556170964,
        "updatedOn": 1556171963,
        "type": 2,
        "routeType": 1,
        "geofenceId": [
            416199,
            416200,
            416201,
            416202
        ]
    }
]
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

