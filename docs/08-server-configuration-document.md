# Server Configuration Document
For each server a standalone configuration document should to be created in the Domino Directory. 
Wildcard configuration documents or configuration for a whole group of servers are not recommended to prevent changes on more than one server by accident.

## Basics

### Basics

| **Field** | **Description / Value** |
| --- | --- |
| Use these settings as the default settings for all servers: | Disabled <br> Remark: <br> If LDAP is used on a server within the domain you have to create one configuration document with this setting set to “Enabled” (a “Global Configuration Document”). Only in a Global Configuration Document the LDAP tab is visible. <br> As LDAP is not a supported Domino feature no further explanation is made for the LDAP settings. |
| Group or Server name: | Abbreviated Name of the Domino server for which this configuration document applies <br> {Servername} |
| Type-ahead: | Enabled |
| International MIME Settings for this document: | Enabled |
| IMAP server returns exact size of message: | Enabled |
| POP3 server returns exact size of message: | Disabled |
| License Tracking: | Disabled |
| Minimum Client Level: | {blank} |
| Maximum Client Level: | {blank} |
| Minimum HCL Client Application Access Level (Does not pertin to Server Administrators) | {blank} |
| Configuration for Domino Server with Shindig | Disabled |
| Comments: | {blank} |

### Tivoli Enterprise Console Settings

| **Field** | **Description / Value** |
| --- | --- |
| Enable Logging to Tivoli Enterprise Console | Disabled |
| IP Address: | {blank} |
| Port Number: | 5529 |

## Security

### Multi Factor Authentication

| **Field** | **Description / Value** |
| --- | --- |
| Time-based one-timepasswords (TOTP) for web authentication | Disable |
| Allow emergeny scratch codes | Yes |
| Email scratch codes to a user | No |
| Maximum number of secrets | 3 |
| Algorithm | HMAC-SHA256 |
| Issuer | {DOMAINNAME} |

### Internet Password Verification

| **Field** | **Description / Value** |
| --- | --- |
|  | Check vault first, then directory |

### Internet Lockout

| **Field** | **Description / Value** |
| --- | --- |
| Enforce Internet Password Lockout | Yes |
| Also enforce lockout based on IP address | Enabled |
| Count user name failures also as IP address failures | Enabled |
| Log Settings | Lockouts, Failures |
| Default Maximum Tries Allowed | 5 |
| Default Lockout Expiration | 365 days |
| Default Maximum Tries Interval | 7 days |

### Server ID Protection on Windows Servers (12.0 and later)

| **Field** | **Description / Value** |
| --- | --- |
| Server ID protection |  |

## Client Upgrade

### AUT

| **Field** | **Description / Value** |
| --- | --- |
| Automatic Update is enabled | Disabled |
| AUT service DNS name | {blank} |
| Maximum number of download sessions | 30 |

### Trust Certificates 
List of trusted certificates if AUT feature is enabled.

### Smart Upgrade

| **Field** | **Description / Value** |
| --- | --- |
| Smart Upgrade Database link: | {blank} |
| Limit Concurrent Smart Upgrade: | Disabled |

### Provisioning

| **Field** | **Description / Value** |
| --- | --- |
| Provisioning settings are enabled | Disabled |

## Router/SMTP

### Basics

#### Router/SMTP Basics

| **Field** | **Description / Value** |
| --- | --- |
| Number of mailboxes: | 2 |
| SMTP used when sending messages outside of the local internet domain: | Enabled |
| SMTP allowed within the local internet domain: | Disabled |
| Servers within the local Notes domain are reachable via SMTP over TCPIP: | Always |
| Address lookup: | Fullname then local part |
| Exhaustive lookup: | Disabled |
| Relay host for messages leaving the local internet domain: | {smtp-relay-server}
The full qualified internet host name of the outgoing SMTP server. |
| Use authentication when sending messages to the relay host | Disabled |
| Local Internet domain smart host: | {blank} |
| Smart host is used for all local internet domain recipients: | Disabled |
| Host name lookup: | Dynamic then local |

### Restrictions and Controls

#### Restrictions

##### Router Restrictions

