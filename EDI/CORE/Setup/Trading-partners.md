---
# required metadata

title: EDI Core
description: EDI Core - Setup Trading partners
author: jdutoi2
manager: Kym Parker
ms.date: 2022-11-08
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  SAB_EDITradingPartner
audience: Application User
# ms.devlang: 
ms.reviewer: jdutoit2

# ms.tgt_pltfrm: 
ms.custom: ["21901", "intro-internal"]
ms.search.region: IconEDI
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jdutoit2
ms.search.validFrom:   2016-05-31
ms.dyn365.ops.version:  AX 7.0.1
---

# Trading partners

EDI works on the basis that an external entity (trading partner) wants to send or receive information from us. To this end, the module is built to link the documents and their associated settings to those entities (trading partners). <br>
A trading partner can be created based on an existing D365 entity like a warehouse, vendor or a customer. Depending on the various modules installed, different trading partner types will be available for setup.

## Prerequisites ##
Below modules are determined by licensing and enabled features.
- **Module setup/Mappings**: This can be assigned to the Trading partner to map Trading partner value to D365 value. 
  - [Customer setup](../../CUSTOMER/SETUP/Customer-setup.md)
  - [Vendor setup](../../VENDOR/SETUP/Vendor-setup.md)
  - [3PL setup](../../3PL/SETUP/3PL-setup.md)
  - [Freight forwarder landed cost setup](../../FREIGHT-FORWARDER/SETUP/Freight-forwarder-setup.md)
