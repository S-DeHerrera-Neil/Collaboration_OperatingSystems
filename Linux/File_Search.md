## Find a file by filename
```
find / -name "*filename*" 2>/dev/null
```

## Find a file by contents
```
find / -type f -exec grep "searchtext" {} 2>/dev/null \;
```
