see sudo permissions
```
sudo -l
```
find SUID only files
```
find / -type f -perm /4000 -ls 2>/dev/null
```
find SGID only files
```
find / -type f -perm /2000 -ls 2>/dev/null
```
find SUID and SGID files
```
find / -type f -perm /6000 -ls 2>/dev/nul
```
the ways you can ABUSE MISCONFIGURATIONS and escalate and whatever
```
https://gtfobins.github.io/
```