| **Field** | **Description / Value** |
| --- | --- |
| Allow mail only from domains: | {blank} |
| Deny mail from domains: | {blank} |
| Allow mail only from the following organizations and organizational units: (*/Acme, */Sales/Corp) | {blank} |
| Deny mail only from the following organizations and organizational units: (*/Acme, */Sales/Corp) | {blank} |
| Maximum message size: | 20.480 kbyte |
| Send all messages as low priority if the message size is between: | Disabled |

#### SMTP Inbound Controls

##### Inbound Relay Controls

| **Field** | **Description / Value** |
| --- | --- |
| Allow messages to be sent only to the following external internet domains: | {blank} |
| Deny messages to be sent to the following external internet domains: (* means all) | * |
| Allow messages only from the following internet hosts to be sent to external internet domains: | {blank} |
| Deny messages from the following internet hosts to be sent to external internet domains* means all) | {blank} |

##### Inbound Relay Enforcement

| **Field** | **Description / Value** |
| --- | --- |
| Perform Anti-Relay enforcement for these connecting hosts: | All connecting hosts <br> . |
| Exclude these connecting hosts from anti-relay checks: | {blank} |
| Exceptions for authenticated users: | Allow all authenticated users to relay |

##### DNS Blacklist Filters

| **Field** | **Description / Value** |
| --- | --- |
| DNS Blacklist filters: | Disabled |
| DNS Blacklist sites: | {blank} |
| Desired action when a connecting host is found in a DNS Blacklist: | Log only |
| Custom SMTP error response for rejected messages: | Your host %s was found in the DNS blacklist at %s |

##### DNS Whitelist Filters

| **Field** | **Description / Value** |
| --- | --- |
| DNS Whitelist Filters: | Disabled |
| DNS Whitelist Sites: | {blank} |
| Desired action when a connecting host is found in a DNS whitelist: | Silently skip blacklist filters |

##### Private Blacklist Filter

| **Field** | **Description / Value** |
| --- | --- |
| Private Blacklist Filter: | Disabled |
| Blacklist the following hosts: | {Empty} |
| Desired action when a connecting host is found in the private blacklist: | Log only |
| Custom SMTP error response for rejected messages: | {Empty} |

##### Private Whitelist Filter

| **Field** | **Description / Value** |
| --- | --- |
| Private Whitelist Filter: | Disabled |
| Whitelist the following hosts: | {Empty} |
| Desired action when a connecting host is found in the private whitelist: | Silently skip blacklist filters |

##### Inbound Connection Controls

| **Field** | **Value** |
| --- | --- |
| Verify connecting hostname in DNS: | Enabled |
| Allow connections only from the following SMTP internet hostnames/IP addresses: | * |
| Deny connections from the following SMTP internet hostnames/IP addresses: | {Empty} |
| Error limit before connection is terminated | {Empty} |

##### Inbound Sender Controls

| **Field** | **Description / Value** |
| --- | --- |
| Verify sender’s domain in DNS: | Enabled |
| Allow messages only from the following external internet addresses/domains: | {Empty} |
| Deny messages from the following internet addresses/domains: | {Empty} |

##### Inbound Intended Recipients Controls

| **Field** | **Description / Value** |
| --- | --- |
| Verify that local domain recipients exist in the Domino Directory: | Enabled |
| Reject ambiguous names | Disabled |
| Deny mail to groups | Disabled |
| Allow messages intended only for the following internet addresses: | {Empty} |
| Deny messages intended for the following internet addresses: | {Empty} |

##### Inbound Sender Domain Authentication Controls

| **Field** | **Description / Value** |
| --- | --- |
| DKIM signature verification |  |
| Sender Policy Framework check (SPF) |  |
| Desired action when the sending IP hard fails the SPF check ofr the sender domain | Log and tag the message |
| Do not perform an SPF check for the following internet hostnames/IP addresses | {Empty} |

##### External Email Notifications

| **Field** | **Description / Value** |
| --- | --- |
| External email notifications | Enabled |
| Notification type | Add to beginning of Subject only |
| Text to add to Subject | [External] |
| Notification text formt | HTML |
| Text or HTML to add to message | CAUTION: This email is from outside the organization. Unless you trust the sender, don't click links or open attachments as it may be a phishing email, which can steal your information and compromise your computer. |
| Exceptions for trusted hostnames/Ipaddresses | {Empty} |

#### SMTP Outbound Controls

##### Outbound Sender Controls

