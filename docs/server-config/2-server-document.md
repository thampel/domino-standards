---
layout: default
title: "Server Document"
nav_order: 2
parent: "Domino Server"
description: "HCL Domino Standards"
has_children: true
---

<h1>Server Document</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

This section describes the standard settings for the different server types that are in use within the Domino environment. All settings are mandatory except otherwise noted.
The following server configuration applies to Domino servers of version 14.5 and above, for older versions of the Domino directory template some elements can not be found in the form and are to be ignored.

# Basics

## Basics

| **Field** | **Description / Value** |
| --- | --- |
| Server Name | Abbreviated Name of Domino server |
| Server Title | Server Title, should include server type (see 4.2) and international Location code of server location, e.g. DE-MUC for Germany-Munich |
| Domain Name | Name of domain where this server belongs to Remark: for naming standards see section |
| Fully qualified Internet host name | Full qualified host name of this server, corresponding to the server name. Don’t use the operating system’s host name. Remark: for naming standards see section |
| Cluster name | Optional, cluster name, only used if server is a member of a cluster Remark: for naming standards see section |
| Load Internet configurations from Server\Internet Sites documents: | Enabled |
| Maximum formula execution time: | 120 seconds |


| **Field** | **Description / Value** |
| --- | --- |
| Server build number | {System value, DO NOT CHANGE} |
| Routing tasks | Mail Routing, SMTP Mail Routing |
| SMTP listener task |  |
| Server's phone number(s) | Blank <br> Remark: for security reasons its not allowed to directly call a domino server using a dialup connection |
| CPU count | {System value, DO NOT CHANGE} |
| Operating system | {System value, DO NOT CHANGE} |
| Is this a Sametime server? | No |

### Directory Information

| **Field** | **Description / Value** |
| --- | --- |
| Directory assistance database name | da-[cc].nsf <br> For symbols please refer to chapter 1.3.1 |
| Name of condensed directory catalog on this server | {Obsolete with Domino 8.5.1} |
| Trust the server based condensed directory catalogue for authentication with internet protocols | {Obsolete with Domino 8.5.1} |
| Directory Type | Primary Domino Directory |
| Allow this directory to be used as a remote primary directory for other servers | Disabled <br> Remark: 
In order to prevent unnecessary network traffic, this option is to be disabled. |

### Automatic Server Recovery

| **Field** | **Description / Value** |
| --- | --- |
| Run This Script After Server Fault/Crash | {blank}
Note: can be used e.g. on Sametime servers to collect diagnostic information. |
| Run NSD To Collect Diagnostic Information | Enabled |
| Automatically Restart Server After Fault/Crash | Enabled |
| Cleanup Script / NSD Maximum Execution Time | 600 seconds |
| Server Shutdown Timeout | 300 seconds |
| Maximum Fault Limits | 3 faults in 60 minutes |
| Mail Fault Notification to | %FaultNotification |

### Server Location Information

| **Field** | **Description / Value** |
| --- | --- |
| Phone Dialing | {blank} |
| Prefix for outside line | {blank} |
| International prefix | {blank} |
| Country code at this location | {blank} |
| Long distance prefix | {blank} |
| Area code at location | {blank} |

| **Field** | **Description / Value** |
| --- | --- |
| Calling card access number | {blank} |
| Calling card number | {blank} |
| Network Dialup idle timeout | {blank} |

| **Field** | **Description / Value** |
| --- | --- |
| Mail server | Abbreviated Domino Server Name of this server, Same value as in field “Server Name” |
| Passthru server | {blank} |
| InterNotes server | {blank} |

# Security
The Security tab of the Server document provides options to configure the server’s security parameters. It is divided into Administrators, Security settings, Server access, Programmability restrictions, Internet access, Passthru use.
According to the naming standard for system groups (see chapter 5.7.4)

## Administrators

| **Field** | **Description / Value** |
| --- | --- |
| Full Access administrators | %FullAccessAdministrators |
| Administrators | %Administrators, [SERVER] |
| Database Administrators | %DbAdministrators |
| Full Remote Console Administrators | %FullRemoteConsoleAdministrators |
| View-only Administrators | %ViewOnlyAdministrators |
| System Administrator | %SystemAdministrators |
| Restricted System Administrator | {blank} |
| Restricted System Commands | {blank} |

## Programmability restrictions

