# Background

This is a windows exploit. 

## Enumeration

```
nmap -i tun0 -sV -sC -A -On <ip address>.txt <ip_address
```

Use RCE the IIS 6.0 on port 80 from "Exploit Database"

## get use

- metasploit use iis/scstoragepathfromurl
- opens session

## get admin

- background (note: can use "sessions" to get session list)
- metasploit use local_exploit_suggester
- use tcpip_ioctl on a runnig as "NETWORK SERVICE" user
- migrate <pid}
- nt authority\system