| **Field** | **Description / Value** |
| --- | --- |
| Allow messages only from the following Internet addresses to be sent to the Internet: | {Empty} |
| Deny messages from the following Internet addresses to be sent to the Internet: | {Empty} |
| Allow messages only from the following Notes addresses to be sent to the Internet: | {Empty} |
| Deny messages from the following Notes addresses to be sent to the Internet: | {Empty} |

##### Outbound Recipient Controls

| **Field** | **Description / Value** |
| --- | --- |
| Allow messages only to recipients in the following Internet domains or hostnames: | {Empty} |
| Deny messages to recipients in the following Internet domains or hostnames: | {Empty} |

#### Delivery Controls

##### Delivery Controls

| **Field** | **Description / Value** |
| --- | --- |
| Maximum delivery threads: | {blank} |
| Encrypt all delivered mail: | Disabled |
| Pre-delivery agents: | Enabled |
| Pre-delivery agent timeout: | 30 seconds |
| User rules mail forwarding: | Enabled |
| Deny rules mail forwarding to external internet domains | Enabled |
| Reverse-Path for forwarded mail | Preserve existing value |

##### Quota Controls

| **Field** | **Description / Value** |
| --- | --- |
| Over warning threshold notifications: | None |
| Over quota notification: | None |
| Over quota enforcement: | Deliver anyway (don’t obey quotas) |

##### Deliver to Junk Folder Controls

| **Field** | **Description / Value** |
| --- | --- |
| Delvier untrusted messages to the Junk folder | Enabled |
| Exceptions for specific recipients | {blank} |

#### Transfer Controls

##### Transfer Controls

| **Field** | **Description / Value** |
| --- | --- |
| Maximum transfer threads: | {blank} |
| Maximum concurrent transfer threads: | {blank} |
| Maximum hop count: | 25 |
| Low priority mail routing time range: | 18:00 – 21:00 |
| Low priority delay notification: | Disabled |
| Initial transfer retry interval: | 2 minutes |
| Expired message purge interval: | 15 minutes |
| Transfer and delivery delay notifications | Disabled |
| Delay notification intervals |  |
| High priority mail | 4 hours |
| Normal priority mail | 24 hours |
| Low priority mail | 48 hours |
| Allow users to schedule a delivery time for messages | Enabled |

#### Rules
No server rules are configured as a standard. They may be configured for special purposes but you should be aware of possible performance degradations.

### Message Disclaimers

#### Message Disclaimers

| **Field** | **Description / Value** |
| --- | --- |
| Message disclaimers: | Disabled |
| Add disclaimer to S/MIME signed or encrypted messages: | Disabled |
| Logging level: | Normal |

### Message Tracking
Message tracking is currently **mandatory for mail servers**. All other servers can enable or disable this feature as wanted.

#### Basics

| **Field** | **Description / Value** |
| --- | --- |
| Message tracking: | Enabled |
| Don’t track messages for: | {Empty} |

#### Message Tracking Collector Settings

| **Field** | **Description / Value** |
| --- | --- |
| Message tracking collection interval: | 15 |

#### Message Tracking Logging Settings

| **Field** | **Description / Value** |
| --- | --- |
| Log message subjects | Yes |
| Don’t log subjects for: | {Empty} |

#### Access Settings

| **Field** | **Description / Value** |
| --- | --- |
| Allowed to track messages: | LocalDomainAdmins, LocalDomainServers |
| Allowed to track subjects: | LocalDomainAdmins, LocalDomainServers |

### Message Recall

| **Field** | **Description / Value** |
| --- | --- |
| Message Recall | Enabled |
| Allow recall of messages with unread status | Unread only |
| Do not allow recall of messages older than | 7 days |

### Advanced

#### Journaling

##### Basics

| **Field** | **Description / Value** |
| --- | --- |
| Journaling: | Disabled |
| Field encryption exclusion list: | Form;From;Principal;PostedDate |
| Method: | Copy to local database |
| Database Name: | mailjrn.nsf |
| Encrypt on behalf of user: | {Empty} |
| Journal Recipients | Disable |

##### Database Management

| **Field** | **Description / Value** |
| --- | --- |
| Method: | Periodic Rollover |
| Periodicity: | 7 days |

#### Commands and Extensions

##### Inbound SMTP Commands and Extensions

