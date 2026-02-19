## Docker

軽量な仮想環境  
Build once, run anyuwhere  

Image を作成、もしくは、Docker Index から取得し、実行する(Image->Container)  
ContainerからImage作成することも可能 (Build)  
このあたりの手順を自動化することも可能 DockerFileに記述する


## ドキュメント
公式サイト  
https://docs.docker.com/
https://docs.docker.com/get-started/

Docker ドキュメント日本語化プロジェクト  
https://docs.docker.jp/index.html

Docker 入門  
https://knowledge.sakura.ad.jp/13795/

実践 Docker - ソフトウェアエンジニアの「Docker よくわからない」を終わりにする本  
https://zenn.dev/suzuki_hoge/books/2022-03-docker-practice-8ae36c33424b59

## install

### Docker Desktop on Windows
for windows  
https://docs.docker.com/docker-for-windows/install/


### Docker Engine
for ubuntu  
https://docs.docker.com/engine/install/ubuntu/

Uninstall old versions
```
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

Install using the apt repository

Set up Docker's apt repository.
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

Install the Docker packages.
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

docker deamon 起動状況確認
```
sudo systemctl status docker
```


### Docker公式のインストールスクリプトを実行する
https://matsuand.github.io/docs.docker.jp.onthefly/engine/install/ubuntu/#install-using-the-convenience-script

利用しているLinuxディストリビューションやCPUアーキテクチャを自動判別し、最適なDockerパッケージをインストールする

```
wget -qO- http://get.docker.com/ | ${SHELL}
```
-q：ダウンロード中の進捗やメッセージを表示しない（quietモード）。
-O -：ダウンロードした内容をファイルではなく標準出力（画面や次のコマンド）に出力する。
| ${SHELL} で、ダウンロードしたスクリプトの内容をそのまま現在のシェルで実行します。

### CLI

バージョン確認  
https://docs.docker.com/engine/reference/commandline/version/  
`docker --version`

ローカル環境のImageの一覧を確認  
`docker images`

Imageの取得  
`docker pull`

実行 Image -> Container へ変化  コンテナ作成＆実行
`docker run`

https://docs.docker.jp/engine/reference/run.html

-d
デタッチド　バックグラウンド起動
-name
コンテナの識別
-e
環境変数

-p=[]
コンテナのポートまたはポート範囲をホスト側に公開する

コンテナ実行  
`docker start`

コンテナ停止  
`docker stop [CONTAINER ID]`

コンテナ削除  
`docker rm [CONTAINER ID]`

停止中の全コンテナ削除  
`docker container prune`

イメージ削除
`docker rmi [IMAGE ID]`

ローカル環境のContainerの一覧を確認  
`docker ps -a`

Image 作成  
`docker commit`

Docker Indexへ配置  
`docker push`

Docker ログ参照  
`docker logs [name]`
name は run で指定したもの

Docker Network  
`docker network ls`

コンテナの詳細情報を確認する  
`docker inspect [CONTAINER ID]`

file copy  

host > container  
`docker cp /path/to/host/file container_name:/path/in/container/`

container > host  
`docker cp container_name:/path/in/container/file /path/to/host/`

実例)  
`sudo docker cp ./test.txt c0b394c730ba:/home/builder`


`sudo docker container run --name ubuntu_22_04 --rm --interactive --tty ubuntu:22.04 bash`

# bunut 20.04

Install the Docker packages.
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```


https://hub.docker.com/layers/library/ubuntu/20.04/images/sha256-c664f8f86ed5a386b0a340d981b8f81714e21a8b9c73f658c4bea56aa179d54a

docker image 取得
```
sudo docker image pull ubuntu:20.04
```

```
sudo docker container run --name ubuntu2004 --rm --interactive --tty ubuntu:20.04 bash
```


起動中のContainerにアタッチする

既に接続している側とコンソールを共有する

```bash
docker attach [CONTAINER ID]
```

Ctrl+P → Ctrl+Q で、デタッチする

コンソールを共有せず、別bashで接続する

```bash
docker exec -it -tty dd39c763b06d bash
```

-it インタラクティブなシェル


# ユーザーを docker グループへ追加

docker コマンド実行時に sudo 不要となる。

vscode 拡張機能 Dev Containers を使用する時にもこの対応が必要らしい。

dockerグループへの追加前だと下記の状態

```bash
docker image ls
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Head "http://%2Fvar%2Frun%2Fdocker.sock/_ping": dial unix /var/run/docker.sock: connect: permission denied
```

docker グループの存在、及び、グループIDを確認する

```bash
cat /etc/group | grep docker
docker:x:999:takashi
```

ユーザーがdockerグループに追加されているか確認する

追加前

```bash
id
uid=1000(takashi) gid=1000(takashi) groups=1000(takashi),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),116(netdev)
```

追加後

```bash
id
uid=1000(takashi) gid=1000(takashi) groups=1000(takashi),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),116(netdev),999(docker)
```

ユーザーをグループへ追加／削除

追加／削除後は再ログインが必要

追加

```bash
sudo gpasswd -a takashi docker
```

削除

```bash
sudo gpasswd -d takashi docker
```


## Dockerfile

DockerfileからDocker iamgeを作成する

Dockerfile
```
FROM ubuntu:20.04

RUN apt update
RUN apt install -y vim

COPY .vimrc /root/.vimrc

CMD date +"%Y/%m/%d %H:%M:%S ( UTC )"
```

image の ビルド
```
docker image build     \
    --tag my-ubuntu:date \
    .
```

作成したimage
```
docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
my-ubuntu    date      90bc6f39d53c   About a minute ago   199MB
ubuntu       20.04     b7bab04fd9aa   7 months ago         72.8MB
```

作成したimageでコンテナ起動
```
docker container run \
    --name my-ubuntu1  \
    --rm               \
    my-ubuntu:date
```

## volume

volumeを確認する
```
docker volume ls
```

```
docker container run                                  \
    --name volume_test                                \
    --rm                                              \
    --interactive                                     \
    --tty                                             \
    --volume ./workspace:/workspace                   \
    ubuntu:20.04                                      \
    bash
```

## commit

Docker container から Dokcer imageを作成する

```
docker commit [CONTAINER ID] volume_test:latest
```

コンテナ起動
```
docker container run                                  \
    --name volume_test                                \
    --rm                                              \
    --interactive                                     \
    --tty                                             \
    volume_test:latest                                \
    bash
```

# ubuntu 22.04

docker image 取得
```
sudo docker image pull ubuntu:22.04
```

カレントディレクトリのDockerfileより、docker imageをbuild
```
sudo docker build -t ubuntu:build-essential .
```

ubuntu:build-essential という image を使用して、ubuntu という名前でContainerを作成して、起動する。
--rm：Container 終了時に、Container削除する。
--interreactive：標準入力を開いたままにし、コンテナ内で対話的な操作を可能にする。
```
sudo docker container run --name ubuntu --rm --interactive --tty ubuntu:build-essential
```

