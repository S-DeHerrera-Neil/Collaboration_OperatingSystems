# Logs and Where they are

# Understanding syslog, rsyslog, and syslog-ng Codes

# Syslog Formatting

### Entry Formatting
`facility`. `severity` `/path/to/log/location`

### Syslog Facilities Codes (Source of Events)
| Code | Facility |
| ---- | -------- |
| 0 | kernel messages |
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