| **Field** | **Description / Value** |
| --- | --- |
| SIZE extension: | Enabled |
| Pipelining extension: | Enabled |
| DSN extension: | Enabled |
| 8 bit MIME extension: | Enabled |
| HELP command: | Enabled |
| VRFY command: | Disabled |
| EXPN command: | Disabled |
| ETRN command: | Disabled |
| TLS negotiated over TCP/IP port: | Enabled |

##### Outbound SMTP Commands and Extensions

| **Field** | **Description / Value** |
| --- | --- |
| SIZE extension: | Enabled |
| Pipelining extension: | Enabled |
| DSN extension: | Enabled |
| 8 bit MIME extension: | Enabled |

#### Controls

##### Miscellaneous Controls

| **Field** | **Description / Value** |
| --- | --- |
| Logging level: | Informational
Remark: equals to Notes.ini variable Log_Mailrouting=30 |
| Out-of-Office Type | Service |

##### 

##### Additional Controls (Delivery and Transfer)

| **Field** | **Description / Value** |
| --- | --- |
| Restrict name lookups to primary directory only: | Disabled |
| Cluster failover: | Enabled for all transfers in this domain |

##### 

##### Advanced Transfer Controls

| **Field** | **Description / Value** |
| --- | --- |
| Ignore message priority: | Disabled |
| Dynamic cost reset interval: | 60 minutes |

##### 

##### Undeliverable Mail

| **Field** | **Description / Value** |
| --- | --- |
| Hold undeliverable mail: | Disabled |
| Automatically process dead mail | Enabled |
| Dead mail delivery attempts allowed | 12 |
| Time between dead mail delivery attempts | 120 |
| Internal Internet domains | {Empty} |

##### Failure Messages

| **Field** | **Description / Value** |
| --- | --- |
| Failure messages for the conditions below are specified by: | Text file |
| Transfer failure: | {blank} |
| Delivery failure: | {blank} |
| Message expiration: | {blank} |
| Domain failure: | {blank} |
| Server failure: | {blank} |
| Username failure: | {blank} |
| Size failure: | {blank} |
| Restriction failure: | {blank} |
| Delay notification: | {blank} |
| Quota warning notification: | {blank} |
| Quota error notification: | {blank} |
| Transfer and delay notifications | {blank} |

## MIME

### Basics

#### Basic

| **Field** | **Description / Value** |
| --- | --- |
| Primary character set group: | English |
| Secondary character set groups: |  |

### Conversion Options

#### General

##### General Conversion Options

| **Field** | **Description / Value** |
| --- | --- |
| Return receipts: | Disabled |

#### Inbound

##### Inbound Conversion Options

| **Field** | **Description / Value** |
| --- | --- |
| Use character set auto-detection if message has no character set information: | Yes |

#### Outbound

##### Outbound Conversion Options

| **Field** | **Description / Value** |
| --- | --- |
| Attachment encoding method: | Base64 |
| Message content: | from Notes to Plain Text and HTML |
| Convert tabs to spaces: | No |
| Outbound line length: | 75 |
| Lookup Internet address for all Notes addresses when Internet address is not defined in document: | Disabled |

### Settings by Character Set Groups

| **Field** | **Description / Value** |
| --- | --- |
| For outbound messages options below use all possible choices | Disabled |

#### Inbound Message Options
**Note:** The following settings have to be set for every different character set group!

| **Field** | **Description / Value** |
| --- | --- |
| HTML Proportional: | Default Sans Serif |
| HTML Mono-spaced: | Default Monospace |
| HTML Size: | 12 |
| Plain Text: | Default Monospace |
| Plain Text Size: | 10 |

#### Outbound Message options
**Note:** The following settings have to be set for every different character set group!

