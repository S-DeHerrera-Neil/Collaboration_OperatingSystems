# Who Creates log
- `syslog` daemon
  - Default on all linux machines
  - Defined in [RFC 5425](https://tools.ietf.org/html/rfc5424)
- `journald` daemon
  - Unique to certain distros

# Paths to Know
| descriptor | Path | Notes |
| ---------- | ---- | ----- | 
| Syslog config files | `/etc/rsyslog/` | |
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

### Syslog Codes
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
