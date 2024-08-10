# Windows Directory
	
 ## File Search -File(Windows)
	- contents search
	- filename search
	- attribute search

## Registry -File(Windows)
	   - persistence
	   - user specific information (SIDs, running processes, etc)
### *Boot* -File(Windows)
    - bcdedit
    - getting out of safe boot	
 # Processes / Services -File(Windows)
    - search for processes
     - tie to persistent processes (services.msc)	
# Logging / Security -File(Windows)
    - Where do security logs go?
    - Reading windows logs (if we actually go over that)
# Linux Directory -file(Linux)
## File Search -File(Linux)
    - contents search
    - filename search
    - attribute search   
### *Boot* -File(Linux)
	   - persistence
	   - user specific information (SIDs, running processes, etc)
		 - using dd, xxd, hexdump, etc to manipulate binary files
		 - navigate init
### *Logging / Security* -File(Linux)
		- sudo logging ( where failed sudo commands go)
    - rsyslog, where logs go
### Processes / Services -File(Linux)
    - search by processes
