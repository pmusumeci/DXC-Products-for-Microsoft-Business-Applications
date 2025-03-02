---
# required metadata

title: EDI Vendor
description: EDI Vendor setup - Order line change type group
author: jdutoit2
manager: Kym Parker
ms.date: 2021-11-09
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  SAB_EDIVendOrderLineChangeMapping
audience: Application User
# ms.devlang:
ms.reviewer: jdutoit2
# ms.tgt_pltfrm:
ms.custom: ["21901", "intro-internal"]
ms.search.region: IconEDIVendorDocuments
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jdutoit2
ms.search.validFrom:  2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Vendor setup
## Setup order line change type group

Users can access the form by navigating to **EDI > Setup > Vendor setup > Order line change type group**

Order line change type codes are used to identify the type of line change sent the the vendor in the Vendor purchase order change document.

-	Click **New** to create a new record. 
-	In the **Name** field, enter the name of the order line change type group
-	In the **Description** field, enter a description of the order line change type group
-	In the **Mappings** FastTab, select **Add** to create a new record
-	Select the **Order line change type**
-	Specify the vendor's value for the line change type in **EDI order change type**

The Order line change types are:

**Order line change type** 	        | **Description of D365 purchase order line change**            | **X12 examples**
:-----------------------------------|:-------------------------------------                         |:----------------:
**Add additional item**             | New purchase order line was added to existing purchase order	| AI
**Delete items**                    | Existing purchase order line’s Deliver remainder has been cancelled, or removed | DI
**Changes to line items**           | All other purchase order lines are sent with this code which indicates the vendor must replace with current info | CA


## Where used
Vendor EDI order line change type group is assigned on the [Vendor Trading partner's](../Trading-partner.md) Options field called **Order line change type**. <br>
Used on field **LineChangeType** on EDI documents:
- Vendor purchase order change

## Data entities:
- Vendor EDI order line change type group
- Vendor EDI order line change type group line
