# Who Creates log
- `syslog` daemon
  - Default on all linux machines
  - Defined in [RFC 5425](https://tools.ietf.org/html/rfc5424)
- `journald` daemon
  - Unique to certain distros

# Paths to Know
| descriptor | Path |
| ---------- | ---- |
| Syslog config files | /etc/rsyslog/ |
| Default log location | /var/log/ |


# Syslog Formatting

### Entry Formatting
`facility`. `severity` `/path/to/log/location`

### Syslog Codes
| Code | Facility | - | Code | Severity |
| ---- | -------- | - | ---- | -------- |
| 0 | kernel messages | | 0 | Emergency |
| 1 | user-level messages | | 1 | Alert |
| 2 | mail system | | 2 | Critical |
| 3 | system daemons | | 3 | Error |
| 4 | security/authorization messages | | 4 | Warning |
| 5 | messages made by syslogd | | 5 | Notice |
| 6 | line printer subsystem | | 6 | Informational |
| 7 | network news subsystem | | 7 | Debug |



| hello | world |
| ----- | ----- |