| **Field** | **Description / Value** |
| --- | --- |
| Sign or Run unrestricted methods and operations |  |
| Sign agents to run on behalf of someone else | %SignAgentsOnBehalf |
| Sign agents or XPages to run on behalf of the invoker | {blank} |
| Sign or run restricted LotusScript/Java agents |  |
| Run Simple and Formula agents |  |
| Sign script libraries to run on behalf of someone else | {blank} |

## Security settings

| **Field** | **Description / Value** |
| --- | --- |
| Compare public keys | Do not enforce key checking |
| Log public key mismatches | Log key mismatches for Notes users and Domino servers listed in trusted directories only |
| Allow anonymous Notes connections | No |
| Check passwords on Notes IDs | Enabled |

### Internet access

| **Field** | **Description / Value** |
| --- | --- |
| Internet authentication | Fewer name variations with higher security |

### Server access

| **Field** | **Description / Value** |
| --- | --- |
| Access server |  |
| Not access server | %ServerAccessDeny |
| Create databases & templates | %ChangeMgmt, %TspServers, %Administrators, %DBAdministrators |
| Create new replicas | %ChangeMgmt, %TspServers, %Administrators, %DbAdministrators |
| Create master templates | %ChangeMgmt, %TspServers, %Administrators, %DbAdministrators |
| Allowed to use monitors | * |
| Not allowed to use monitors | {blank} |
| Trusted servers | %TrustedServers_[CC] |

### Passthru Use

| **Field** | **Description / Value** |
| --- | --- |
| Users listed in all trusted directories | Disabled |
| Access this server |  |
| Route through |  |
| Cause calling | {blank} |
| Destinations allowed | {blank} |

## Ports
The port configuration of a server defines network ports and how to use them.
Network ports are enabled/disabled by a two step process using the Setup Ports dialog box and then using Server documents and/or by changing your servers notes.ini

### Notes Network Ports 
Only TCP/IP networks are to be used within this environment.
Clustered servers will have to use 3 network interfaces/ports in a minimum, one for user access, a second one for cluster network and a third one for admin access.
Non clustered servers use 2 network interfaces/ports in a minimum, one for user access and a second one for admin access.
For all network ports, network compression is to be enabled by default
Configuration options are shown below.

| **Port** | **Protocol** | **Notes Network** | **Net Address** | **Enabled** |
| --- | --- | --- | --- | --- |
| TCP1 | TCP | [CC]-USERS[XX] | {fully qualified DNS host name} | Enabled |
| TCP2 | TCP | [CC]-[TYPE]-SERVERS[XX] | {TCP/IP Address of NIC} | Enabled |
| TCP3 | TCP | [CC]-[TYPE]-ADMIN[XX] | {TCP/IP Address of NIC} | Enabled |
| TCPMAIL | TCP | [CC]-[TYPE]-WANMAIL[XX] | {TCP/IP Address of NIC}:51354 | Enabled |
| TCPREPL | TCP | [CC]-[TYPE]-WANREPL[XX] | {TCP/IP Address of NIC}:51353 | Enabled |
Remark:
The ports TCPMAIL and TCPREPL are to be used optionally for all servers and mandatory for servers participating in mail routing or database replication across the wide area network. These ports are using different TCP ports to allow network routing based on QOS classification for each type of traffic.
This table describes the naming standard for domino named networks within the environment.

| **Interface** | **Description** |
| --- | --- |
| [CC]-USERS[XX] | First network interface is to be used for user access and mail routing,
All servers of the same location / same network should use the same User network, [XX] is a serial number for each network <br> Example: DE-USERS01 |
| [CC]-[TYPE]-SERVERS[XX] | Secondary network interface is to be used for clustered servers in the same data center. Only for server to server traffic, e.g. cluster replication. <br> Example:  <br> “US-APPL-SERVERS01” for the first application server in the US
“US-APPL-SERVERS02” for the second application server in the US |
| [CC]-[TYPE]-ADMIN[XX] | Dedicated network interface for admin access, having a different IP Address <br> Example: SE-APPL-ADMIN01
for the first application cluster admin port in Sweden |
| [CC]-[TYPE]-WANMAIL[XX] | Optional port for incoming mail routing traffic <br> Example: IN-MAIL-WANMAIL01
for MAIL01 server in India |
| [CC]-[TYPE]-WANREPL[XX] | Optional port for incoming replication traffic <br> Example: DE-HUB-WANREPL03
for HUB03 server in Germany |

