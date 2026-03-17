# Basic Standards
This section describes the core standards for an HCL Domino environment.

## Domoin Certificates
This section describes standards for Domino Certificates and how they are to be used.

### Root Certificates
Root certificates are the top level certificate, the it should use a unique name that describes the organization. 
Using this organization certifier, organization units will be created for each company/organization per country that is using Domino. 
To differentiate between employees and external accounts two root certificates should be used.
Furthermore temporary certificates can be issued for merge & divestiture projects.

| **Certificate** | **Description** | **Example** |
| --- | --- | --- |
| O=Org | Used for internal employees only (see text below table) | /Org |
| O=[xxx]-TEMP | Used for merge & divestiture projects only. Valid only for a short period of time. | /ABC-TEMP |
Every employee with a valid employment contract is considered an employee and must **not** have “Contractor” in his/her user name.
This includes:
Regular employees working on a permanent contract
Temporary employees.
Trainees 
Short-term assignees
Interns & Apprentices

## Server Types
This section describes the different server types used within the environment. 
Definition of server types is a prerequisite for further classification of standards later in this document.

### Standard Server Types

| **Server Type** | **Short ** | **Description** |
| --- | --- | --- |
| Mail | MAIL | Mail servers are purely hosting Mail users.
Except for system databases no applications are supposed to hosted on those servers. |
| Application | APPL | Application servers are hosting Domino applications of various kind as well as system databases, but no Mail files. |
| Ontime | ONTIME | Special application server running Ontime Group Calendar task |
| ADMIN | ADMIN | Dedicated administration server used by administrators for backend functions and domain operations, not hosting any users. IDVault replica. |
| Files | FILE | Domino Files |
| HUB | HUB | Infrastructure server used for mail routing and database replication on country level |
| External | EXT | Providing external connectivity to other companies or business partners.
Servers hosting application databases to be accessed or replicated. Connections may also be used for Notes mail routing |
| Directory | DIR | Directory Server, primary purpose is to run the LDAP service for other services in the environment |
| SMTP | SMTP | SMTP mail relay hosts based on Domino sending SMTP mail to the internet
Remark: SMTP servers need to be listed in the MX record of your domain to allow reverse lookups |
| Test | TEST | Test servers |
| Development | DEV | Development Servers |

## User Account Types

## Database Types
