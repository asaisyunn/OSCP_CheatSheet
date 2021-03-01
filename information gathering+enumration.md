# PortScan

## nmap
### Alive hosts scan
`nmap -sn 10.0.0.0/24`

### 1024 most common ports
`nmap -oA nmap <targetip>`

### full connect-scan
`nmap -v -sT <targetip> -p- `

### full tcp syn-scan
`nmap -sS -O -v -p 1–65535 <targetip>`

### tcp spec service scan
`nmap -sS -A -v -p <port> <targetip>`

### ftp