### Mandated port encryption for Server (NRPC)

| **Setting** | **Value** |
| --- | --- |
| Encryption Level | Best negotiated port encryption |
| Mandated level | 256-bit AES GCM Keys with Forward Secrecy (most protection) |
| Current Status | {DO NOT CHANGE} |

### Internet Ports
This section describes the internet port settings for a domino server
SSL settings

| **Setting** | **Value** |
| --- | --- |
| Outgoing TLS Key file name | Keyfiles\[TYPE][XX]-[CC].kyr |
Note: 
Other settings are not displayed here because ‘Use Internet Sites’ is supposed to be enabled.

#### Web

| **Setting** | **Value** |
| --- | --- |
| TCP/IP port number | 80 |
| TCP/IP port status |  |
| Enforce server access settings | Yes |
| SSL port number | 443 |
| SSL port status |  |

#### Directory
This section describes the port settings for directory / LDAP use.
It describes the default values, which have no effect until the LDAP task is loaded. Keep in mind that LDAP is a restricted feature – for more information, please refer to chapterXXXX

| **Setting** | **Value** |
| --- | --- |
| TCP/IP port number | 389 |
| TCP/IP port status |  |
| Enforce server access settings | **Yes** |
| SSL port number | 636 |
| SSL port status |  |

#### Mail
Inbound mail protocols are to be used on mail servers only, if not used the respective ports are to be disabled.

| **Setting** | **IMAP** <br> | **POP** | **SMTP****
Inbound** | **SMTP****
Outbound** |
| --- | --- | --- | --- | --- |
| TCP/IP port number | 143 | 110 | 25 | 25 |
| Port Status | Enabled | Disabled | Enabled | Negotiated SSL |
| Enforce server access settings | Yes | Yes | No | N/A |
| SSL Port number | 993 | 995 | 567 | 465 |
| SSL port status | Enabled | Disabled | Enabled | Disabled |

#### Domino IIOP
This chapter describes the default settings for Domino IIOP Server component.
DIIOP is an optional Domino feature that is not supposed to be used within the environment described here.

| **Setting** | **Value** |
| --- | --- |
| TCP/IP port number | 63148 |
| TCP/IP port status | Disabled |
| Enforce server access settings | Yes |
| SSL Port number | 63149 |
| SSL port status | Disabled |

#### Remote Debug Manager

| **Setting** | **Value** |
| --- | --- |
| TCP/IP port number | 60000 |
| TCP/IP port status | Disabled |
| Enforce server access settings | Yes |
| SSL port number | 60001 |
| SSL port status | Disabled |

#### Server Controller

| **Setting** | **Value** |
| --- | --- |
| TCP/IP address: | {blank} |
| TCP/IP port number: | 2050 |

### Proxies
All Domino servers are located within a network which allows direct outbound Internet access. It should not be necessary to define any proxy settings.

| **Setting** | **Value** |
| --- | --- |
| HTTP proxy: | {blank} |
| FTP proxy | {blank} |
| Gopher proxy | {blank} |
| TLS Security proxy | {blank} |
| Http Tunnel proxy | {blank} |
| Socks proxy |  |
| No proxy for these hosts and domains |  |

## Server Tasks
Server tasks perform complex administration procedures -- for example, compacting databases and updating indexes. 
You can run a server task manually, by loading the task at the server console or by using the Domino Administrator Task - Start tool, Server menu, or the Administrator console. Or you can run the task automatically when the server starts by adding the name of the task to the ServerTasks or ServerTasksAt settings in the NOTES.INI file. 
In addition, you can create a Program document in the Domino Directory to run a task at scheduled intervals.

### Administration Process
The Administration Process is a program that automates many routine administrative tasks. 
In this section the standard configuration parameters for Domino servers are described. However, it might be necessary to adjust some of these settings for performance tuning.
For more details please refer to the product documentation.

#### Basics

| **Field** | **Description / Value** |
| --- | --- |
| Maximum number of threads |  |
| Interval between purging mail file and deleting when using object store: | {empty} <br> Shared mail is not to be used. |
| Normal Request Settings 
Interval | 10 Minutes |

| **Normal Request Settings** | **Description / Value** |
| --- | --- |
| Normal Request Settings 
Interval | **10 Minutes** |
| Execute once a day requests at: | **17:30** |

| **Delayed Request Settings** | **Description / Value** |
| --- | --- |
| Start executing at | **Sat, ****Sun Day(s)** |
| Execute once a day requests at: | **06:00** |

