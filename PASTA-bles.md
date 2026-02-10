## MASTER SOCKETS AND FORWARDING
```
ssh -MS /tmp/jmp student@10.50.16.246
```
<sub> initial master socket to jump box <sub>
```
  ssh -S /tmp/jmp jmp -O forward -L 21630:192.168.28.100:2222
```
<sub> from the jump box to the target 1 <sub>
```
      ssh -S /tmp/jmp jmp -O forward -D 9050
```
<sub> dynamic port open <sub>
```
      ssh -S /tmp/jmp jmp -O cancel -D 9050
```
<sub> dynamic port close <sub>
#### TUNNEL TO T1
```
ssh -p21630 -MS /tmp/t1 www-data@127.0.0.1
```
<sub> mew master socket starting at target 1, referncing previously made port from the first port forward <sub>
```
  ssh -S /tmp/t1 t1 -O forward -L 21631:192.168.150.253:3201
```
<sub> port forward from target 1 to the NEXT ip <sub>
```
      ssh -S /tmp/t1 t1 -O forward -D 9050
```
<sub> dynamic port open <sub>
```
      ssh -S /tmp/t1 t1 -O cancel -D 9050
```
<sub> dynamic port close <sub>

#### TUNNEL TO TARGET AFTER T1
``` 
ssh -p21631 -MS /tmp/intra comrade@127.0.0.1
```
<sub> new master socket to the NEXT BOX <sub>
```
    ssh -S /tmp/intra intra -O forward -D 9050
```
<sub> dynamic port open <sub>
```
    ssh -S /tmp/intra intra -O cancel -D 9050 
```
<sub> dynamic port close <sub>



## STOLEN KEY
```
chmod 600 /home/user/stolenkey    #done on linops BEFORE ATTEMPTING to use the key in ssh command
                                  #
```
<sub>done on linops BEFORE ATTEMPTING to use the key in ssh command <sub>
<sub>IF YOU ACCIDENTALLY SKIP THIS STEP, RENAME the key file, chmod it and move on <sub>
```
ssh -i /home/user/stolenkey jane@10.20.30.40
```

## RDP FROM LINUX (XFREERDP)
```
proxychains xfreerdp /u:comrade /p:StudentMidwayPassword /v:192.168.28.9 /clipboard
```