- **Document types**: Template, setting profile, outbound filenames for each applicable document type will be assigned to the Trading partner.
  - [Customer document types](../../CUSTOMER/INTRODUCTION/Introduction.md#customer-document-type-setup)
  - [Vendor document types](../../VENDOR/INTRODUCTION/Introduction.md#vendor-document-type-setup)
  - [3PL document types](../../3PL/INTRODUCTION/Introduction.md#3pl-document-type-setup)
  - [Freight forwarder landed document types](../../FREIGHT-FORWARDER/INTRODUCTION/Introduction.md#freight-forwarder-document-type-setup)

## Setup Trading partners
Users can access the form by navigating to **EDI > Setup > Trading partners**.

The Trading partner provides a centralized location to manage all trading partners. <br>
Create new Trading partner:
- To create a new record, select **New**
- Select the trading partner **Type**. Available options depends on licensing and enabled features.
- Select the Trading partner's **Company**
-	Select the **Account number**. Only account numbers for the selected company that are not assigned for the specified trading partner type are available.
-	Enter the **Trading partner GLN**. This value will be used in the Import-to-staging step to create the incoming staging against the correct Trading partner GLN and should thus be provided in the Inbound file. The Trading partner GLN is required to be unique by Type.
-	Select **Create**, then complete the remaining setup for the trading partner.

Copy existing Trading partner:
- To create a new record by copying an existing trading partner, select the applicable trading partner to copy and select **Copy**
- Select the new Trading partner's **Company**
-	Select the **Account number**. Only account numbers for the selected company that are not assigned for the specified trading partner type are available.
-	Enter the **Trading partner GLN**. This value will be used in the Import-to-staging step to create the incoming staging against the correct Trading partner GLN and should thus be provided in the Inbound file. The Trading partner GLN is required to be unique by Type.
-	Select **Copy**, then complete/update the remaining setup for the trading partner.

### Trading partner list

**Field** 	                      | **Description**
:-------------------------------- |:-------------------------------------
**Trading partner GLN**           |	The GLN we know the trading partner as. <br> This field denotes the trading partner GLN. The module will use this field as a match to <br> • Customer trading partner: Customer account <br> •	Warehouse/3PL trading partner: Warehouse <br> •	Vendor trading partner: Vendor <br> • Freight forwarder landed cost: vendor account with Voyages' **Shipment type** set to _Shipping company_.
**Company**                       |	The **D365 company** this trading partner relates to 
**Type**	                        | The **type** of trading partner (i.e. Customer, Warehouse, Vendor, Freight forwarder landed cost)
**Trading partner account**       |	The **primary identifier** of the trading partner (i.e. Customer account, Warehouse number or Vendor account)
**Name**                          |	The trading partner account's name
**Company GLN**                   |	The GLN the trading partner knows **us** as. This field denotes the trading ID - GLN (Global Location Number) - of your company to be sent on documents to this trading partner.

> Note: Selecting the trading partner GLN will display the detailed form relating to the trading partner
> It also provides the setup for trading partner level options as well as defining which incoming and outgoing document types are enabled for the trading partner.

### Trading partner details

Users can access the form by navigating to **EDI > Setup > Trading partners**. <br>
Select the **Trading partner GLN** hyperlink or the **Details** button to update trading partner's details. <br>
The following setup applies to all types of Trading partners and will be discussed in the Core module. The module specific setup/mappings will be discussed in each Module's guides.

**Field** 	                      | **Description**
:-------------------------------- |:-------------------------------------
**Company**	                      | The D365 company this trading partner relates to. This field is not editable after creation.
**Type**                          | The type of trading partner (i.e. Customer, Warehouse, Vendor, Freight forwarder landed cost). This field is not editable after creation. 
**Company GLN**                   |	The GLN the trading partner knows ‘us’ as. Note: This field denotes the trading ID - GLN (Global Location Number) - of your company to be sent on documents to this trading partner.
**Trading partner account**       |	The primary identifier of the trading partner (i.e. Customer account, Warehouse number or Vendor account). This field is not editable after creation.
**Name**                          |	The trading partner account's name. Not editable in this form. Links to customer, warehouse or vendor account's name.
**Created by**                    | User id that created the record.
**Created date and time**         | Date and time the record was created.
**Modified by**                   | User id that last modified the record.
**Modified date and time**        | Date and time the record was last modified.
**Trading partner GLN**           |	The GLN we know the trading partner as. Note: This field denotes the trading partner GLN. The module will use this field as a match to the customer, warehouse or vendor. 
**Connection profile**            |	Ability to override the default EDI connection profile on Trading partner level. If blank, default EDI connection will be used. Default EDI connection is determined by: <br> • Outgoing documents: Connection profile setup on [EDI > Setup > EDI parameters](EDI-parameters.md) <br> • Incoming documents: All active connection incoming paths as setup in [Connections](Connection-setup.md).
**Cleanup profile**               |	Ability to override the default Cleanup profile (setup on Shared EDI parameters) on Trading partner level. If blank, default Cleanup profile will be used as setup on [EDI > Setup > EDI shared parameters](EDI-shared-parameters.md)

Module specific setup are discussed in their sections:
- [Customer trading partners](../../CUSTOMER/SETUP/Trading-partner.md)
- [Vendor trading partners](../../VENDOR/SETUP/Trading-partner.md)
- [3PL trading partners](../../3PL/SETUP/Trading-partner.md)
- [Freight forwarder landed cost trading partners](../../FREIGHT-FORWARDER/SETUP/Trading-partner.md)

### Outgoing documents

Users can access the form by navigating to **EDI > Setup > Trading partners**. <br>
Select the **Trading partner GLN** hyperlink or the **Details** button to update trading partner's details. <br>

The Outgoing documents FastTab defines the outgoing EDI document types that have been configured and enabled for the trading partner. It brings the document template, mappings and filename setup together with the settings profile to enable the document for the trading partner.

**Field** 	                      | **Description**
:-------------------------------- |:-------------------------------------
**EDI Document type**             |	[EDI document type](Document-types.md). Users can add outgoing document types as available for the trading partner type. 
**Template**                      |	[Document type template](DocumentTypes/File-templates.md) that has been previously defined.
**Setting profile**               |	[Settings profile](DocumentTypes/Setting-profiles.md) that has been previously defined. Note: View details displays the settings profiles in read only.
**File name setup**               |	Select the [Outbound file name mask](DocumentTypes/Outbound-filenames.md) to use for the document. Note: Options displayed depends if the selected template supports multiple headers. If assigned template only supports single headers, only Outbound files with **Single file per document** set to _Yes_ will be available.
**Connection profile**            |	Ability to override the default [EDI connection profile](Connection-setup.md) on document level. If blank, the trading partner’s Connection profile will be used.
**Cleanup profile**               |	Ability to override the default [Cleanup profile](Cleanup-profile.md) on document level. If blank, the trading partner’s Cleanup profile will be used. If Trading partner's Cleanup profile is blank, the default Cleanup profile on [EDI shared parameters](EDI-shared-parameters.md) will be used.
**Reset status profile**          |	Ability to override the default [Reset status](Reset-status.md) on document level. If blank, [EDI shared parameters](EDI-shared-parameters.md) will be used.
**Acknowledgement**               |	An Inbound Functional Acknowledgement is required from the trading partner for the outgoing document. Note: Also required to setup the Functional acknowledgement inbound document under Incoming documents.
**Enabled**                       |	Enable the document for the Trading partner – Yes/No

### Incoming documents

Users can access the form by navigating to **EDI > Setup > Trading partners**. <br>
Select the **Trading partner GLN** hyperlink or the **Details** button to update trading partner's details. <br>

The Incoming documents FastTab defines the incoming EDI document types that have been configured and enabled for the trading partner. It brings the document template, mappings, validation profile and setting profiles together along with a file mask for importing to enable the document for the trading partner.

**Up** and **Down** buttons set the sequence of processing in batch. This applies where the same incoming document type is setup against the Trading partner with different Search mask.

**Field** 	                      | **Description**
:-------------------------------- |:-------------------------------------
**EDI Document type**             |	[EDI document type](Document-types.md). Users can add incoming document types as available for the trading partner type. 
**Template**                      |	[Document type template](DocumentTypes/File-templates.md) that has been previously defined.
**Setting profile**               |	[Settings profile](DocumentTypes/Setting-profiles.md) that has been previously defined. Note: View details displays the settings profiles in read only.
**Validation profile**            |	[Validation profile](DocumentTypes/Validation-profiles.md) that has been previously defined.
**Search mask**                   |	A file mask is used to match files in the document type’s defined directories. <br> The setup of the directory (i.e. FTP site) configures whether the file mask is matched at the start of the file name or at the end (For further information, see Site Paths in [Connection setup](Connection-setup.md)). See [examples for Search mask](#examples-for-search-mask) below.
**Connection profile**	          | Ability to override the default [EDI connection profile](Connection-setup.md) on document level. If blank, the trading partner’s Connection profile will be used.
**Cleanup profile**               |	Ability to override the default [Cleanup profile](Cleanup-profile.md) on document level. If blank, the trading partner’s Cleanup profile will be used. If Trading partner's Cleanup profile is blank, the default Cleanup profile on [EDI shared parameters](EDI-shared-parameters.md) will be used.
**Reset status profile**          |	Ability to override the default [Reset status](Reset-status.md) on document level. If blank, [EDI shared parameters](EDI-shared-parameters.md) will be used.
**Acknowledgement**               |	Trading partner requires an Outbound Functional Acknowledgement for the incoming document. Note: Also required to setup the Functional acknowledgement outbound document under Outgoing documents.
**Enabled**                       |	Enable the document for the Trading partner – Yes/No

#### Examples for Search mask:
- Example 1: <br>
  - File mask: LCAB10 <br>
  - Search mode:  File name must start with <br>
  - Will match file: **LCAB10**20170623.txt <br>
  - Won’t match file: ACAB1020170623.txt <br>
  
- Example 2: <br>
  - File mask: SalesInvoice.xml <br>
  - Search mode:  File name must end with <br>
  - Will match file: 20170623_**SalesInvoice.xml** <br>
  - Won’t match file: 20170623_SalesInvoice.txt <br>

Additionally, regular expressions can be used for the file mask <br>
- Example 3: <br>
  - File mask: *US-001 <br>
  - The following file names will be matched:
    - **US-001**_1234.json
    - 1234_**US-001**
    - 1234_**US-001**_5678.xml <br>

- Example 4: <br>
  - File mask: ^PO_.*_CustUS-001.xml <br>
  - The following file names will be matched:
    - **PO**347**CustUS-001.xml**
    - **PO**6796**CustUs-001.xml** <br>

  Note: ^ - String Anchor ‘Starts with’ and & - String Anchor ‘Ends with’
