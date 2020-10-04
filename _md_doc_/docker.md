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
http://docs.docker.jp/v1.9/#

Docker 入門
https://knowledge.sakura.ad.jp/13795/

### インストール
Docker Hub インストーラ
Docker Hub は、Windows/Macでの利用の場合に使用する？ 
https://docs.docker.com/docker-for-windows/install/

### CLI

バージョン確認  
https://docs.docker.com/engine/reference/commandline/version/
`docker --version`

ローカル環境のImageの一覧を確認  
`docker images`

Imageの取得  
`docker pull`

実行 Image -> Container へ変化  
`docker run`

ローカル環境のContainerの一覧を確認  
`docker ps -a`

Image 作成  
`docker commit`

Docker Indexへ配置  
`docker push`
