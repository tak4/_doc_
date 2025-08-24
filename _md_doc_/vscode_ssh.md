
# WSL

## クライアント側で認証用の鍵を作成

ssh-keygen -t rsa -b 4096

## （クライアント側→サーバ側）公開鍵をコピー・サーバ側に設置

scp ./.ssh/id_ubuntu_pc_rsa.pub takashi@192.168.1.3:~/tmp.pub

ssh takashi@192.168.1.3 "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat ~/tmp.pub >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys && rm -f ~/tmp.pub"

## 接続テスト

ssh -i ./.ssh/id_ubuntu_pc_rsa takashi@192.168.1.3


# Windows

## クライアント側で認証用の鍵を作成

ssh-keygen -t rsa -b 4096

## （クライアント側→サーバ側）公開鍵をコピー・サーバ側に設置

scp C:\Users\takashi\.ssh\id_ubuntu_pc_rsa.pub takashi@192.168.1.3:~/tmp.pub

ssh takashi@192.168.1.3 "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat ~/tmp.pub >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys && rm -f ~/tmp.pub"
