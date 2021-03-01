# OSCP_CheatSheet

## PortScan
- pingscan  
`sudo nmap -sn 10.11.1.0/24 -n -oA 10.11.1.0_24-pingscan`

- ArpScan  
`netdiscover -r 10.11.1.0/24`

- TCP Syn-scan all port  
`sudo nmap -sS -p- 10.11.1.1 -oA 10.11.1.1-tcp-allscan`

- netbios  
`sudo nbtscan -r 10.11.1.0/24`


## Enumration

## Password Crack

## Connection
- Netcat  
Connect `nc -nv <IPaddress>`  
Listen `nc -nlvp 9999`  
File transfer `nc -nlvp 9999 > test.txt`

- Telnet  
`telnet 192.168.1.1 443`

## nikto
-http-basi pattern  
`nikto -Display on -host 10.11.1.71 -o 10.11.1.71-80-nikto.txt`


## 権限昇格(Linux)

- sudo設定
