---
layout: default
title: "Software"
nav_order: 3
parent: "Home"
description: "HCL Domino - Software Standards"
has_children: true
---

<h1>Software Standards</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Operating System

## OS Specific Settings

## Antivirus on Operating System Level
Running an antivirus software on  operating system level is highly recommended.
The virus pattern files should be updated at least once a day.
If a local pattern update infrastructure (for a central management of the antivirus software) is available the server should be connected to it to make sure to have the current settings and virus pattern files available. 

Please follow the local upgrade policy to make sure that you have the most current version of the antivirus software installed.

The following configuration changes for the antivirus software have to be made:
1. Disable OnAccess Scanner

This has to be disabled because of performance reasons

2. Exclude the following file extensions from scanning

This will prevent operating antivirus scanners to scan file types it can not handle.

- *.NSF
- *.NTF
- *.NCF
- *.NT5
- *.TXN
- *.BOX
- *.NLO

3. Exclude the following directories from scanning

This will prevent operating antivirus scanners to scan directories that are used by Domino.

- *\NOTES*\ 
- *\view-rebuild\
- *\Logfiles\
- *\DAOS\

Files and directories which are excluded in the operating system scanning will be checked by the antivirus software on Domino level

## Antivirus on Domino 
Domino Installation Directories
When installing a Domino server, change the default installation folders to the following:
For AIX / Linux
- Domino Program Files: /opt/HCL/Domino/
- Domino Data Directory: /local/notesdata

For Windows Operating Systems
- Domino Program Files:
- Domino Data Directory:

### Drive Indexing
By default Windows operating systems are configured to run a built in drive indexing service. In order to improve the overall system performance for Domino it’s highly recommended to turn off the built in drive indexing. 
This option can be found in the properties of every drive letter. Make sure it’s turned off.
Alternatively the drive indexing service can be turned off completely within the services control panel.

## Time Settings
To assure a smooth mail routing and replication between all Domino servers it is very important that the servers have been set to the correct time.

### Time Zone
The operating system’s time zone has to be set to the correct value according to the physical location of the server. In addition the setting "Automatically adjust clock to daylight saving changes" must be enabled. Domino Servers must be set to "use OS time zone settings"

### Time Adjustment
The server time itself has to be automatically set by a NTP time server. Within there are several NTP servers which can be used for that purposes.
Run the following commands from a command prompt to enable the automatic time adjustment via NTP:
net stop w32time
net time /setsntp:<ipaddress of NTP server>
net start w32time
Please use an NTP server to keep time settings up to date.
If the Domino server is connected to a Windows Domain Controller the server time may also be set via Windows standard domain functions. In that case it has to be made sure that the domain controller’s time is controlled by one of the NTP servers.

### Regional Settings
The settings for Date and Time within the regional settings of the operating system should be set to the following values:
- Short date format: yyyy-mm-dd (Sample: 2006-12-31)
- Time: HH:mm:ss (Sample: 20:30:00)

All Domino applications must be designed in a way that they work independently of the operating system representation of date and time.

**Attention!**
Please be aware that changing the regional settings might affect existing applications.
Also, please keep in mind that the Domino server uses the "HKEY_USERS\.DEFAULT" settings!
