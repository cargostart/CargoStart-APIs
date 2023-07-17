
---
title: "Partial or incomplete data"
linkTitle: "Partial data"
type: docs
weight: 30
---

The correct operational process consists of transmitting FWB and FHL messages to the Carrier at the end of the shipment. However, in some cases, for example, when the House (HAWB) management happens in two or more different branches, there is a possibility to send partial or incomplete data.

In these cases, data contained in such flows will be transmitted to the Ecosystem but not the Carrier.

The branch in charge will generate the total flows according to the normal process. Then, it will transmit them to the Ecosystem and the Carrier.

**Example:**

The Rome branch of freight forwarder X will create FWB and FHL partial data that will be inserted in a specific folder *root* **FTP**. After receiving the messages, our system will only validate and transmit them to the Ecosystem.

The Milan branch will complete the data compilation and will generate the final FWB to submit, as per the standard process, in the CargoStart FTP folder. Finally, our system will analyse and normalise the message and transmit all the extracted information to the Ecosystem and to the Carrier.

#### EXAMPLE OF STANDARD TRANSMISSION

<img title="Standard Transmission" alt="Standard Transmission Flow" src="/Images/StartCity/StartCityStandardTT.png">

#### EXAMPLE OF PARTIAL DATA

<img title="Partial Transmission" alt="Partial Transmission Flow" src="/Images/StartCity/StartCityPartialTT.png">


