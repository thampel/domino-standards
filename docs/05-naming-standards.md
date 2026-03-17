---
layout: default
title: "Naming Standards"
nav_order: 5
parent: "Home"
description: "HCL Domino Standards - Naming Standards"
has_children: true
---

<h1>Naming Standards</h1>

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Domain Names

## Cluster Names
When Domino servers are clustered a cluster name is to be defined. A cluster name must be unique across the organization and across all servers that a user is accessing.
Syntax:
[TYPE]-[CC]-CLUSTER[XX]
Examples:
- APPL-CH-CLUSTER01
- MAIL-DE-CLUSTER02

### Server Common Name Standard
To Be Done

### Directory for system databases
The following directories are used by Domino for its own system databases and/or can be used to store own system databases as long as these databases are not used by any end users.
List of specific system databases can be found in appendix **XXXXXX**

| **Path** | **Description** |
| --- | --- |
| HELP\
W32\
GTRHOME\
MTSTORE\
RMEVAL\ | Domino Core System Directories |
| SYSTEM\ | This system directory to be used for customer specific system databases |

### Directory for mail databases
All mail files have to be stored in the directory 
	MAIL\

## File Names
File names shall be unique within the enterprise environment, that’s why all applications created will need to follow this standard for file names
All these application file names must be registered within the Database Catalog to avoid naming conflicts.

Syntax: 
 “DB\” + “DB” + [DirNr] + “\” + “DB” + [XXXXXX] + “.NSF”

**Example:**
DB\DB0000\DB000002.NSF
DB\DB0000\DB000041.NSF
DB\DB0001\DB000102.NSF

## User Names
A user name is the name that Notes recognizes when you login to Notes and access servers, databases, and documents. It is in hierarchical format, which means common name and certificate authority's (CA) name makes up a user name. Common name is usually first, middle, and last name. The CA is the entity that created the certificates in the User ID. For example, if the User name is Joe User/User/Org, Joe User is your common name and /User/Org is the CA's name. 
A user name contains these elements

| **Element** | **Example** |
| --- | --- |
| First Name | Given name, e.g. “Joe” |
| Middle Initial | e.g. “B” |
| Last Name | Surname, e.g. “Smith” |
| Common Name | Combination of First name + middle initial + last name, 
e.g. “Joe B Smith” |
| Certificate (OU) | Certificate Authority (CA) used to create this user |
| Organization (O) | Organization that the user belongs to, for details see chapter **XXXX** |
Recommendation for user names is
For real users, only given name, middle initial and Surname should be used to uniquely define a person. Do not use department or other qualifier in the user’s name.
Don't use a third layer (OU2) within Notes certificates and don’t use a “unique orgunit” to uniquely define a person.
e.g. Harald Mueller/Finance/User/Org
Upper and lower cases need to be used with care.
It’s not acceptable to use only upper or only lower cases.
Expiration time should be between 6 months and 2 years.

### Naming Conventions
User names can contain the following characters 
uppercase and lowercase alpha characters (A - Z)
numbers (0 - 9) are to be used for middle initials only, 
for details please refer to chapter 5.4.4
dash (-) has to be used to join multi part names,
For any other local / country characters, please refer to chapter 5.4.5
Even if technically possible, it is not allowed to use the following characters for user names within this environment.
Spaces “ “ 
Periods “.”
Apostrophes “‘”
Brackets “(“ or “)” 

### First Name / Given Name
Within the Domino environment it’s mandatory to provide a first name for all User IDs issued following these standards 
Maximum length of 16 characters
Uppercase and lowercase alpha characters (A - Z)
Numbers (0-9) are NOT to be used as part of the first name
dash (-) has to be used to join multi part names,
e.g. if a user has two first names “Anne Charlotte” the resulting Notes first name is “Anne-Charlotte”
For special multi part names like “Henk van der Boer”
the first name is “Henk” and the last name is “Van-der-Boer” 
Upper and lower cases need to be used with care.
It’s not acceptable to use only upper, or only lower cases.
For any other local / country characters, please refer to chapter **XXXXXX**

### Last Name / Surname
Standards for the surname is
Maximum length of 40 characters.
Uppercase and lowercase alpha characters (A - Z)
Numbers (0-9) are NOT to be used as part of the last name / surname
dash (-) can be used to join multi part names,
e.g. “Jan Mollefors Lokken” will be named “Jan Mollefors-Lokken”
Uppercase and lowercases characters can be mixed within the name
e.g. “McConnell” or “deMouse”
Upper and lower cases need to be used with care.
It’s not acceptable to use only upper or only lower cases.
Do not use blanks ( ) or apostrophes (‘) should be removed.
So for “Joel O’Donald” the last name would be “ODonald”

