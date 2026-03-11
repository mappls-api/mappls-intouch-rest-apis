
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)


# Prerequisites for Using InTouch APIs
Before consuming the InTouch APIs, ensure the following prerequisites are met:

### **Mappls Console Login**
Developers must log in to the Mappls Console to manage subscriptions and API access.
- If the developer already has a registered email ID, they can directly log in to the [Mappls Console](https://apis.mappls.com/console).
- From the console, developers can click the [<img src="https://cdn-icons-png.flaticon.com/128/7465/7465995.png" height="36"/>](https://apis.mappls.com/console/#/freetrial-signup) **subscribe to InTouch** button from the credentials tab inside the Project.


### **Client Credentials (CI & CS)**
After subscribing to InTouch, developers get access to the InTouch APIs and can be accessed using:
- Client ID (CI)
- Client Secret (CS)

These credentials are mandatory for authenticating and accessing the InTouch APIs. They also provide access to the default enabled APIs.

### **API Access Mapping**
- Each Client ID and Client Secret is mapped to a specific project and can only consume APIs associated with that project.
- API requests will be rejected if the requested endpoint is not enabled for the associated CI/CS.
- Ensure all required APIs are properly mapped before starting integration.

### **API Usage Limits**
- Some APIs come with default hit limits, which define how many times an API can be accessed within a given period.

### **Credential Issuance & Validation**
Asset allocation, limit enhancement, and default access–related concerns are managed by the API team. For requesting, validating, or resolving issues related to CI/CS, please contact. apisupport@mapmyindia.com or apisupport@mappls.com

### **Authentication Token Generation**
- InTouch APIs use Bearer Token–based authentication.
- Users must generate a valid Bearer Token using their Client ID and Client Secret through the authentication endpoint by invoking the [Token Generation API](https://github.com/mappls-api/mappls-rest-apis/tree/auth-legacy/mappls-token-generation-api).
- Tokens are time-bound (24 hours) and must be regenerated upon expiration.


# InTouch Fleet Management APIs

This repository contains documentation for *`Intouch APIs`*, designed to streamline and optimize fleet management operations. With a focus on real-time tracking, reporting, and performance optimization, these APIs help businesses simplify logistics operations. They integrate critical data such as trip details, device statuses, alarms, historical events, device drive details, device groups, routes and route assignments, geofences, video telematics, charging events, and push event notifications, enabling seamless communication and better decision-making.

By leveraging Intouch APIs, companies can automate complex workflows, improve operational efficiency, and gain valuable insights for proactive fleet management. Whether it is monitoring charging events, receiving push-based event notifications, or tracking driver behavior, these APIs provide a comprehensive solution for managing and monitoring fleets efficiently.

## Table Of Content

- [Intouch Alarms APIs](./Intouch%20Alarms%20APIs)
- [Intouch Charging Events APIs](./Intouch%20Charging%20Events%20APIs)
- [Intouch Devices APIs](./Intouch%20Devices%20APIs)
- [Intouch Drive APIs](./Intouch%20Drive%20APIs)
- [Intouch Entities Group APIs](./Intouch%20Entities%20Group%20APIs)
- [Intouch Events APIs](./Intouch%20Events%20APIs)
- [Intouch Geofence APIs](./Intouch%20Geofence%20APIs)
- [Intouch Route APIs](./Intouch%20Route%20APIs)
- [Intouch Trip APIs](./Intouch%20Trip%20APIs)
- [Intouch Video Telematics APIs](./Intouch%20Video%20Telematics%20APIs)
- [Push Event API](./Push%20Event%20API.md)










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

