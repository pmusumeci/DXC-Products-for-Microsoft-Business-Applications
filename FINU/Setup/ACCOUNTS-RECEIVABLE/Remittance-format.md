---
# required metadata

title: DXC Finance Utilities - AR Utilities
description: Customer remittance format setup
author: jdutoit2
manager: Kym Parker
ms.date: 2023-07-10
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  DXCARRemittanceFormat, SAB_FinUtilParameters
audience: Application User
# ms.devlang: 
ms.reviewer: jdutoit2

# ms.tgt_pltfrm: 
# ms.custom: : ["21901", "intro-internal"]
ms.search.region: FinanceUtilFeature
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: helenho
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
---

# Remittance format
The fields as described in the following subsections are available to control the file format for periodic import tasks available in additional licensed feature **Finance utilities - AR utilities**.

## Number sequence

**Cash and bank management > Setup > Advanced bank reconciliation setup > Financial utilities parameters**

The following number sequences are required for setting up AR Utilities Remittance format.

**Field**     | **Description**
:--           |:--
**Staging Id**  | The number sequence that defines the Remittance format's Staging Id
**Template ID**  | The number sequence that defines the Remittance format's Template Id

## Data management

Ensure entity **Customer payment journal header** contains field **DXCARIMPORTVIAFINU**. <br>
Create a new import Data management project using composite entity **Customer payment journal**.

## Remittance format

> Note: The page is only available where additional licensed feature **Finance utilities - AR utilities** is enabled.

To open the **Remittance format** page, go to **Accounts receivable > Payment setup > Remittance format**. <br>
On the Action Pane, select **New** and enter the following details.

### Setup

| **Field**     | **Description** |
:--             |:--
**Custom format**               | When set to _Yes_, a custom format can be set via button **Mappings**.
**Import format configuration** | When **Custom format** is set to _No_, an electronic reporting configuration can be selected.
**Processing group**            | Select the Import Data project previously created in **Progressing group**. This data project will be used when importing the file and processing to customer payment journal.
When **Custom format** is set to _Yes_: | 
**Flat or structured**          | Select if the import file format is flat or structured. <br> **Flat** – A single line per record. Each line of text in the file has all the header information on it as well as the line information. <br> **Structured** – Multiple lines per record. Each line in the file is either a header type or a line type.
**Delimited or fixed**          | Select if the import file format is delimited or fixed. <br> **Delimited** – Columns using a defined separator. <br> **Fixed** – Fixed width.
**Column delimiter**            | Select the Row delimiter used within the file, options: <br> **{;}** – Semicolon <br> **{:}** – Colon <br> **{,}** – Comma <br> **{t}** – Tab <br> **{\|}** Vertical bar
**Record identifier position**  | Where the file is **Structured**, specify the Record identifier position.
**Date format**                 | Select the applicable date format.


### Mapping

Where **Custom format** is set to _Yes_, select **Mapping** to map the file format fields.

The mapping is made up of two sections: <br> 
- File sections (structured only) and
- Field mappings (structured and flat)

| **Remittance format field**  | **Data management target** |
:--                     |:--
**Amount**              | Customer payment journal line entity > Credit
**Reference number**    | Used to find D365 customer account and populate: Customer payment journal line entity > Ledger account <br> Account type is set to Customer.
**Description**         | Customer payment journal line entity > Description
**Invoice**             | Customer payment journal line entity > Invoice <br> If Reference number is not used to find Customer, the invoice can also be used to populate: <br> Customer payment journal line entity > Ledger account
**Payment reference**   | Customer payment journal line entity > Payment reference
**Date**                | Customer payment journal line entity > Date - If Methods of payment's **Posting date** is set to use _Remittance transaction date_

#### File sections

##### Flat

Select **Add** to add mappings for a text file
> Note: The Section type information will be defaulted and only a single Line entry is possible for flat text templates.

##### Structured

File sections are the different types of lines that can be found in a **structured** type file (as defined in the Template's setup called _Flat or structured_). <br>
Field mappings belong to each file section.

A Structured file can have many different file sections, all with an associated section type.
- Select **New** to create a new record
- Specify the **Name** of the file section. Exampled include header, lines, summary.
- Select the **Section type**. The options are:
    - **Header** – Header information often related to the Customer information.
    - **Line** – Related to line information.  
    - **Line Detail** – A sub line data line whose data will be mapped to the same record as the Line’s section type data.
    - **Footer** – Summary/Total information.
> Note: Only one element is possible for Footer and Line sections within a file Section. Multiple elements are possible for Header and Line Details. <br>
> Note:  Each section type that is included in the file must be specified even if no mappings are required. 
- Enter the section type **Description**
- Enter the **Record Identifier** - The identifier value used to identify the line type from the files data. The position of this identifier is specified on the template's setup called _Row identifier position_.

#### Field mappings

Field mappings define how the data is positioned in the file on the section line. Fields can also be statically set to values and certain functions are available to transform the fields data if required.

**Field** 	                      | **Description**                                 
:-------------------------------- |:-------------------------------------   
**Value type**                    |	Whether the field value is a **static** value or a mapped **field** value	
**Static value**	                | If the field type is a static type, then enter the static value	
**Staging field**	                | The mapped staging field	                                                
**Staging table**	                | The table the mapped field represents                               
**Field position**	              | The position in the file the mapping represents                     
** **Field length**               |	Number of characters for field	                                    
** **Alignment**	                | Select Left or Right alignment for the field	                    
** **Padding character**	        | Enter a padding character for the field	                                      

> Note: ** Available for **Fixed** type text templates.


There are two ways to add a field mapping:

##### Manual selection

1. To create a new mapping, select **Add** from the mapping FastTab.
2. Select if the **Value type** will be:
    - Field - mapped to or from staging field, or 
    - Static - Static value used
4. If the Value type is Static, complete the **Static value** <br> _Note: Static value can be either plain text or a method between brackets for outbound files. Example:_ <br> 
(currentDate()) <br> 
(currentLanguageId()) <br> 
(currentSessionDate()) <br> 
(currentSessionDateTime()) <br> 
5.  Specify the **Staging field**. Switch bewteen the header and lines table to find the required field.
7.  Enter the **Field position** within the file.

> Note: To delete a line, select the record then select **Remove**. 

##### Fields picker

Alternatively, a bulk field picker can be used to add multiple mappings at once. 
- Select **Fields picker**
- A new form is displayed allowing Header and Line selection of multiple available records

**Field** 	                      | **Description**                      
:-------------------------------- |:-------------------------------------
**Selected**                      |	Mark whether to add the field. <br> Also indicates if the field is already selected for the template.
**Field label**                   |	The label of the field
**Field name**                    | The name of the field

- Select **Update** to update the mapping

Buttons **Select all** and **Clear all** are also available to easily select or clear all fields for the mapping.

> Note: To delete a line, select the record then select **Remove**. Lines can also be moved using the **Move up** or **Move down** buttons.
> If a field needs to be added more than once, use manual **Add** button on the Mappings FastTab.

### Where used

The **Remittance format** is assigned on **Methods of payment**. <br>
The **Methods of payment** is assigned in the Periodic task called [Payment journal import](https://dxcanzproduct.github.io/DXC-Products-for-Microsoft-Business-Applications/FINU/Setup/ACCOUNTS-RECEIVABLE/Customer-remittance.html#periodic-task).

### Data entities

**Order** | **Entity**                            
:--       |:--
1         | Finance utilities template file
2         | Remittance format
3         | Finance utilities template file section
4         | Finance utilities template file line section
