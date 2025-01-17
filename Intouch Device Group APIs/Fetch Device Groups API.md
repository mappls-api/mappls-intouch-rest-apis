
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch Device Groups API

## **Introduction**

The *`Fetch Device Groups API`* allows you to *`retrieve a list of all device groups associated with a specific user`*. By providing the necessary token key, this API returns details about each group, including group names, IDs, device associations, and timestamps for creation and updates. Additionally, you can filter the results based on alarm IDs, device IDs, and alarm types, offering greater flexibility in managing your groups.

With this API, you can easily track, organize, and review your device groups, ensuring smooth management across your platform. Whether you need to retrieve all groups or filter by specific criteria, this API provides a quick and efficient way to get the information you need.

## **Security Type**
This API follows OAuth2 based security. To know more on how to create your authorization tokens, please use our authorization token URL. More details available [here](https://github.com/mappls-api/mappls-rest-apis/tree/main/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer would need to send a request for access token using their client_id and client_secret to the OAuth API. Once validated from the OAuth API, the access_token and the token_type need to be sent as Authorization header with the value: **`"{token_type} {access_token}”`.**

- **Authorization: `"{token_type} {access_token}”.`**
- **Content-Type: `application/json`**
 

## **Input Method:** 
- GET

## **Input URL:**
 > https://intouch.mappls.com/iot/api/group

## **Request Parametrs**

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| *`id`* | string | This is the alarm's ID, a non-mandatory parameter. If not passed then by default the API will return the list of all alarm configurations in the account. You can pass single value or comma separated alarm IDs for multiple values. |
| *`deviceId`* | string | This is device ID. API will return data based on the configs set for the passed device IDs. You can pass a single device ID or comma seperated multiple device IDs. |
| *`alarmType`* | string | This is alarm type. API will return data based on the passed alarm types. You can pass a single alarm type or comma seperated multiple alarm types. |

## **Response Codes**

| **Code** | **Description** |
| --- | --- |
| `200(Successful operation)` | The request was successful, and a list of device groups is returned in JSON format. |
| `203(Device Not Found)` | No device matches the specified criteria. |
| `204(No Content)` | The request was successful, but there is no content to return. |
| `400(Bad Request)` | Invalid ID supplied or invalid data type. |
| `401(Unauthorized Request)` | The request is forbidden due to lack of proper authorization. |
| `404(Not Found)` | The URL was not found. |

 ## **Response Parameters** 

The response from the Fetch Device Groups API returns a list of groups, with each group object containing the following attributes:

- **`groupobjresponse Parameters:`**
     - *`id`*(number): This is group ID. `Example: 8232`
     - *`deviceId`*(array of numbers): List of device IDs associated with the group. Example: [10647019, 2986152, 3042309]
     - *`name`*(string): Name of the group. `Example: "MapmyIndia(testing_device)"`
     - *`createdOn`*(number): Timestamp at which the group got created. `Example: 1736924435`
     - *`updatedOn`*(integer): Timestamp at which the group got updated. `Example: 1736924435`
     - *`colorCode`*(string): The color associated with the group, if available. `Example: #8562bf`

## **Sample Input**
```
https://intouch.mappls.com/iot/api/group?id=8232&deviceId=10647019,2986152,3042309&alarmType=26,22
```
## **Sample output**
```json
{
    "data": [
        {
            "id": 8232,
            "name": "MapmyIndia(testing_device)",
            "deviceId": [
                10647019,
                2986152,
                3042309
            ],
            "createdOn": 1736924435,
            "updatedOn": 1736924435,
            "colorCode": "#8562bf"
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

