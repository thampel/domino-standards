# Domino Feature usage
Domino offers various new features, for security and standardization reasons only a limited set is allowed to be used within the standardized Domino environment.

## Standard features
This section describes the standard features that are allowed to be used within Domino environment. Additional implementation manuals and guidelines may apply for each element.

| **Task/Feature** | **Description** | **Mandatory** |
| --- | --- | --- |
| Automatic Server Recovery | Automated server restart in case of server crash | X |
| Agent manager | Server task to control scheduled agents | X |
| AdminP | Administration Process | X |
| Calendar Connector | Calendar Connector,
to be used on mail servers and servers hosting a rooms and resource database as well as all HUB servers. |  |
| Catalog Task | Scheduled task that lists all databases in the database catalog catalog.nsf | X |
| Compact | compacts databases in order to remove whitespace | X |
| Statrep | Statistics reporter |  |
| Events | Events | X |
| Fixup | Analyzes and fixes problems within the database structure
to be used when needed. |  |
| Design | Refresh database design | X |
| Directory Cataloger | Initially aggregates information from source Domino Directories into a directory catalog |  |
| HTTP Server | Server task required to access domino databases from a web browser. Not allowed on all server types, please check chapter 7 for details |  |
| Indexer | Builds view index | X |
| Replicator | Perform scheduled replication | X |
| Router | Routing of mails | X |
| Rooms & Resource Manager | Server task controlling room and resource usage, reacting on incoming requests, e.g. request to book a room or resource for a specific time. To be used for servers with room and resource databases only. |  |
| Schedule manager | To be used on mail servers and application servers hosting a rooms and resource databases or mail files. |  |
| Fault Analyzer | Fault Analyzer is a server add-in task that processes all new crashes as they are delivered to the Automatic Data Collection mail-in database. |  |
| Cluster Replicator | Required to keep clusters in sync <br> Mandatory for clustered servers. |  |
| DDM | Domino Domain Monitoring <br> Not mandatory, but highly recommended to be used.
For implementation please refer to EPCOS implementation manuals or IBM Lotus Redbooks. |  |
| Stats | Statistics reporter | X |
| Event Monitor | Events |  |
| Smart Upgrade | Software distribution system which allows to upgrade existing Notes clients a higher release. Clients need to use Notes version 6.x or higher in order to use this feature. |  |
| SMTP Mail Routing | Convert Notes messages to SMTP mails for routing mails to internet. |  |
| SMTP Listener | Listen for incoming SMTP mails.
to be used for dedicated SMTP Servers only |  |
| Activity Trends Collector | Runs the Activity Trends Collector which performs historical and trended analysis on Domino Activity data. |  |
| Chronos | Updates full-text indexes that are marked to be updated hourly, daily, or weekly. | X |
| Change Manager | Domino Change Manager |  |
| Statistics Collector | Collect statistics information | X |
| MTC | Message Tracking | X |

## Restricted features
Lotus Domino features listed in this section require explicit approval from the EPCOS Global Service Owner for Mail & Groupware and the EPCOS Global Security Manager before using.

| **Task/Feature** | **Description** |
| --- | --- |
| CA process | Domino Built In process for automated handling of User ID’s and certificates |
| SNMP
- QuerySet
- Interceptor | SNMP protocol for Domino |
| IMAP Server | Using domino as an IMAP server |
| POP3 Server | Using domino as an POP3 server |
| LDAP Server | Using domino as an LDAP server <br> Within EPCOS the global LDAP services have to be used |
| Billing | Collects all generated billing information. |
| DIIOP | Allows COBRA applications to access a domino server |
| Shared Mail | Stores all mail data in a single database instead of using individual mail files for each user |
| Domain Indexer | Domain wide indexing process |
