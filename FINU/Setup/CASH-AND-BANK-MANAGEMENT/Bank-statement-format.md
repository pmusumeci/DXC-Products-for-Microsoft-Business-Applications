---
# required metadata

title: Finance Utilities 
description: Cash and bank management setup - Bank statement format 
author: jdutoit2
manager: Kym Parker
ms.date: 2023-06-09
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  BankStatementFormat
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
# Advanced bank reconciliation functionality
The fields as described in the following subsections are available to control the additional functionality for advanced bank reconciliation.

## Setup
### Bank Statement format

To open the **Bank statement format** page, go to **Cash and bank management > Setup > Advanced bank reconciliation setup > Bank statement format**.

#### Fields

When the **Financial utilities parameter**'s **Enable custom bank statement formats** is enabled, the following Finance utilities fields become active in the **Bank statement format** page.

| **Field**           | **Description** |
|-|-|
| **Custom format**   | Checkbox option which enables the **Custom format** buttons and following fields.
| **ABSR file type**  | Choose the file format of the bank statement – options include:  <br> •	Flat File <br> •	NAI File <br> •	BAI2 <br> •	Custom <br> •	BRS |
| **Field delimiter** | The type of field delimiter the file uses. E.g. a comma “,”  |
| **Record code field position** | This field is active only if the **ABSR file type** is set to BAI2, NAI or BRS file. This field captures the position of the **Line code** in each line of the file. E.g. if Field Number = 1, the first field of each line in the file determines the Line code (i.e. 01, 02, 03, 16, 49, 98, 99).
| **Record code field length** | Applicable to BRS files types as BRS files aren't delimited |


#### Custom Format

When field **Custom format** is set to _Yes_, the button **Custom format** is enabled on the Action Pane.

#### Buttons

| **Button** | **Description** |
|-|-|
| **Custom Format > Lines** | The **Lines** page stores the column definition to use whilst importing the custom bank statement. |
| **Custom Format > Line codes** | The **Line codes** page stores the **Custom line codes**. The button is only enabled when **ABSR file type** is set to _Custom_ or BRS|
| **Custom Format > Line codes format** | The **Type codes** stores the relation between statement code and transaction direction (debit/credit) for BAI2 or NAI file <br> Note: Type codes button is active only if the **ABSR file type** is set to _BAI2 file_, _NAI file_ or _Custom_. | 

##### **Custom Format - Line Codes**
The **Custom Format - Line codes** page is used to determine the line identifier for this bank statement. It is used in the **Custom Format - Lines** definition. It contains the following fields:

| **Field** | **Description** |
|-|-|
| **Line Code** | The field number corresponds to the **Custom line code** specified on the bank statement. |
| **Description** | Specify the format line code description. |
| **Is transaction line** | Specify if the line code is a transaction line. |

##### **Custom Format – Lines**

The **Custom Format - Lines** page defines the column definitions to use whilst importing the bank statement. It identifies which fields to use, and their position on the Bank Statement file, for the system to use when loading the detail into the system. It contains the following fields:

> Note: Not all columns in the statement need to be configured. 

| **Field** | **Description** |
|-|-|
| **Field number**| The field number corresponds to the **column number** on the bank statement.|
| **Line code** or **Custom line code**| The **Line code** option appears when the **ABSR file type** is either _BAI2 File_ or _NAI File_. <br> Line type of the file where the Bank Statement fields map to Dynamics 365 Bank Transactions: <br> **02**	– Group Header  <br> **03**	– Account Identifier <br> **16** – Transaction detail <br> **88** – Continuation Record <br>  The **Custom line code** option appears when the **ABSR file type** is either _BRS_ or _Custom_ and utilizes the **Line code** as setup on **Custom format - Line codes**
| **Field** | The corresponding bank account transaction field in Dynamics 365 that this bank statement field maps to - options include: <br> •	Date <br> • Bank statement transaction code <br> • Description <br> • Amount <br> • Reference no. <br> • Entry reference  <br> • Bank account number <br> • Currency <br> • Trading party <br> • Document number <br> • Related bank account <br> • Ending balance |
| **Start position** | If no delimiter is selected on the header, the start position of the field will need to be entered. This field can also be used for files with delimiter where only a set number of characters need to be mapped, for example only map account number starting from 7 for a bank statement field containing bsb (6 characters) + account number (9 characters) |
| **Length** | If no delimiter is selected on the header, the length of the field will need to be entered. This field can also be used for files with delimiter where only a set number of characters need to be mapped, for example only map account number containing 9 characters for a bank statement field containing bsb (6 characters) + account number (9 characters)|
| **Strip leading zeroes** | Specifies whether any leading zeroes in this field should be removed. |
| **Date format** | This specifies the date format in the bank statement.  Note: This mandatory option appears when the **Field** is set to _Date_. |
| **Use Julian date format** | Where applicable, enter the bank statement format's date field in Julian format, for example BRS using YYYYDDD |
| **Decimal adjustment** | This specifies the Decimal adjustment required for the bank statement's **Amount**. For example bank statement amount is 20055, but last two charactes are decimal, thus amount to be mapped to D365 Bank statement is 200.55 <br> For this example enter 2 in **Decimal adjustment** field.| 
| **Position credit/debit** |	This specifies the position of the credit/debit indicator for BRS file’s Amount field. Only enabled where **ABSR file type** is _BRS_.|


##### **Custom Format - Line codes format**
The **Line codes format** page controls how transaction **amounts** are posted. For example all the amounts on the bank statement are positive values, but transactions with a **Bank statement transaction code** in the range set to _Credit_ will be converted to a negative amount when mapped to D365 bank statement. 

| Field | Description |
|-|-|
| **From type code** | Transaction type code range from the Bank Statement Transaction Types |
| **To type code** | 	Transaction type code range from the Bank Statement Transaction Types|
| **Debit/Credit** | 	Area to specify if transaction statement line amount is: <br> •	**Debit** in the system (i.e. positive) <br> • **Credit** in the system (i.e. convert to negative) |
| **Description** |	Description of the particular rule |

> Note: The **Line codes format** page is available only when **ABSR file type** is set to either _BAI2 File_, _NAI File_, or _Custom_. <br> _BRS_ uses the **Position credit/debit** field on **Statement format lines** to determine if the **Amount** is positive (debit) or negative (credit).
