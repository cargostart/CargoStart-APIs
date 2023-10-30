
---
title: "Legend"
linkTitle: "Legend"
type: docs
weight: 20
---

**LEGEND OF CODES AND FIELDS SPECIFICATION**:


| Code | Mandatory | Name                      | Notes                                                        |
| :--: | :-------: | :------------------------ | :----------------------------------------------------------- |
|  CI  |     N     | Customer ID               | Numeric Customer Identification Code (for internal purposes) |
|  S   |     Y     | BORDEREAU SECURED         | 0 corresponds to FALSE and 1 to TRUE                         |
| BDX  |     N     | BORDEREAU ID              | Customer Identification for Bordereau		              |

|  H   |     C 	   | Handler                   | SmartCity Handler (es. MLE. ALH). Mandatory for Phase 2. For Phase 1, if not indicated, Ecosystem Cargo MXP assigns it automatically |
|  AG  |     Y     | Agent Code                |                                                              |
|  DN  |     Y     | Driver Name               |                                                              |
|  DT  |     Y     | Document Type             |                                                              |
|  DA  |     Y     | Document Issuer Authority |                                                              |
|  DI  |     Y     | Document Number           |                                                              |
|  PN  |     Y     | PLATE #                   | Can be Repeated                                              |
|  SN  |     Y     | SEAL #                    | Can be Repeated                                              |
|  CN  |     N     | DRIVER COMPANY NAME       | Name of the company for which the driver works.              |
|  TN  |     N     | TRUCK COMPANY NAME        | Name of the company to which the truck belongs.              |
| DN2  |     N     | DRIVER NAME               | 2nd DRIVER                                                   |
| DT2  |     N     | DOCUMENT TYPE             | 2nd DRIVER                                                   |
| DA2  |     N     | DOCUMENT AUTHORITY        | 2nd DRIVER                                                   |
| DI2  |     N     | DOCUMENT NUMBER           | 2nd DRIVER                                                   |
| CN2  |     N     | COMPANY NAME              | 2nd DRIVER    