| **Character Set Group** | **Header****
Character Set** | **Header****
Encoding** | **Body****
Characeter Set** | **Body****
Encoding** |
| --- | --- | --- | --- | --- |
| Arabic | Windows-1256 | Base 64 | Windows-1256 | Base 64 |
| Baltic Rim | Windows-1257 | Quoted Printable | Windows-1257 | Quoted Printable |
| Central Europe | ISO-8859-2 | Quoted Printable | ISO-8859-2 | Quoted Printable |
| Cyrillic | KOI8-R | Base64 | KOI8-R | Base64 |
| English | US-ASCII | None | US-ASCII | Nones |
| Greek | Windows-1253 | Base64 | Windows-1253 | Base64 |
| Hebrew | Windows-1255 | Base64 | Windows-1255 | Base64 |
| Japanese | ISO-2022-JP | Base64 | ISO-2022-JP | None |
| Korean | EUC-KR | Base64 | ISO-2022-KR | None |
| Simplified Chinese | GB2312 | Base64 | GB2312 | Base64 |
| Thai | TIS-620 | Base64 | TIS-620 | Base64 |
| Traditional Chinese | Big5 | Base64 | Big5 | Base64 |
| Turkish | Windows-1254 | Quoted Printable | Windows-1254 | Quoted Printable |
| Unicode | UTF-8 | Base64 | UTF-8 | Base64 |
| Vietnamese | Windows-1258 | Quoted Printable | Windows-1258 | Quoted Printable |
| Western | ISO-8859-1 | Quoted Printable | ISO-8859-1 | Quoted Printable |

### Advanced

#### Advanced Inbound Message Options

##### Advanced Inbound Message Options

| **Field** | **Description / Value** |
| --- | --- |
| Resent headers take precedence over original headers: | Disabled |
| Remove group names from headers: | No |
| If each recipient’s address does not appear in any  address header, then add their address to the BCC list: | Yes |
| For non-MIME messages or MIME messages with an unknown character set, 8-bit character set is assumed to be: | Default |
| Character set name aliases | {Empty} maps to {Empty} |

#### Advanced Outbound Message Options

##### Advanced Outbound Message Options

| **Field** | **Description / Value** |
| --- | --- |
| Macintosh attachment conversion: | AppleDouble (base64 only) |
| RFC822 phrase handling: | Use CN as phrase |
| Internet Mail server sends Notes private items in messages: | Disabled |
| Always send the following Notes items in headers: | {Blank} |
| Notes items to be removed from headers: | $Mailer
$MIMETrack
Received |
| When converting a multilingual message to MIME: | Send it in Unicode (UTF8) |
| Character set name aliases: | {Empty} maps to {Empty} |

## NOTES.INI Settings
The following settings should be used::

