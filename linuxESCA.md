# sudo 
see sudo permissions
```
sudo -l
```
find **_SUID_** only files
```
find / -type f -perm /4000 -ls 2>/dev/null
```
find **_SGID_** only files
```
find / -type f -perm /2000 -ls 2>/dev/null
```
find **_SUID_** and **_SGID_** files
```
find / -type f -perm /6000 -ls 2>/dev/nul
```
the ways you can **_ABUSE_** **MISCONFIGURATIONS**__ and escalate and whatever
```
https://gtfobins.org/
```

1. sudo -l (TOP 5 AND BOTTOM 5),
2. open up gtfobins,
3. in the filter box type in one of things you have perms on, ie. mount, nice, etc.
4. CLICK ON SUID, copy command (nice /bin/sh -p) into terminal

# cron



# checking logs

auth.log/secure  -  Logins/authentications

lastlog  -  Each users' last successful login time

btmp  -  Bad login attempts

sulog  -  Usage of SU command

utmp  -  Currently logged in users (W command)

wtmp  -  Permanent record on user on/off




# dot in path?

echo $PATH

> replicate dot in path


PATH=.:$PATH
























touch cat
vim cat

#!/bin/bash
echo meow meow meow

