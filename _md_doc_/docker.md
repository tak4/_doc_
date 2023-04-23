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

image をここで探せる



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

docker network ls


### Word Press 構築

https://hub.docker.com/_/mysql
docker pull mysql

docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=administrator -d mysql:latest
docker exec -it some-mysql bash
mysql -u root -p
create database wpdb;
create user 'wpadmin'@'localhost' identified by 'lindbergh';
grant all on wpdb.* to 'wpadmin'@'localhost';




※没
docker run -it --rm mysql mysql -u root -p
docker run -it --rm mysql mysql -hsome-mysql -uexample-user -p
docker run --name some-mysql --network bridge -it -e MYSQL_ROOT_PASSWORD=administrator --rm mysql mysql -u root -p
docker run --name some-mysql --network simple-network -it -e MYSQL_ROOT_PASSWORD=administrator --rm mysql mysql -u root -p

https://hub.docker.com/_/wordpress
docker pull wordpress
docker run --name some-wordpress -p 8080:80 -d wordpress

docker run --name some-wordpress -p 8080:80 -e WORDPRESS_DB_HOST=127.0.0.1 -e WORDPRESS_DB_USER=wpadmin -e WORDPRESS_DB_PASSWORD=lindbergh -e WORDPRESS_DB_NAME=wpdb -d wordpress

docker exec -it some-wordpress bash

※没
docker run --name some-wordpress -p 8080:80 -d wordpress -e WORDPRESS_DB_USER=wpadmin -e WORDPRESS_DB_PASSWORD=lindbergh -e WORDPRESS_DB_NAME=wpdb
docker run --name some-wordpress -p 8080:80 -e WORDPRESS_DB_HOST=127.0.0.1:3306 -e WORDPRESS_DB_USER=wpadmin -e WORDPRESS_DB_PASSWORD=lindbergh -e WORDPRESS_DB_NAME=wpdb -d wordpress
docker run --name some-wordpress --network some-network -d wordpress
docker run --name some-wordpress -p 8080:80 -d wordpress

docker run --name some-wordpress -d wordpress

### MySQL

https://dev.mysql.com/downloads/workbench/