| **Parameter** | **Value** |
| --- | --- |
| Amgr_DisableMailLookup | 1 |
| ADMIN_CLIENT_SKIP_DOMINO | 1 |
| ARCHIVE_DISABLE_STRICT_SOURCE_SERVER | 1 |
| CLUSTER_ADMIN_ON | 1 |
| COMPRESS_LZ1_CREATE | 1 |
| CLUSTER_REPLICATORS | For clustered servers only: <br> 3 |
| Clrepl_Obeys_Quotas | 0 |
| converter_log_level | 10 |
| Console_Log_Enabled | 1 |
| Console_Log_Max_kbytes | 204800 |
| Console_Log_Mirror | 1 |
| CATALOG_DISK_USAGE | 1 |
| **CREATE_R12_DATABASES** | **1** |
| CREATE_R85_LOG | 1 |
| COMPACT_FILTER | names.nsf; admin4.nsf; ddm.nsf, log.nsf; clubusy.nsf;busytime.nsf |
| Compact_Upgrade_Medium_Encryption_To_Strong | 1 |
| DisableLDAPonAdmin | 1 |
| Debug_ThreadID | 1 |
| DominoNoWebAdmin | 1 |
| Disable_BCC_group_expansion | 1 |
| **DAOS_ENCRYPT_NLO** | **0** |
| **DAOS_ENCRYPTION** | **0** |
| DEBUG_SCR_DISABLED | 1 |
| DEBUG_CAPTURE_TIMEOUT | 1 |
| DEBUG_SHOW_TIMEOUT | 1 |
| DEFAULT_INDEX_LIFETIME_DAYS | 14 |
| Delete_Duplicate_Puid_Notes | 1 |
| DEBUG_AMGR_ENABLE_RETRY_ON_COMPACT | 1 |
| DominoXURLProcess | 1 |
| Disable_Random_RW_File_ATTR | For Servers running on Windows 2008 R2:
1 (see Technote 1449825) |
| EnableImapFolderSynch | 1 (see Technote 1447408) |
| Enforce_EffectiveUserRights_EvaluateCommand | 1 |
| FT_Index_Ignore_Attachment_Types | *.zip,*.tif,*.BMP,*.ZIP,*.ID,*.SHB,*.GIF,*.JPG,*.NSF,*.NTF,*.EML,*.EXE,*.DLL,*.CAB,*.PNG,*.WAV,*.JPE,*.JPEG,*.AVI,*.MPG,*.MPEG,*.MP3 |
| FTG_INDEX_LIMIT | 25165824 |
| FT_FLY_INDEX_OFF | Mail servers : “1”
Other : “0” |
| FTG_USE_SYS_MEMORY | 1 |
| GROUP_CACHE_SIZE | 15360 |
| HTTPJVMMaxHeapSize | 2048M |
| HTTPJVMMaxHeapSizeSet | 1 |
| HTTPallowdecodedurlpercent | 1 |
| HTTPQueueMethod | Only for server type “APPL”: 
2 <br> |
| JavaMaxHeapSize | 256MB |
| LOG_DisableTXNLogging | 1 |
| LOG_AGENTMANAGER | 1 |
| LOG_REPLICATION | 0 |
| LOG_SESSIONS | 0 |
| LOG_PURGE_HOUR | 2 |
| LOG | LOG.NSF,1,0,7,40000,2 |
| MailBoxDisableTXNLogging | 1 |
| MailCompactDisabled | 1 |
| MinNewMailPoll | 15 |
| NSF_BACKUP_MEMORY_LIMIT | 104857600 |
| NSF_BACKUP_MEMORY_CONSTRAINED | 1 |
| NSF_BUFFER_POOL_SIZE_MB | 1024 |
| Name_Change_Expiration_Days | 60 |
| NLCACHE_SIZE | 134217728 |
| NOTES_TEMPDIR |  |
| NTS_BUFFER_POOL_SIZE_MB | 1024 |
| NO_TERM_EXIT_NO_PANIC | 1 |
| NO_FORCE_Activity_Logging | 1 |
| NTS_MAIL_SERVERS_ALGORITHM | LOCALPREFER |
| PhoneLog | 0 |
| PLATFORM_STATISTICS_DISABLED | 1 |
| POP3Greeting | POP3 Server Ready at %s |
| RNRMGR_CLUSTER_FAIL_INTERVAL | 10 |
| PORT_ENC_ADV | 127 |
| RouterINIUseMessageDisabled | 1 |
| RouterAllowConcurrentXferToAll | 1 |
| REPL_OBEYS_QUOTAS | 0 |
| RouterMaxEffectiveSize | 200000 |
| RNR_NO_CALCSTATS | 1 |
| RNR_MAKE_TOPIC_PRIVATE | 1 (see Technote 1391768) |
| RNRMGR_CLUSTER_FAIL_INTERVAL | 10 |
| RFC822StripUnquotedDelimiters | 1 |
| Retain_Mirror_Logs | 1 |
| RouterExpansionAllowNonUniqueGroupMatch | 1 |
| RouterINIUseMessageDisabledd | 1 |
| RouterTranslateSpecial | 0 |
| ServerTasksAt1 | <empty> <br> Remark: Program documents should be used instead |
| ServerTasksAt2 | <empty> <br> Remark: Program documents should be used instead |
| ServerTasksAt3 | <empty> <br> Remark: Program documents should be used instead |
| ServerTasksAt4 | <empty> <br> Remark: Program documents should be used instead |
| ServerTasksAt5 | <empty> <br> Remark: Program documents should be used instead |
| Server_Upgrade_No_Directory_Redesign | 1 |
| SERVER_TRANSINFO_RANGE | 75 |
| SCHEDULE_NO_CALCSTATS | 1 |
| Schedule_DisableTXNLogging | 1 |
| SSL_DISABLE_RENEGOTIATE | 1 (see Technote 1430331) |
| STATS_COLLECT_ALLOCATED_SHARED_PRIVATE | 1 |
| SERVER_CLUSTER_DEFAULT_PORT <br> | For clustered servers only: <br> Set to the designated LAN port which should be used for clustering, e.g: <br> “TCP2” |
| SMTP_LEFT_DOT_NEVER_DOMAIN | For server type “SMTP” only: <br> 1 |
| SMTPTranslateAddresses | For server type “SMTP” only: <br> 2 <br> Other : 0 |
| SMTPGreeting | SMTP Server Ready at %S |
| SMTPDisplayHosName | {fully qualified host name} |
| SSL_RESUMABLE_SESIONS | 0 |
| SMTPNOVERSIONINRCVDHDR | 1 |
| SetupLeaveServerTasks | 1 |
| SERVER_NAME_LOOKUP_NO_UPDATE | 1 |
| TNEFEnableConversion | 1 |
| UPDATE_NO_FULLTEXT | 0 |
| UPDATERS | 3 <br> use the number of CPU’s available in the server minus 1 (e.g.4 CPU cores – 1 = 3) <br> |
| VIEW_REBUILD_DIR |  |
| wskdmn_debug_dontlinger | 1 |

