# Guidelines and Aproaches

## Terminal setup

Either be in root or use sudo. 
Create three tabs (VPN, NMAP, HACK).

## Enumeration

First scans

```
# nmap -p- -sV -sC -A -oN <ip address.txt> [ -oA <ip address> ]  <ip address>
```

```
# nikto -h http:\\<<ip address>
```

use browser to see if you can see files

```
http://<ip address</../../../../etc/password
```

dirbuster with medium word list

## after foothold

To provides a moderately stable shell look for python or python3
```
python3 -c "import pty;pty.spawn('bin/bash')
```

download (LinEnum.sh)[https://github.com/rebootuser/LinEnum] to machine.  One way is to use a python server
```
$ sudo python -m Simple/HttpServer 80
```

