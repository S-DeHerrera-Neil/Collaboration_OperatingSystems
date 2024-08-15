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

### Syslog Facilities Codes (Source of Events)
| Code | Facility | - | Code | Severity |
| ---- | -------- | - | ---- | -------- |

| 0 | kernel messages | | | | |
| 1 | user-level messages |
| 2 | mail system |
| 3 | system daemons |
| 4 | security/authorization messages |
| 5 | messages made by syslogd |
| 6 | line printer subsystem |
| 7 | network news subsystem |

### Syslog Severity Codes

| Code | Severity |
| ---- | -------- |
| 0 | Emergency |
| 1 | Alert |
| 2 | Critical |
| 3 | Error |
| 4 | Warning |
| 5 | Notice |
| 6 | Informational |
| 7 | Debug |
