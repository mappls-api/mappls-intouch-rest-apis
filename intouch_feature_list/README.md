[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# InTouch APK - Features List

## **Introduction**

`Mappls InTouch APK` is a powerful tracking application designed to demonstrate the capabilities of the
InTouch SDK. It allows developers to experience how real-time location tracking works using various tracking
modes, one-time location fetch, and geolocation-based tracking.

![Intouch APK](/intouch_feature_list/docs/image1.jpg)

This APK serves as a sample implementation for developers integrating InTouch SDK into their own apps,
enabling accurate telematics, location intelligence, and device activity tracking.

## **Key Features**

### 1. **Device Initialization**
- Before using any tracking features, the Device must be initialized.
- **`InTouch SDK supports two ways to initialize a device`**:
   1. SDK initializes with device name, and self generated deviceId - useful when tracking devices when there is no unique userId available from the consuming application.
   2. SDK initializes with device name and client app's uniqueId (which can be that user's ID); thereby ensuring that even if the user changes his device, the same device name persists for that user's data.

- **`Required Inputs`**:
   - Device Name (User-defined)
   - Client ID (Provided by Mappls)
   - Client Secret (Provided by Mappls)
- After filling in the details, click on Initialize to register the device with InTouch Platform.

![Intouch Initialization](/intouch_feature_list/docs/Initialize_Intouch%20_apk.gif)

### 2. **Tracking Priority Modes**
   Once initialized, you can select a Tracking Priority Mode based on your use case:
   | **Priority Mode** | **Data Sending Frequency** | **Suitable Use Case** |
   | --- | --- | --- |
   | Fast | Every 5 seconds | Real-time logistics, delivery tracking |
   | Optimal | Every 10 seconds | Employee tracking, regular location updates |
   | Slow | Every 15 seconds | Low-power mode, occasional tracking |
   | Custom | Developer-defined interval | Flexible custom needs |
   | Driving Mode | Smart tracking during vehicle movement | Dynamic tracking for vehicle telematics |

![Intouch APK](/intouch_feature_list/docs/image2.png)

   - **`Purpose`**: These modes help balance between accuracy and battery efficiency.

### 3. **Start Tracking**
   - Once Priority is set, click Start Tracking to begin continuous location tracking.
   - Real-time data such as Latitude, Longitude, Accuracy, Network Provider Info, GPS Provider Status, Road Details, etc. are displayed on the UI.
   - Tracking data is pushed to the InTouch Platform where it is visible on the InTouch Dashboard and accessible via APIs.
  
![Start Tracking](/intouch_feature_list/docs/start_tracking.gif
)

### 4. **Stop Tracking**
   At any time, tracking can be stopped by clicking Stop Tracking. Final data packet is sent before stopping to ensure latest position is captured.

![Stop Tracking](/intouch_feature_list/docs/Stop_intouch_tracking.gif)

### 5. **One-Time Location Fetch**
   - This feature allows fetching the current device location just once, without continuous tracking.
   - **`Useful for`**:
      - Check-in apps
      - Attendance marking
      - Location-based services requiring snapshot location

### 6. **One-Time Location from Geolocation**
   - This feature allows fetching the current device location just once, without continuous tracking.
   - **`Useful for`**:
      - Check-in apps
      - Attendance marking
      - Location-based services requiring snapshot location
      
### 7. **Location Permissions Handling**
   - During setup, the APK requests several critical permissions. Each permission is important for reliable tracking:
      - **`Location (All time access)`**: For accurate and background tracking
      - **`Physical Activity`**: To detect motion changes (e.g., walking, driving)
      - **`Nearby Devices`**: For proximity-based triggers
      - **`Phone Call Access`**: To detect call events during tracking (optional)
      - **`Notifications`**: For alerting users about tracking state

![Permissions handling](/intouch_feature_list/docs/image3.png)![Permissions handling](/intouch_feature_list/docs/image4.png)

   - **`User Flow for Permissions`**:
      - **`Allow Location (All the time)`**: Essential
      - **`Allow Physical Activity`**: Recommended
      - **`Allow Nearby Devices`**: Recommended
      - **`Allow Notifications`**: Optional
      - **`Allow Call Access`**: Optional


![User flow for Permissions](/intouch_feature_list/docs/image5.png)


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




