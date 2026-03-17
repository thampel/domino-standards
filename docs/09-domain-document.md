---
layout: default
title: "Domain Document"
nav_order: 9
parent: "Home"
description: "HCL Domino Standards - Domain Document"
has_children: true
---

<h1>Domain Document</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Global Domain Document
You have to create a global domain document for every Internet domain which is used in the Internet address of one of your users / mail-in databases in that domain.

### Basics

#### Basics

| **Field** | **Description / Value** |
| --- | --- |
| Domain type: | Global Domain |
| Global domain name: | {smtp-domain} <br> e.g. : ”de.company.com” |
| Use as default Global Domain (for use with all Internet protocols except HTTP): | Disabled |

### Restrictions

#### Domino Domain Aliases / SMTP Members

| **Field** | **Description / Value** |
| --- | --- |
| Domino domains and aliases: |  |
| Alias separator character: | = |

### Conversions

#### SMTP Address Conversion

| **Field** | **Description / Value** |
| --- | --- |
| Local primary Internet domain: | {smtp-domain} <br> e.g. ”de.company.com” |
| Alternate Internet domain aliases: | {blank} |
| Internet address lookup: | Enabled |
| Local part formed from: | Common name |
| Domino domain(s) included: | None |
| Domino domain(s) position: | Left of ‘@’ |
| Domino domain separator: | % - percent sign |
| Outbound mail restriction: | Unrestricted |
| Address format: | Name and Address |

#### X.400 Address Conversion

| **Field** | **Description / Value** |
| --- | --- |
| Outbound mail restriction: | Restrict to global domain |
| Country name: | {blank} |
| ADMD name: | {blank} |
| PRMD name: | {blank} |
| Domino domain attribute: | None |
