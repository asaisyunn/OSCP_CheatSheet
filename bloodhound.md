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

https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a