## HCL Verse
Webmail configuration options

### Welcome Page

| **Field** | **Description / Value** |
| --- | --- |
| Default Welcome Page | {default} |
| Allow users to edit the Welcome Page | Enabled |

### Alarms

| **Field** | **Description / Value** |
| --- | --- |
| Alarms | Enabled |
| Minimum alarm polling time | 5 minutes |

### Offline
Not supported

### Mail

| **Field** | **Description / Value** |
| --- | --- |
| Minimum mail polling time | 5 minutes |
| When sending mail, set format to | Let use decide |
| Name resolution and validation | Enabled |
| Maxium attachments size (kb) | **50000** |
| Mail threads | Enabled |

### International

| **Field** | **Description / Value** |
| --- | --- |
| Alternate name support | Enabled |
| Preferred alternate name languages | English |
| Allow users to choose alternate name display | Disabled |

### Start Up View

| **Field** | **Description / Value** |
| --- | --- |
| Allow users to select default active view | Enabled |
| When opening iNotes, open to | Welcome |

### Mail Encryption

| **Field** | **Description / Value** |
| --- | --- |
| Encrypted mail support | Enabled |
| Allow users to delete their NotesID | Disabled |
| Allow users to export their NotesID | Disabled |
| Require TLS to access secure mail features | Client |
| Use JavaScript for SSL-rediretion requests | Enabled |
| Allow untrusted Internet certificates to be used for S/MIME encryption | Disabled |

### Sametime

| **Field** | **Description / Value** |
| --- | --- |
| Sametime features | Disabled |
| Online awareness | Disabled |
| Directory type used by HCL Sametime server | Domino Directory |
| Allow secrets and tokens authentication | Enabled |
| Location of the Sametime proxy server to use when using http | {Empty} |
| Location of the Sametime proxy server to use when using https | {Empty} |
| Use a login dialog for authentication, if SSO is not enabled |  |

### Browser Cache Management

| **Field** | **Description / Value** |
| --- | --- |
| Browser cache Managemnt | Enabled |
| Automatically install Browser cache Management | Disabled |
| Default cache scrubbing level | **2** |
| Clear history when browser windo is closed | Disabled |
| Disallow attachments if not installed | Disabled |
| Maintain static code archive between browser sessions | Enabled |

### Other Settings

| **Field** | **Description / Value** |
| --- | --- |
| Archiving on server | Enabled |
| Full-text indexing | Enabled |
| Modification of Internet Password | Enabled |
| Calendar Printing | Enabled |
| HCL iNotes ActiveX file attachment utility | Enabled |
| Compress HTTP response data | Enabled |
| Rooms and Resources | Enabled |
| Reuse Child Windows | Disabled |
| Local Archiving | Disabled |

### Disclaimer Text

| **Field** | **Description / Value** |
| --- | --- |
| Add disclaimer notice to mail memo | At the bottom |
| Disclaimer text or HTML | {empty} |

## IMAP
This chapter explains the IMAP settings 

### Basic

| **Field** | **Description / Value** |
| --- | --- |
| Maximum number of IMAP sessions |  |
| IMAP Session timeout | 30 minutes |
| Enable IMAP during login | Disabled |

### Public and Other users Folder

| **Field** | **Description / Value** |
| --- | --- |
| Public and other users folders support | Enabled |
| Include all public and other users folders when a folder list is requested | Enabled |
| Public folder prefix | Public Foders |
| Public folder database links |  |
| Other users folder prefix | Other Users |
| Other users domain delimiter |  |
| IMAP users who can change other users unread marks |  |

### Advanced

#### Greeting

