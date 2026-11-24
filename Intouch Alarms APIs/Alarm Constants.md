
[<img src="https://about.mappls.com/about/images/MAPPLS-MapmyIndia-logo.png" height="40"/> </p>](https://about.mappls.com/api/)

# Alarm Constants
This document lists all supported alarm constants and their corresponding subtype (*`type`*) values used across the Alarm APIs.

## Alarm Types
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| `ALARM_IGNITION` | 21 | Ignition status alarm |
| `ALARM_OVERSPEED` | 22 | Overspeed alarm |
| `ALARM_UNPLUGGED` | 23 | Device unplugged alarm |
| `ALARM_PANIC` | 24 | Panic/SOS alarm |
| `ALARM_GEOFENCE` | 26 | Geofence alarm |
| `ALARM_STOPPAGE` | 27 | Vehicle stoppage alarm |
| `ALARM_IDLE` | 28 | Vehicle idle alarm |
| `ALARM_TOWING` | 29 | Vehicle towing alarm |
| `ALARM_GPRS_CONNECTIVITY` | 126 | GPRS connectivity alarm |
| `ALARM_VEHICLE_BATTERY` | 129 | Vehicle battery alarm |
| `ALARM_MILEAGE` | 133 | Mileage alarm |
| `ALARM_GPS_CONNECTIVITY` | 146 | GPS connectivity alarm |
| `ALARM_DISTANCE_COVERED` | 151 | Distance covered alarm |
| `ALARM_INTERNAL_BATTERY_VOLTAGE` | 161 | Internal battery voltage alarm |


## Alarm Subtypes (`type`)
> **Note:** The meaning of the *`type`* field depends on the selected `alarmType`.

### 1. Panic Alarm
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| General | 0 | General panic alarm |
| Critical | 1 | Critical panic alarm |
| Warning | 2 | Warning panic alarm |

### 2. Ignition Alarm
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| `ALARM_IGNITION_ON_OFF` | 1 | Trigger on both ignition ON and OFF |
| `ALARM_IGNITION_ON` | 2 | Trigger only on ignition ON |
| `ALARM_IGNITION_OFF` | 3 | Trigger only on ignition OFF |
| `ALARM_DAY_FIRST_IGNITION` | 5 | Trigger on the first ignition ON of the day |

### 3. Overspeed Alarm
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| Value Based | 0 | Trigger when configured speed limit is exceeded |
| Route/Geofence Based | 1 | Trigger based on route or geofence speed limit |

### 4. Unplugged Alarm
| **Constant** | **Description** |
| :--- | :--- |
| Always | Trigger whenever the device is unplugged |
| Conditional | Trigger only when configured conditions are met |

> This alarm does not use numeric `type` values.

### 5. Geofence Alarm
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| `ALARM_GEOFENCE_ENTRY_EXIT` | 1 | Trigger on both entry and exit |
| `ALARM_GEOFENCE_ENTRY` | 2 | Trigger only on entry |
| `ALARM_GEOFENCE_EXIT` | 3 | Trigger only on exit |
| `ALARM_GEOFENCE_STAY_LONG` | 4 | Trigger when vehicle stays inside the geofence longer than the configured duration |

### 6. Stoppage Alarm
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| General | 0 | General stoppage alarm |
| Critical | 1 | Critical stoppage alarm |
| Warning | 2 | Warning stoppage alarm |

### 7. Idle Alarm
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| General | 0 | General idle alarm |
| Critical | 1 | Critical idle alarm |
| Warning | 2 | Warning idle alarm |

### 8. Mileage Alarm
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| `ALARM_MILEAGE_DAILY` | 0 | Daily mileage |
| `ALARM_MILEAGE_MONTHLY` | 1 | Monthly mileage |

### 9. Distance Covered Alarm
| **Constant** | **Value** | **Description** |
| :--- | :---: | :--- |
| `ALARM_DISTANCE_COVERED_ATLEAST` | 1 | Trigger when distance covered is at least the configured value |
| `ALARM_DISTANCE_COVERED_ATMOST` | 2 | Trigger when distance covered is at most the configured value |

### 10. Towing Alarm
This alarm does not define any subtype (`type`) values.

### 11. GPRS Connectivity Alarm
This alarm does not define any subtype (`type`) values.

### 12. GPS Connectivity Alarm
This alarm does not define any subtype (`type`) values.

### 13. Vehicle Battery Alarm
This alarm does not define any subtype (`type`) values.

### 14. Internal Battery VoltageAlarm
This alarm does not define any subtype (`type`) values.




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
