---
layout: default
title: "Database Properties"
nav_order: 11
parent: "Home"
description: "HCL Domino Standards - Database Properties"
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

## Fulltext index
A full text index can be created for application databases as needed.
However, for best usability, the FullText index should be enabled for mail files.

When creating a Full Text Index the following settings should be used:

| **Field** | **Description / Value** |
| --- | --- |
| Index attached files | Disabled by default, <br> When enabled, only used with option “Using conversion filters” |
| Index encrypted fields | Disabled |
| Index sentence and paragraph breaks | Optional, disabled by default |
| Enabled case-sensitive searches | Optional, disabled by default |
| Update frequency (server only) |  |

## Design Properties

| **Field** | **Description / Value** | **Comments**
| --- | --- | --- |
| Refresh design on admin server only | Enabled | if  inherits from any master template |

## Advanced Database Properties

| **Field** | **Description / Value** |
| --- | --- |
| Don’t overwrite free space |  |
| Compress Database Design |  |
| Compress Document Data | Disabled |
