# ERP-Cloud-BIP-Report-OIC
Oracle Integration Cloud (OIC): ERP to SFTP Automated Pipeline
An end-to-end integration solution designed to automate the extraction of financial data from Oracle ERP Cloud, transform the payload, and archive it securely on an SFTP server with real-time stakeholder notifications.

## Project Overview
This project demonstrates a robust orchestration in OIC that bridges the gap between Oracle ERP Cloud and external storage systems. It replaces manual report exports with a secure, parameter-driven automated flow.

### Key Features:
Dynamic Extraction: Utilizes a LedgerName parameter to filter BIP Reports at runtime.

Multi-Protocol Connectivity: Seamlessly integrates REST triggers, SOAP (ERP Report Service), and SFTP adapters.

Data Transformation: Handles Base64 decoding of SOAP responses and transforms them into structured CSV format.

Resilient Architecture: Implemented a Global Fault Handler to catch execution errors and notify administrators.

Collision Prevention: Uses XPath expressions for Dynamic File Naming with unique timestamps.

### Technical Stack
Platform: Oracle Integration Cloud (OIC) Gen 2/3

Adapters: REST (Trigger), SOAP (Oracle ERP Cloud), FTP (Target)

Reporting: Oracle BI Publisher (SQL-based Data Model)

Data Formats: XML, JSON, CSV, Base64

Logic: XPath, XSLT Mapping, Fault Handling, Parameterized Scopes

### Integration Flow
Trigger: REST API receives the Report Path and LedgerName.

Invoke: OIC calls the BIP SOAP Service to run the financial report.

Process: The Base64 encoded document is decoded and staged.

Delivery: The file is written to the SFTP Server using a timestamped naming convention (Report_YYYYMMDD_HHMM.csv).

Notification: An HTML Email is dispatched confirming Success or Failure.

### Testing & Error Handling
To ensure enterprise-grade reliability, the integration includes:

Happy Path: Verified successful delivery and CSV integrity on the SFTP server.

Fault Path: Intentionally incorrect report paths trigger the fault handler, ensuring no silent failures occur and the admin is alerted immediately.

###  Demo
https://youtu.be/xoH5t5S1tLU