#### Miscellaneous

| **Field** | **Description / Value** |
| --- | --- |
| Mail file moves expire after | 21 days |
| Store Admin Process log entries when status of no change is recorded | No |
| Suspend Admin Process at | {empty} |
| Restart Admin Process at | {empty} |

#### Inbox Maintenance

| **Field** | **Description / Value** |
| --- | --- |
| Start executing Inbox Maintenance agent on: | Sat |
| Restart Admin Process at | 01:00 |
| Maintain inboxes based on policies | Enabled |

### Agent Manager

#### Basics

| **Field** | **Description / Value** |
| --- | --- |
| Refresh Agent Cache | 00:00 |

#### Daytime parameters

| **Field** | **Description / Value** |
| --- | --- |
| Start time: | 06:00 |
| End time: | 20:00 |
| Max concurrent agents: | Number of concurrent agents depends to server type <br> |
| Max LotusScript/Java execution time: |  |
| Note: The following setting only applies to servers running R4.6 and earlier |  |
| Max % busy before delay: | 50 |

#### Nighttime parameters

| **Field** | **Description / Value** |
| --- | --- |
| Start time: | 20:00 |
| End time: | 06:00 |
| Max concurrent agents: | Number of concurrent agents depends to server type <br> |
| Max LotusScript/Java execution time: |  |
| Note: The following setting only applies to servers running R4.6 and earlier |  |
| Max % busy before delay: | 70 |

### Domain catalog
This task builds a domain wide database catalog. Servers should never be configured to collect database information from another server.

| **Field** | **Description / Value** |
| --- | --- |
| Domain Catalog | Disabled |
| Limit domain cataloging to the following servers | {empty} |

### Directory Cataloger
The Directory Catalog task is designed to build a condensed domino directory.
As shown in this configuration, this task is to be disabled. However it can be enabled for special needs.

| **Field** | **Description / Value** |
| --- | --- |
| Directory Catalog filenames: | {empty} |
| Schedule | DISABLED |
| Run Directory Cataloger task at | 00:00 - 23:59 each day |
| Repeat interval of | 120 minutes |
| Days of week | Sun, Mon, Tue, Wed, Thu, Fri, Sat |

### Internet Cluster Manager
This feature is currently not in use.

### Web Retriever
The Web Navigator lets Notes workstations access the Web, without having a direct connection to the Internet. This task is not to be used within this environment.

| **Field** | **Description / Value** |
| --- | --- |
| Web Navigator database | Web.nsf |
| Services | {none} – all have to be deselected |
| Concurrent retrievers | 50 |
| Retriever log level | None |
| Update cache | Once per session |
| SMTP Domain | {empty} |
| Allow access to these Internet sites | * |
| Deny access ot these Internet sites | {empty} |

### Remote Debug Manager
The remote debugger allows debugging of LotusScript agents running on remote servers. For more information about remote debugging, see the Domino Designer documentation, topic Using the Remote Debugger. 
By default, this task is to be disabled – as shown in the configuration below.

| **Field** | **Description / Value** |
| --- | --- |
| Allow remote debugging on this server | Disabled |
| Turnoff Server Debug after | 24 hours of inactivity |
| Agent Wait at StartTime | 0 seconds |

### Active Directory Password Sync
This feature allows to sync passwords from an Active Directory Domain controller. Although technically possible, HCL recommends using federated authentication instead of syncing passwords.

| **Field** | **Description / Value** |
| --- | --- |
| Password sync processing role | None |

## Internet Protocols

### HTTP
This chapter describes generic configuration parameters for application servers running HTTP task.
For servers not running the HTTP task, these settings have no effect.
Parameters highlighted can be adjusted in case of performance tuning needs.

### Basics

| **Field** | **Description / Value** |
| --- | --- |
| Host name(s) | [Common Name] <br> Fully qualified internet host name of server as described in chapterxxx, for servers not following this standard, a DNS resolvable name is to be used. |
| Bind to host name | Disabled |
| DNS lookup | Disabled |
| DNS lookup cache | Enabled |
| DNS lookup cache size | 256 |
| DNS lookup cache found timeout | 120 seconds |
| DNS lookup cache not found timeout | 240 seconds |
| Number active threads |  |

#### Log File Settings

