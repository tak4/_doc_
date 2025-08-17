Ubuntuで使用しているネットワークデバイスに対応するデバイスドライバを見つける方法は以下のような手順があります。

1. ネットワークデバイスの情報を調べる
```bash
lspci | grep -i network
```
または有線LANなら
```bash
lspci | grep -i ethernet
```
無線LANなら
```bash
lspci | grep -i wireless
```
これでネットワークカードの型番やベンダー情報が分かります。

2. 実際に使用しているドライバを確認する
```bash
ethtool -i インターフェース名
```
例: eth0やenp3s0など
これで「driver」項目に現在使われているドライバ名が表示されます。

3. カーネルにロードされているドライバモジュールを確認する
```bash
lsmod | grep ドライバ名
```
ドライバ名がわからなければ、
```bash
lsmod
```
で全表示してネットワーク関係のモジュールを探します。

4. 起動メッセージからドライバ情報を探る
```bash
dmesg | grep -i ethernet
```
や
```bash
dmesg | grep -i ドライバ名
```
でカーネルログにドライバのロード情報が出ている場合があります。

5. 詳細を調べる場合は
```bash
modinfo ドライバ名
```
でドライバのバージョンや説明、依存関係なども確認できます。

6. udevからのデバイス情報も確認可能
```bash
udevadm info --query=all --path=/sys/class/net/インターフェース名
```

***

これらのコマンドを使うことで、Ubuntuで使っているネットワークデバイスに対応するドライバ名やバージョン、ロード状況を詳しく調べることができます。もしドライバが当たっていない場合は上記のデバイス情報をもとにネット検索やメーカーサイトで対応ドライバを探すのが一般的です。

[1] http://sweng.web.fc2.com/ja/linux/ubuntu/check-net-driver.html
[2] https://www.na3.jp/entry/20140121/p1
[3] https://qiita.com/matsuo7005/items/b0037b6450d752378316
[4] https://www.pc-koubou.jp/magazine/36572
[5] https://www.linux.digibeatrix.com/troubleshooting/ubuntu-24-04-network-troubleshooting/
[6] https://qiita.com/bunnyhopper_isolated/items/40aea93b72fb11a0d6a0
[7] https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html.ja
[8] https://detail.chiebukuro.yahoo.co.jp/qa/question_detail/q10277388495
[9] https://pc.watch.impress.co.jp/docs/column/ubuntu/1509181.html
[10] https://3ryupg.hatenablog.com/entry/2018/06/05/220000