### Middle initials
If the combination out of surname and given name is not unique within a country, a middle initial has to be used to differentiate between users.
Maximum length of 5 characters
Allowed characters as described in chapter XXXX
Not allowed to use dash (-)
Not allowed to use dot (.)
Usage:
Where the combination of Surname and Given name is unique then no initials need be specified. A new user having the same name as an existing user must get a middle initial while existing users will keep their user name without any change. 

### National Characters 
Different languages have different additional characters. The following table shows most of these characters and their common replacements.  These replacements differ from language to language, so there are several alternatives for some characters.  The grouping of the characters into the languages is not linguistically correct, however it should give some guidelines.

| **Language** | **Character** | **Replacements** |
| --- | --- | --- |
| French | á/à/â <br> Ç - ç <br> é/è/ê <br> ó/ò/ô | a <br> C - c <br> e <br> o |
| German | Ä - ä <br> Ö - ö <br> Ü - ü <br> ß | Ae/A - ae/a <br> Oe/O - oe/o <br> Ue/U - ue/u <br> ss |
| Scandinavian Languages | Å - å <br> Ö/Ø - ö/ø <br> Ä/Æ - ä/æ | Aa/A - aa/a <br> Oe/o - oe/o <br> Ae/a - ae/a |
| Spanish/Portuguese | Ñ - ñ | Nj/N - nj/n |
| various other Languages <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br> Apostrophe | Ë - ë <br> Á/À/Â <br> Ã - ã <br> É/È/Ê <br> Ï - ï/Ì - ì/Í - í/Î - î <br> Ò/Ó/Ô <br> Õ - õ <br> Ù - ù/Ú - ú/Û - û <br> Y- ÿ/Ý - ý <br> O'Toole | E - e <br> A <br> A - a <br> E <br> I - i <br> O <br> O - o <br> U - u <br> Y - y <br> OToole |

## Internet Mail Addresses

### Internet Mail Addresses for People
Internet mail addresses (email addresses) are computed based on the users first name, middle initial, last name and ISO country code.
**Syntax:**
firstname.m.lastname@company.COM
Allowed characters
lowercase alpha characters (A - Z)
numbers (0 - 9)
dash (-) can be used
Do not use spaces.
Usage rules
Addresses have to be unique within a country
Addresses are computed by an agent within the primary name and address book of the domain.
Users can not define an own internet address
The internet mail address will change when the user name changes.

### Internet Mail Addresses for Databases

## Agent Signer Names

### Neutral application signer IDs

### Unrestricted Agents

## Public Groups
Public groups are Domino groups stored in the name and address book or a cascaded secondary address book for shared usage.

