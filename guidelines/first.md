# Guidelines and Aproaches

## Terminal setup

Either be in root or use sudo. 
Create three tabs (VPN, NMAP, HACK).

## Enumeration

First comes nmap.  Note -oA is handy for using zenmap, but it not on kali 
```
# nmap -p- -T4 -sV -sC -A -oN <ip address.txt> [ -oA <ip address> ]  <ip address>
```

### HTTP
if there is a web server open then you can use the NICTO web vulnerability scanner. 
```
# nikto -h http://<<ip address>
```
use browser to check for LFI (Local File Inclusion) if you can view the data of any special files.
```
# http://<ip address>/../../../../etc/password
```
another tack is to user DIRBUSTER with medium word list

Gobuster 3.X.X is newer and has a lot more features it can be used with the following:
```
# gobuster dir -u http://<ip address> -w /location/of/wordlist.txt
```
### SMB

```
# cd /usr/share/nmap/scripts/
# nmap --script smb-vuln* -p 445 -oA ~/smb_vulns.txt <ip address>
```

TODO: describe
```
# cackmapexec smb \\<ip address>
# cackmapexec smb \\<ip address> --shares
```

use -N to suppress password prompt. Using the 'invalid' user with a <cr> password will connect with a 'guest' session.
```
# smbclient -U invalid –L \\<ip address>
```

If nothing works, use smbmap as above which will show permissions on any shares
```
# smbmap -U invalid –L \\<ip address>
```

If you can mount profiles$ and there are any intersting user then you can collect them in a  file of usernames 
```
# smbclient -U <username>%invalid –L \\<ip address> -c ls | awk { print $1 } > users.txt
```

If this is a Domain Controller then use a kerberos preauthentication hack
```
$ kerburte userenum -dc <ip address> -d <domain name> users.txt
``

## after foothold

To provides a moderately stable shell look for python or python3
```
python3 -c "import pty;pty.spawn('bin/bash')"
```

The goal is to get user access, so getting access is best
Download [LinEnum.sh](https://github.com/rebootuser/LinEnum) to machine.  One way is to use a python server
```
$ sudo python -m Simple/HttpServer 80
```