| **Field** | **Description / Value** |
| --- | --- |
| Access log format | Common |
| Time format | LocalTime |
| Log file duration | Daily |
| Maximum log entry length | 10 kilobytes |
| Maximum access log size | 0 megabytes |

#### Enable logging to

| **Field** | **Description / Value** |
| --- | --- |
| Log Files |  |
| Domlog.nsf |  |

#### Log File Names

| **Field** | **Description / Value** |
| --- | --- |
| Directory for log files | {empty} |
| Access log | [Servername]-Access |
| Agent log | [Servername]-Agent |
| Referer log | [Servername]-Referrer |
| Error log (R4 and R5 only) | [Servername]-Error |
| CGI error log | [Servername]-Cgi-error |

#### Exclude from logging

| **Field** | **Description / Value** |
| --- | --- |
| URLs | *.gif
*.jpg
*.png
*.jpeg
*.css
/servlet/traveler/Microsoft-Server-ActiveSync* |
| Methods |  |
| MIME types | image/gif
image/jpeg |
| User agents |  |
| Return codes |  |
| Hosts and domains |  |

#### Timeouts

| **Field** | **Description / Value** |
| --- | --- |
| HTTP persistent connections | Enabled |
| Maximum requests per persistent connection | 5 |
| Persistent connection timeout | 180 seconds |
| Request timeout | 60 seconds |
| Input timeout | 15 seconds |
| Output timeout | 180 seconds |
| CGI timeout | 180 seconds |

#### R5 Timeouts
This section is obsolete – it was used for R5 servers running within the domain.

#### Network Settings

| **Field** | **Description / Value** |
| --- | --- |
| Listen queue size | 2048 |
| Maximum number of concurrent network sessions | 2000 |
| IP address allow/deny priority | Allow |
| IP address allow list | * |
| IP address deny list | {empty} |

#### HTTP Protocol Limits 

| **Field** | **Description / Value** |
| --- | --- |
| Maximum URL length | 4 kbytes |
| Maximum number of URL path segments | 64 |
| Maximum number of request headers | 48 |
| Maximum size of request headers | 16 kbyte |
| Maximum size of request content | 20480 kilobytes <br> specify 0 to allow unlimited content <br> max. 20MByte file size for HTTP uploads. |

#### Trusted Proxies

| **Field** | **Description / Value** |
| --- | --- |
| Enable trusted proxies | {unchecked} <br> Note: enable only if Server is behind an HTTP proxy |
| Trusted proxy IP list |  |

#### HTTP HOST Header Whitelist

| **Field** | **Description / Value** |
| --- | --- |
| Enable HTTP Whitelist | {unchecked} |

### Domino Web Engine
This chapter describes how to configure the Domino web engine.

#### HTTP Sessions
This section does not apply as "Load Internet configurations from Server\Internet Sites documents" has been enabled.

####  Java Servlets

| **Field** | **Description / Value** |
| --- | --- |
| Java servlet support | Domino Servlet Manager |
| Servlet URL path | /servlet |
| Class path | domino\servlet |
| Servlet file extensions |  |
| Session state tracking | Enabled |
| Idle session time-out | 30 minutes |
| Maximum active sessions | 1000 |
| Session persistence | Disabled |

#### Generating References to this server

| **Field** | **Description / Value** |
| --- | --- |
| Protocol | {empty} |
| Host name | {empty} |
| Port number | 80 |

#### Memory Caches
This section lists the proposed default values for running http on a Domino server. However these values can be adjusted for performance tuning needs.

| **Field** | **Description / Value** |
| --- | --- |
| Maximum cached designs | 1024 |
| Maximum cached users | 256 |
| Cached user expiration interval | 120 seconds |

#### Web Agents

| **Field** | **Description / Value** |
| --- | --- |
| Run web agents concurrently? | Enabled |
| Web agent timeout | 120 seconds |

#### Domino XML Services

| **Field** | **Description / Value** |
| --- | --- |
| XML Services | Disabled |
| Restrict mail message ‘from:” field | Enabled |

### DIIOP
Using DIIOP is restricted, please refer to chapter xx for more information. 

| **Field** | **Description / Value** |
| --- | --- |
| External HTML directory | {empty} |
| Idle session timeout | 60 seconds |
| Host name/Address | {empty} |

### LDAP
Using DIIOP is restricted, please refer to chapter xx for more information.
This section is empty because LDAP settings are configured in an Internet Site document.

## Miscellaneous