### Restrictions and Limitations
For public groups only the following characters are allowed to be used for List Name and List Members.
letters A through Z
numbers 0 through 9
ampersand ( & )
dash ( - )
underscore ( _ )
hash ( # )
dollar sign ( $ )
percent sign ( % )
**Limitations**
Although technically possible, it is not allowed to use ALIAS names for groups within the Domain. An alias name is a list name separated by semicolon ( ; ) or comma ( , )  Alternative names or a second names for the same group in the public name and address book are unmanageable and may cause problems.
Do not use a backslash ( \ ) or any other characters not included in the list of allowed characters above, because they can cause unexpected results.  
Maximum length for group names is 64 characters
**Recommendations**
For easier administration, use a name without spaces. Do not use a name that is in use as the name of an organizational unit in the hierarchical name scheme.
While the use of the period ( . ) currently is not prevented by Lotus, it may be advisable to avoid its use, in consideration of possible future conflicts with Internet addressing.  At this time though there are no known issues relative to using the period in Group names.

### Access Only Groups

|  | **Description** |
| --- | --- |
| Purpose | Administrate user’s access to databases. |
| Group Type | Access list only |
| Created by | Administrators, or the Database Management Team |
| Storage | The primary Domino Directory |
| Updated by | By Users |
| Prefix | “$” = dollar sign |

#### Administration of Access Only Groups in Global Domain
Each database has a number of related Access Only Groups. Each database has one or several defined Database Managers. 
The Database Manager administrates the Access Only Groups belonging to the specific database. The Access Only Groups are automatically created when deploying a database.

#### Group Naming Standard Global Domain
Syntax: 
$DB_[XXXXXX]_[AccessLevel]_[Role]


| **Element** | **Description** |
| --- | --- |
| [AccessLevel] | This part will denote the various access levels user groups will have on the database. You should make a separate group for each access level your database requires. Thus you can have "Editors", "Readers", "Authors", "Depositors" and “NoAccess” <br> Note:  <br> Manager access will be provided to administrators only <br> Designer access is not set by default, because design updates are to be done outside of the production environment <br> Developers will get Designer access rights as highest level.
Users will have Editor access as highest level. |
| [Role] | Optional. 
If you need different roles within one access level, you should make distinct groups, e.g. _Accounting or _Sales. These suffixes are used to the right of the access level. |
**Example: **
$DB_000034_Authors_Projleader
$DB_000034_Authors_2
$DB_000034_Authors_XYZ
The suffix is optional and can be anything (A-Z, 0-9). The length of the group name is to be limited to a maximum number of characters.

### Multi purpose Groups
Multi purpose groups are groups which can be used for access control and for mailing purposes. Multi purpose groups clearly need to belong to an existing notes application database.
The naming for access control groups (see chapter 5.7.2 ) will apply.

|  | **Description** |
| --- | --- |
| Purpose | In special cases it might be required to create access control groups that can also be used for mailing purposes.  <br> Example:
In order to send mails to all people having the role “approver” in a database, a multi purpose group using the naming standard described in chapter 5.7.2 will be created, All users and also all functions can now send a mail to people belonging to that group. |
| Group Type | Multi Purpose |
| Storage | The primary Domino Directory |
| Prefix | “$” = dollar sign |
| Comment | Multi purpose groups can be created by administrators only.
Administration will be done as for access control groups as explained in chapter 5.7.2 |

### System Groups

|  | **Description** |
| --- | --- |
| **Purpose** | System groups are used in the server document to provide administrate access for Notes administrators, servers and system agents. |
| **Group Type** | Access Only |
| **Storage** | The primary Domino Directory (Names.nsf) |
| **Prefix** | “%” = percent |
A list of system groups can be found in chapter **Fehler! Verweisquelle konnte nicht gefunden werden.**

#### Administration of System Groups
System Groups are created and updated by the Domino Administrators.

#### System Groups Naming standard Global Domain
The Global Lotus Domino Domain uses a different syntax than country domains.
Syntax: 
* “%” + Group Name**
*
Examples:
%Administrators
%ServerAccess

This new standard will be used when creating new system groups. Former system groups LocalDomainServers, LocalDomainAdministrators and OtherDomainServers etc. will have to be supported in the new domain by adding the appropriate group above as members of the $ groups.

### Mail Only Groups
Administrators are allowed to manually create special groups that can only be used for mail addressing. Within the global EPCOS Lotus Notes Domain, mail only groups are to be created by users using a different naming standard which is described in chapter **Fehler! Verweisquelle konnte nicht gefunden werden.**

|  | **Description** |
| --- | --- |
| **Purpose** | Share mailing lists among users. |
| **Group Type** | Mail only |
| **Storage** | In primary Domino Directory “names.nsf” |
| **Prefix** | “#” = hash |
Syntax: 
 [Prefix] [CC] - Group Name

Examples

#SE-AllSalesManagers

#US-ApplicationDevelopers

Remark:
Make sure only to use the characters described in chapter 5.7.1

#### Administration of User Generated Mail Only Groups

#### Naming standard

### Deny Access Groups

## Rooms and Resources
A room or resource name is using similar components than a Notes user name, it consists out of 3 components, for each element only the following characters can be used:
Uppercase and lowercase alpha characters (A - Z)
Numbers 0 through 9
Space ( )
dash (-) can be used to join multi part names,
Upper and lower cases need to be used with care.
It’s not acceptable to use only upper-, or only lower cases.
**Remark**
Each room & resource name has to be absolutely unique.
Otherwise the functionality of room & resource booking cannot be guaranteed.
Although technically possible, it’s not recommended to use international characters as part of any room or resource component.
**Syntax**
[CN] / [OU1] / [O]

| **Component** | **Description** |
| --- | --- |
| [CN] | basic resource name |
| [OU1] | OrgUnit1, is only used for resources to define the resource category.
For details, please refer to chapter 5.8.2 |
| [O] | Site, details are described in chapter 5.8.3 |

### Basic Resource Name
Descriptive and (on a specific site) unique name of the room or resource.
Recommendations
Choose a basic resource name that will identify the room for everyone, even visitors who don’t know the building
Use room numbers instead of room names
e.g. “Room 412” instead of “Meeting Room Blue”
Avoid to specify the floor unless it is really required to find the room
e.g. “Room 412” is in most buildings located on the 4th floor anyway.

### OrgUnit1 Component
This component is only used for resources, and not used for rooms at all. It contains the resource category, which can be anything that you like, as long as the following rules are met
Only using allowed characters as specified in chapter 5.8
**Example**
“CompanyCars”

### Site Component
The site name is created by using the ISO country code, followed by the two letter city code. Additionally to the allowed characters, the following characters can be used:
Underscore ( _ ), which is only to be used to separate elements of the site name 
**Syntax**
[CC]_CityCode
**Remark**
Minimum length of a site name is 3 characters
Maximum length of a site name 30 characters 
**Example**
DE_MK
DE_EH

### Summary
All these 3 components together are building a full room / resource name
Examples for rooms
Room412/DE_MK
A204/DE_MK
Examples for resources
Olympus/Digitalcamera/ DE_MK
Canon Stationary/PC Projector/ DE_MK
