> [!Note]

## Find All Files Recursively
```
get-childitem -force -recurse -erroraction SilentlyContinue | Select Mode, LastWriteTime, Fullname
```
## Find Files with ADS
```
Get-Childitem -path C:\Users\CTF -force -recurse -ErrorAction 'silentlycontinue' | ForEach-Object {Get-Item $_.fullname -Stream * | Where-Object {$_.stream -cnotmatch '.*DATA.*'} } 2>$null
```
## Find Hidden Files
```
Get-Childitem -Path C:\Users\CTF -Recurse -hidden 2>$null
```

## Search by Filename
```
Get-Childitem -Path C:\Users\CTF -Force -Recurse -Include '*key*' 2>$null
```
## Search by Contents
```
Get-Childitem -path C:\Users\CTF -force -recurse -ErrorAction 'silentlycontinue' | ForEach-Object {Get-Content $_.fullname | Where-Object {$_.stream -cmatch '.*SEARCH_KEY.*'} } 2>$null
```
