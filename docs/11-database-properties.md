# Database Properties

## Fulltext index
A full text index can be created for application databases when needed.
For mail files, full text indexes should be created on the local replica, but never on a server.
When creating a Full Text Index the following settings should be used:

| **Field** | **Description / Value** |
| --- | --- |
| Index attached files | Disabled by default, <br> When enabled, only used with option “Using conversion filters” |
| Index encrypted fields | Disabled |
| Index sentence and paragraph breaks | Optional, disabled by default |
| Enabled case-sensitive searches | Optional, disabled by default |
| Update frequency (server only) |  |

## Design Properties

| **Field** | **Description / Value** |
| --- | --- |
| Refresh design on admin server only | Enabled 
if database inherits from any template |

## Advanced Database Properties

| **Field** | **Description / Value** |
| --- | --- |
| Don’t overwrite free space |  |
| Compress Database Design |  |
| Compress Document Data | Disabled |
