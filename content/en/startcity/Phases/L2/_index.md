
---
title: "Phase L2"
linkTitle: "Phase L2"
type: docs
weight: 20
---

> PALLETISATION AND CARGO TRANSPORTATION

**Phase L2** concerns the palletisation and transportation of cargo. It includes data describing the **bordereau**, **transport security**, and the transmission of AWB partial data. This information is sent to the Ecosystem via a standard **IATA FFM** message.

The availability of such data allows a leaner process at the acceptance in Malpensa. The GHA operator will be able to:

- Verify the presence of the bordereau and other related information in the Ecosystem
- Verify the identity of the driver
- Collect the possible paper documentation

From a technical point of view, given that the OCI field in the FFM is repeatable because it is at the same master level, it is customary to provide the information as follows:

- Enter the ID line **ST** inside **the last OCI field** in the **FFM** for the information related to the **bordereau.**
- Optionally, Enter the OSI field for the possible identification of the customer/forwarder (**Customer Id**)

