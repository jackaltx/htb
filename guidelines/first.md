# Guidelines and Aproaches

## Terminal setup

Either be in root or use sudo. 
Create three tabs (VPN, NMAP, HACK).

## Enumeration

First comes nmap.
```
# nmap -p- -T4 -sV -sC -A -oN <ip address.txt> [ -oA <ip address> ]  <ip address>
```

### HTTP
if there is a web server open then you can use the NICTO web vulnerability scanner. 
```
# nikto -h http:\\<<ip address>
```
use browser to see if you can see any special files.
```
http://<ip address>/../../../../etc/password
```
another tack is to user DIRBUSTER with medium word list

### SMB

```
nmap --script smb-vuln* -p 445 <ip address>
```

use -N to suppress password promt
```
smbclient –L <ip address>
```


## after foothold

To provides a moderately stable shell look for python or python3
```
python3 -c "import pty;pty.spawn('bin/bash')
```

The goal is to get user access, so getting access is best
Download [LinEnum.sh](https://github.com/rebootuser/LinEnum) to machine.  One way is to use a python server
```
$ sudo python -m Simple/HttpServer 80
```

