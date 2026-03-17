---
layout: default
title: "Program documents"
nav_order: 10
parent: "Home"
description: "HCL Domino Standards - Program documents"
has_children: true
---

<h1>Program Document(s)</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

A Program document is used to automatically run a server task at a specific time

## Standard program documents
Its highly recommended to create one program document per task and per server.
Using wildcard (*) in the field “server to run on” may cause issues within a problem analysis.

| **Program** | **Command Line** | **Server to run on** | **Schedule** |  **Days of Week** |
| --- | --- | --- | --- | --- |
| Catalog |  | ALL | 01:00 each day, Repeat interval of: 0 minutes,  |  Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Updall |  | ALL | 02:00 each day, Repeat interval of: 0 minutes | Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Statlog |  | ALL | 05:00 each day, Repeat interval of: 0 minutes | Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Compact | -b log.nsf | ALL | 04:30 each day, Repeat interval of: 0 minutes | Fri |
| convert | -l mailprimary.ind | MAIL | 18:30 each day, Repeat interval of: 0 minutes | Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Compact | -A mailprimary.ind | MAIL | 19:00 each day, Repeat interval of: 0 minutes | Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Compact | -B –S 20 | ALL | 23:00 each day, Repeat interval of: 0 minutes | Sat |
| Compact | -b | ALL | 00:00 each day, Repeat interval of: 0 minutes | Sun, Mon, Tue, Wed, Thu, Fri, Sat |
| Collect |  | ALL | At server startup only <br> Remark: Make sure the task is not loaded in the Notes.ini via “ServerTasks=” |
| daosmgr | resync | ALL servers where DAOS is enabled. | 23:30 each day, Repeat interval of: 0 minutes | Mon, Wed, Fri |
| RnRMgr |  | APPL , MAIL only if hosting Room and Resource DBs | At server startup only <br> Remark: Make sure the task is not loaded in the Notes.ini via “ServerTasks=” |
| (n)server | -c “Tell sched validate” | MAIL, APPL | 02:00 each day |
| (n)server | -c “tell mtc Purge 7” | ALL | 00:00 each day, Repeat interval of: 0 minutes | Sun, Mon, Tue, Wed, Thu, Fri, Sat |
