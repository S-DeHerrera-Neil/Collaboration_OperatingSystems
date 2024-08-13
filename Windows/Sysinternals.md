# Downloading Sysinternals

## Method 1: Link Drive (CMD or Powershell)
```
PS C:\Users\student> net use * http://live.sysinternals.com
PS C:\Users\student> z:
```
This creates a seperate z drive that holds all sysinternals tools

Note: move all sysinternals tools to `C:\Users\<yourusername>\AppData\Local\Microsoft\WindowsApps` to be able to use them from anywhere, I.E:
```
mv Z:\* C:\Users\<yourusername>\AppData\Local\Microsoft\WindowsApps
```

## Method 2: Install via web gui
- Download Sysinternals Suite via https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite
- copy zip file to `C:\Users\<yourusername>\AppData\Local\Microsoft\WindowsApps`
- unzip all files (powershell command: `expand-archive -path <infile> -destinationpath <outfile>`)

## Method 3: install via powershell

look it up
