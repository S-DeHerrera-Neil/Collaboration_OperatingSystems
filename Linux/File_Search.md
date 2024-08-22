> [!NOTE]
> running `sudo -l` allows you to see what permissions work with sudo and can avoid logging sudo violations

## Find a file by filename 
```
find / -name "*filename*" 2>/dev/null
```

## Find hidden Files
```
find / -type f 2>/dev/null | grep "/\."
```

## Find a file by contents
```
find / -type f -exec grep "searchtext" {} 2>/dev/null \;
```
