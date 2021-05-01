
### gobuster

    gobuster dir -u http://10.129.1.185/webservices -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
    gobuster dir -u <url> -w <wordlist_file.txt> -x <file_extensions>

### nikto  
    nikto -Display on -host 10.11.1.71 -o 出力ファイル名

### hydra

- post

    hydra -l /usr/share/wordlists/metasploit/default_users_for_services_unhash.txt -p admin 10.129.138.33 http-post-form "/api/session/authenticate:username=^USER^&password=admin:Login Failed"


### WordPress

- Vulnerable Plugins

    wpscan --url http://tartarsauce.htb/webservices/wp/ -e vp,vt,cb,dbe,u --plugins-detection aggressive -vv

- Popular Plugins

    wpscan --url http://tartarsauce.htb/webservices/wp/ -e p,vt,cb,dbe,u --plugins-detection aggressive -vv

- full

    wpscan --url http://tartarsauce.htb/webservices/wp/ -e ap,vt,cb,dbe,u --plugins-detection aggressive -o wpscan.log -vv

- passwordcrack
ユーザ名がとれている場合で、xmlrpcが使えるなら以下そのままで問題ない。（使えない場合`wp-login`）

httpsの場合
    wpscan --url https://brainfuck.htb/ -e u -P /usr/share/wordlists/rockyou.txt --password-attack xmlrpc --disable-tls-checks

httpの場合
    wpscan --url http://brainfuck.htb/ -e u -P /usr/share/wordlists/rockyou.txt --password-attack xmlrpc



### Drupal

バージョン情報はCHANGELOG.txtで確認できるけど、基本droopscanをまずは実行する。

    ./droopescan scan drupal -u http://10.129.139.15/
