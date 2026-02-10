## MASTER SOCKETS AND FORWARDING
```
ssh -MS /tmp/jmp student@10.50.16.246
```
> initial master socket to jump box
```
  ssh -S /tmp/jmp jmp -O forward -L 21630:192.168.28.100:2222
```
> from the jump box to the target 1
```
      ssh -S /tmp/jmp jmp -O forward -D 9050
```
> dynamic port open
```
      ssh -S /tmp/jmp jmp -O cancel -D 9050
```
> dynamic port close
#### TUNNEL TO T1
```
ssh -p21630 -MS /tmp/t1 www-data@127.0.0.1
```
> mew master socket starting at target 1, referncing previously made port from the first port forward 
```
  ssh -S /tmp/t1 t1 -O forward -L 21631:192.168.150.253:3201
```
> port forward from target 1 to the NEXT ip
```
      ssh -S /tmp/t1 t1 -O forward -D 9050
```
> dynamic port open
```
      ssh -S /tmp/t1 t1 -O cancel -D 9050
```
> dynamic port close

#### TUNNEL TO TARGET AFTER T1
```
ssh -p21631 -MS /tmp/intra comrade@127.0.0.1
```
> new master socket to the NEXT BOX
```
    ssh -S /tmp/intra intra -O forward -D 9050
```
> dynamic port open
```
    ssh -S /tmp/intra intra -O cancel -D 9050 
```
> dynamic port close



## STOLEN KEY
```
chmod 600 /home/user/stolenkey    #done on linops BEFORE ATTEMPTING to use the key in ssh command
                                  #IF YOU ACCIDENTALLY SKIP THIS STEP, RENAME the key file, chmod it and move on
```
```
ssh -i /home/user/stolenkey jane@10.20.30.40
```

## RDP FROM LINUX (XFREERDP)
```
proxychains xfreerdp /u:comrade /p:StudentMidwayPassword /v:192.168.28.9 /clipboard
```







