# Who Creates log
- `syslog` daemon
  - Default on all linux machines
  - Defined in [RFC 5425](https://tools.ietf.org/html/rfc5424)
- `journald` daemon
  - Unique to certain distros

# Paths to Know
| descriptor | Path | Notes |
| :--- | ---- | ----- | 
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
| Ubuntu/Debian Catch all | /var/log/syslog | |
| Device Messenger | run `dmesg` | This queries /proc/kmsg |

# Syslog Formatting

### Syslog Codes
| Code | [Facility](https://en.wikipedia.org/wiki/Syslog#Facility) | [Severity](https://en.wikipedia.org/wiki/Syslog#Severity_level) |
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

### Entry Formatting
`facility.severity /path/to/log/location`


`facility.severity @@X.X.X.X:Port` (see syntax for difference between `@` and `@@`)


### [Syntax](https://man7.org/linux/man-pages/man5/rsyslog.conf.5.html)
- Severity
  - `=` means only this severity
  - `!` means exclude this and any higher severities
  - `!=` means exclude only this severity
- Path
  - `-` enables syncing (I.E: `-/var/log/messages`)
  - `@` forward logs to a specified IP and port via UDP
  - `@@` forward logs to a specified IP and port via TCP

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

# Using XPATH (reading XML)
XPATH is a linux command and tool to parse through .XML files and grab the desired values. Essentially regex for XML files

testing tool: [xpather](http://xpather.com/) (similar to regex101)

### [Syntax](http://www.whitebeam.org/library/guide/TechNotes/xpath.rhtm)
```
xpath -q -e `//path/to/the/element/@theattribute` <searchfile>
```
- `-q` quiet output, removes unneccessary output
- `-e` required before an expression
- `//` this is the start to an expression
  - `path/to/element`

### Examples
```
xpath -q -e '//host/address/@addr' output.xml
```
grabs all ips from the nmap xml file

```
xpath -q -e '//host/address/@addr | //host/ports/port/@portid' output.xml
```
grabs all ips and portids from the nmap xml file

```
xpath -q -e '//host/ports/port/@portid | //host/ports/port/@portid/../../../address/@addr' output.xml
```
This grabs all ips with open ports and all ports

this is pretty complicated and a bit inefficient so lets delve into it:
- `//host/ports/port/@portid` grabs all the port ids
- `//host/ports/port/@portid/../../../address/@addr` So what this does is try to go to the portid element then goes back up to grab the address (this means that it will fail if portid would fail)


# Using JQ (JSON Query)
JQ is a linux command and tool to parse through .JSON files and grab the desired information. Essentially regex for JSON files

- [Cheat Sheet](https://cheat.sh/jq)

### Examples


```
cat conn.log | jq .
```
prints a JSON file in "pretty" print

```
cat conn.log | jq '."id.orig_h"' | sort -u | wc -l
```
read a file, grab the "id.orig_h" element and grab the count of unique lines

```
cat conn.log | jq 'select(.resp_bytes >= 40).ts' | wc -l # select the ts line from all blocks where "resp_bytes" >= 40 and gets the count
cat conn.log | jq '.resp_bytes >= 40' | grep "true" |wc -l # gets boolean values for each resp_bytes value, filters out falses and gets the count
```
grabs the count of lines where resp_bytes is greater than or equal to 40

```
cat conn.log | 
```
