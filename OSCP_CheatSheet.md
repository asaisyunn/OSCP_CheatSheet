# OSCP_CheatSheet

## PortScan
- pingscan  
`sudo nmap -sn 10.11.1.0/24 -n -oA 10.11.1.0_24-pingscan`

- TCP Synscan all port
`sudo nmap -sS -p- 10.11.1.1 -oA 10.11.1.1-tcp-allscan`
## Enumration

## Password Crack

## Connection
- Netcat  
Connect `nc -nv <IPaddress>`  
Listen `nc -nlvp 9999`  
File transfer `nc -nlvp 9999 > test.txt`

- Telnet  
`telnet 192.168.1.1 443`