### Contact Info

| **Field** | **Description / Value** |
| --- | --- |
| Location | [CC] + Location City Name  <br> e.g. DE-Berlin |
| Department | {Empty} |
| Comments | {Empty} |
| Detailed description | {Empty} |

## Transactional Logging
Transaction logging captures all the changes made to a database and writes them to a transaction log. The logged transactions are then written to disk in a batch, either when resources are available or when scheduled.
Before configuring transactional logging, please make sure your server configuration follows the disc specification in chapter xx. For further assistance refer to the Domino Administrator help database.

| **Field** | **Description / Value** |
| --- | --- |
| Transactional logging | Enabled |
| Log Path | For Windows : T:\ <br> For AIX and Linux : /local/translog/ |
| Logging style | Archived for servers where incremental backup is used <br> Circular is transactional logging is only used for performance reasons |
| Automatic fixup of corrupt databases | Enabled |
| Runtime/Restart performance | Standard |
| Quota enforcement | Check space used in file when adding a note |

## DAOS

### DAOS Settings

| **Field** | **Description / Value** |
| --- | --- |
| Store file attachments in DAOS | Enabled |
| Minimum size of object before Domino will store in DAOS | <br> Note: This value provides a good balance between savings and additional backup effort. Feel free to change at your own risk. |
| DAOS base path |  |
| Defer object deletion for | 30 days |
| DAOS object enryption | Private to this server |
| DAOS encryption strength | AES-256 |

### Tier 2 Storage

| **Field** | **Description / Value** |
| --- | --- |
| DAOS Tier | Disabled |
| S3 Credential Name | {Empty} |
| S3 Bucket |  |
| S3 Endpoint |  |
| Assigned S3 Storage ID | (unssigned) |
| Push object to store if not access for | 180 days |
| Pusb objects only between | 02:00 and 05:00 |
| Index T2 attachments | Disabled |

## Notes Traveler
These settings only apply if Traveler has been installed on this server.

### Basics

| **Field** | **Description / Value** |
| --- | --- |
| Maxium Memory Size | 2048 MB |
| IPC Socket Ports | 50125    50126 |
| External Server URL | https:// |

### HCL Notes Traveler Access

| **Field** | **Description / Value** |
| --- | --- |
| Access Server | Users listed in all trusted directories
and |
| Not access server | $ServerAccessDeny |
| Remote user commands | Disabled |
| User managed security | Enabled |

### Log Settings

| **Field** | **Description / Value** |
| --- | --- |
| Logging Level | Informational |
| SyncML Logging | Off |
| Package Log Filter | * |
| Maximum File Size | 50 MB |
| Maximum Number of Activity Log Files | 10 |
| Fields Logged – Privacy | Subject; Location; Address; Phone Number |

### Auto Sync Settings

| **Field** | **Description / Value** |
| --- | --- |
| Montor Polling Interval | 3 seconds |
| Port for TCP Connections | 8642 |
| Heartbeat Algorithm | Indefinite Detection |
| Heartbet Initial Interval | 30 seconds |
| Heartbeat Algorithm Min. Interval | 30 seconds |
| Heartbeat Algorithm Max. Interval | 15 minutes |
| Heartbeat Retry Interval | 15 minutes |
| Device Offline Timeout | 24 hours |
| User Cleanup Timeout | 30 days |
NIFNSF
NIFNSF Storage

| **Field** | **Description / Value** |
| --- | --- |
| Store view indexes in NIFNSF | Enabled |
| NIFNSF base path |  |
| Enable NIFNSF when creating new databsaes | Yes |

## Administration

### Administration

| **Field** | **Description / Value** |
| --- | --- |
| Owner | %Administrators |
| Administrators | %Administrators |

### Public Key Requirements

| **Field** | **Description / Value** |
| --- | --- |
| Minimum Allowable Key Strength | No Minimum |
| Maximum Allowable Key Strength | Compatible with Release 7 and later (2048 bits) |
| Preferred Key Strength | Compatible with Release 7 and later (2048 bits) |
| Maximum Allowable Age for Key | 36500 days |
| Earliest Allowable Key Creation Date | 01.08.77 |
| Don't automatically generate a new key before | 01.01.2106 |
| Maximum number of days the old key should remain valid after the new key has been created | 365 days |

### Additional Administration Information

| **Field** | **Description / Value** |
| --- | --- |
| Certified public key | {The certified public key of this server} |