| **Field** | **Description / Value** |
| --- | --- |
| IMAP server greeting | IMAP Server Ready at %S |
| IMAP SSL greeting | IMAP Server Ready at %S |
| IMAP SSL redirect greeting |  |

#### Worker thread pool

| **Field** | **Description / Value** |
| --- | --- |
| Maximum number of IMAP worker threads |  |
| Maximum number of response threads per FETCH | 4 |
| Maximum number of FETCH threads allowed |  |
| Maximum number of FETCH response threads allowed |  |

#### 

## Activity Logging

### Activity Logging

| **Field** | **Description / Value** |
| --- | --- |
| Activity logging is enabled: | Disabled <br> Note: Was enabled before in order to be used for Activity Trends. |

#### Server Activity Logging Configuration

| **Field** | **Description / Value** |
| --- | --- |
| Enabled logging types: | Domino.Notes.Database
Domino.Notes.Session <br> Note: 
When enabled these two logging types are needed for Activity Trends. |
| Checkpoint interval: | 15 minutes |
| Log checkpoint at midnight: | Yes |
| Log checkpoints for prime shift: | Yes |
| Prime shift interval: | 09 – 17 |

### Activity Trends

#### Basics

##### Activity Trends Basic Configuration

| **Field** | **Description / Value** |
| --- | --- |
| Enable activity trends collector: | **Enabled** |
| Activity trends collector database path: | activity.nsf |
| Time of day to run activity trends collector: | 3:23 <br> Note: The trends collector needs to be run after the daily catalog task has finished. Set the time to a value which meets this criteria for your server. |
| Days of the week to collect observations: | Enabled for all days including Sat/Sun |

##### Activity Trends Data Profile Options

| **Field** | **Description / Value** |
| --- | --- |
| Use defaults | Enabled |

#### Retention

##### Activity Trends Retention Periods

| **Field** | **Description / Value** |
| --- | --- |
| Use defaults | Enabled |

#### Proxy Data

##### Activity Trends Proxy Databases

| **Field** | **Description / Value** |
| --- | --- |
| Local databases containing trends data from other servers: | {blank} |

## Diagnostics
Diagnostic collection is used to collect all Domino crash information of every server on one central point in the domain. To enable this option a Fault report mail-in database has to be created on one central server in the domain.
We suggest using the hub server of the domain for that purpose.
You have to create a new mail-in database on this central server using the template ”Lotus Notes/Domino Fault Reports” (lndfr.ntf).
The address of this mail-in database has to be put into the field ”Mail-in Database for diagnostic reports” on every server of the domain.
In addition you need to enable the option ” Run FaultAnalyzer on Fault DBs on this server:” on the central server where the mail-in database resides on.

### Diagnostic Collection Options

| **Field** | **Description / Value** |
| --- | --- |
| Mail-in Database for diagnostic reports: |  |
| Maximum size of diagnostic message including attachments (in MB): | 50 |
| Maximum size of NSD output to attach (in MB): | 40 |
| Maximum amount of console output file to attach (in KB): | 10240 |
| Diagnostic file patterns: |  |
| Remove diagnostic files after a specified number of days: | Yes |
| Number of days to keep diagnostic files: | 60 |

### Fault Analyzer

| **Field** | **Description / Value** |
| --- | --- |
| Run FaultAnalyzer on Fault DBs on this server: |  |
| Run Fault Analyzer on: | Specific mail-in databases |
| Databases to run fault analyzer against: | Only to be configured for the server, that runs the Fault Analyzer task. <br> Path and file name of fault analyzer database.  <br> System/lndfrsrv.nsf |
| Remove attachments from duplicate faults: | No |

### Active Directory Password Sync

### Global settings

| **Setting** | **Description / Value** |
| --- | --- |
| Sync Active Directory passwords to Domino | Notes ID and HTTP Password <br> |
| Password change requests expire after | 360 minutes |
| Managers of password sync request databases: |  |
| AD Domain Controller settings |  |
| Configuration refresh interval | 5 minutes |
| Statistics output interval | 30 minutes	(Enter zero to disable statistics logging) |
| Debug level | Errors only |

### Administration

| **Setting** | **Description / Value** |
| --- | --- |
| Owner | LocalDomainAdmins |
| Administrator | LocalDomainAdmins |
