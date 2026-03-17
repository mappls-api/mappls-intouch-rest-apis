
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Fetch Entities Group API

> **Before consuming the InTouch APIs, please complete the required [Prerequisites](https://github.com/mappls-api/mappls-intouch-rest-apis/tree/main).**

## **Introduction**
The `Fetch Entities Groups API` allows you to retrieve a list of all entities groups associated with a specific developer. developers can specify a particular group’s details by passing the groupId, if not provided, the API returns all entity groups associated with the account. By providing the necessary token key, this API returns details about each group, including group names, IDs, device associations, and timestamps for creation and updates. With this API, you can easily track, organize, and review your device groups, ensuring smooth management across your platform. Whether you need to retrieve all groups or filter by specific criteria, this API provides a quick and efficient way to get the information you need.
> **Note:** Ensure the required groups are already created. If not, use the [Create Entities Group API](https://github.com/mappls-api/mappls-intouch-rest-apis/blob/main/Intouch%20Entities%20Group%20APIs/Create%20Entities%20Group%20API.md) to create them.

## **Security Type**
This API follows OAuth2 based security. To generate the authorization token, please use the token generation API. More details are available [here](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).

## **Request Headers**

The API leverages OAuth 2.0 based security. Hence, the developer needs to send a request for an access token using their client_id and client_secret to the OAuth API. Once validated by the OAuth API, the `access_token` and `token_type` must be sent in the Authorization header with the value: **`{token_type} {access_token}`.**

- **Authorization: `{token_type} {access_token}`**

- **Content-Type: `application/json`**
 

## **Input Method** 
- GET

## **Input URL**
> https://intouch.mappls.com/iot/api/groups

## **Request Parametrs**
| **Name** | **Type** | **Required** | **Description** |
| :--- | :--- | --- | :--- |
| `id` | Array[long] | No | This is the Group ID. If provided, the API returns details of the specified device group. If not provided, the API returns a list of all device groups associated with the developer. |

## **Response Codes**
| **Code** | **Description** |
| :--- | :--- |
| `200(Successful operation)` | The request was successful, and a list of device groups is returned in JSON format. |
| `203(Device Not Found)` | No device matches the specified criteria. |
| `204(No Content)` | The request was successful, but there is no content to return. |
| `400(Bad Request)` | Invalid ID supplied or invalid data type. |
| `401(Unauthorized Request)` | The request is forbidden due to lack of proper authorization. |
| `404(Not Found)` | The URL was not found. |

 ## **Response Parameters**
- **`data`** (array of objects): List of entity groups associated with the developer.
     - *`id`*(number): This is group ID. `Example: 8232`
     - *`deviceIds`* (array[number]): List of device IDs associated with the group. Example: [10647019, 2986152, 3042309]
     - *`name`*(string): Name of the group. `Example: "MapmyIndia(testing_device)"`
     - *`createdOn`*(number): Unix timestamp when the group was created. `Example: 1736924435`
     - *`updatedOn`*(number): Unix timestamp when the group was last updated. `Example: 1736924435`
     - *`colorCode`*(string): The color associated with the group, if available. `Example: #8562bf`

## **Sample cURL Request**
```bash
curl --location 'https://intouch.mapmyindia.in/iot/api/groups?id=2803%2C%202427%2C%201871' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6' \
--header 'Cookie: HttpOnly'
```

## **Sample Output Response**
```json
{
    "data": [
        {
            "id": 1871,
            "name": "Test321",
            "deviceId": [
                443187
            ],
            "createdOn": 1565152976,
            "updatedOn": 1589867065,
            "colorCode": "#224ae6"
        },
        {
            "id": 2427,
            "name": "Narayan",
            "deviceId": [
                562573,
                562574,
                562575,
                562576,
                562582,
                562581,
                562580,
                562579,
                562583,
                562584,
                562587,
                562588,
                562589,
                562590,
                562591,
                562592,
                562586,
                562585,
                562577,
                562578
            ],
            "createdOn": 1603864761,
            "updatedOn": 1603864761
        },
        {
            "id": 2803,
            "name": "Bangalore updated",
            "deviceId": [
                28411
            ],
            "createdOn": 1611836561,
            "updatedOn": 1613045075,
            "colorCode": "#4527eb"
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

