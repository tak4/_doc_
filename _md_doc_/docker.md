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

## install

### Docker Desktop on Windows
for windows  
https://docs.docker.com/docker-for-windows/install/


### Docker Engine
for ubuntu  
https://docs.docker.com/engine/install/ubuntu/



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

イメージ削除
`docker rmi [イメージID]`

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

file copy  

host > container  
`docker cp /path/to/host/file container_name:/path/in/container/`

container > host  
`docker cp container_name:/path/in/container/file /path/to/host/`

実例)  
`sudo docker cp ./test.txt c0b394c730ba:/home/builder`
