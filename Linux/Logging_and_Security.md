# Who Creates log
- `syslog` daemon
  - Default on all linux machines
  - Defined in [RFC 5425](https://tools.ietf.org/html/rfc5424)
- `journald` daemon
  - Unique to certain distros

# Paths to Know
| descriptor | Path | Notes |
| ---------- | ---- | ----- | 
| Syslog config files | `/etc/rsyslog.d/` | |
| Default log location | `/var/log/` | most logs are in /var/log, all logs are in /var |
| | | |
| ----- | Authentication | ----- |
| Authentication | /var/log/auth.log | |
| Logged in Users | /var/run/utmp | NOTE: this is not in a human readable format, use the `last` command to read it |
| History of utmp | /var/log/wtmp | NOTE: this is not in a human readable format, use the `last` command to read it |
| ----- | Application | ----- |
| ----- | System | ----- |
| Legacy Catch all | /var/log/messages | |
| Ubuntu/Debiam Catch all | /var/log/syslog | |
| Device Messenger | run `dmesg` | This queries /proc/kmsg |

# Syslog Formatting

### Entry Formatting
`facility`. `severity` `/path/to/log/location`

### [Syslog Codes](https://en.wikipedia.org/wiki/Syslog)
| Code | Facility | Severity |
| ---- | -------- | -------- |
| 0 | kernel messages | Emergency |
| 1 | user-level messages | Alert |
| 2 | mail system | Critical |
| 3 | system daemons | Error |
| 4 | security/authorization messages | Warning |
| 5 | messages made by syslogd | Notice |
| 6 | line printer subsystem | Informational |
| 7 | network news subsystem | Debug |
| 8 	| uucp 	| |
| 9 	| cron 	| |
| 10 	| authpriv 	| |
| 11 	| ftp 	| |
| 12 	| ntp 	| |
| 13 	| security 	| |
| 14 	| console 	| |
| 15 	| solaris-cron 	| |
| 16–23 	| local0 – local7 	| |
### Syntax
- Severity
  - `=` means only this severity
  - `!` means exclude this and any higher severities
  - 

### Examples
```
0.* /var/log/test
```
Logs all kernel messages of any severity to /var/log/test

```
*.4 /var/log/test
```
Logs messages from any facility of severity Warning and higher (Warning, Error, Critical, Alert, and Emergency) to /var/log/test

```
2.!2
```
Logs messages from mail system of severity Error and lower (Error,Warning,Notice,Informational,Debug) to /var/log/test
