# Program documents
A Program document is used to automatically run a server task at a specific time

## Standard program documents
Its highly recommended to create one program document per task and per server.
Using wildcard (*) in the field “server to run on” may cause issues within a problem analysis.

| **Program** | **Command Line** | **Server to run on** | **Schedule** |
| --- | --- | --- | --- |
| Catalog |  | ALL | 01:00 each day
Repeat interval of: 0 minutes 
Days of week: Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Updall |  | ALL | 02:00 each day
Repeat interval of: 0 minutes 
Days of week: Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Statlog |  | ALL | 05:00 each day
Repeat interval of: 0 minutes 
Days of week: Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Compact | -b log.nsf | ALL | 04:30 each day
Repeat interval of: 0 minutes 
Days of week: Fri |
| convert | -l mailprimary.ind | MAIL | 18:30 each day
Repeat interval of: 0 minutes 
Days of week: Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Compact | -A mailprimary.ind | MAIL | 19:00 each day
Repeat interval of: 0 minutes 
Days of week: Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Compact | -B –S 20 | ALL | 23:00 each day
Repeat interval of: 0 minutes 
Days of week: **Sat** |
| Compact | -b | ALL | 00:00 each day
Repeat interval of: 0 minutes 
Days of week: Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Collect |  | ALL | At server startup only <br> Remark: Make sure the task is not loaded in the Notes.ini via “ServerTasks=” |
| daosmgr | resync | ALL servers where DAOS is enabled. | 23:30 each day
Repeat interval of: 0 minutes 
Days of week: Mon, Wed, Fri |
| RnRMgr |  | APPL , MAIL
only if using Room and Resource DBs | At server startup only <br> Remark: Make sure the task is not loaded in the Notes.ini via “ServerTasks=” |
| (n)server | -c “Tell sched validate” | MAIL, APPL | 02:00 each day |
| (n)server | -c “tell mtc Purge 7” | ALL | 00:00 each day
Repeat interval of: 0 minutes 
Days of week: Sun, Mon, Tue, Wed, Thu, Fri, Sat |
