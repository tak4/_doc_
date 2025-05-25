# open-ssh

インストール

```bash
sudo apt update
sudo apt install openssh-server
```

インストール状況確認

クライアント

```bash
ssh -V
```

sshサービス起動確認

確認

```bash
service --status-all | grep ssh
```

起動中

```bash
 [ + ]  ssh
```

停止中

```bash
 [ - ]  ssh
```

サービス起動／停止（一時的） ※方法１

```bash
sudo service ssh start

```

```bash
sudo service ssh stop
```

サービス起動／停止（一時的）　※方法２

```bash
sudo systemctl start ssh
```

```bash
sudo systemctl stop ssh
```

サービス有効／無効（恒久的）　

※WSLの場合、systemd が完全にサポートされない為、再起動するとsshは有効にならない

有効化

```bash
sudo systemctl enable ssh
```

無効化

```bash
sudo systemctl disable ssh
```

サービス有効／無効　状態確認

```bash
sudo systemctl is-enabled ssh
```