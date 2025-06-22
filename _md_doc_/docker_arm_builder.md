# Install Arm Compiler for Linux
https://developer.arm.com/documentation/102621/latest/

# arm linker --info-stack
https://developer.arm.com/documentation/100070/0609/linker-command-line-options/--info-topic--topic---?lang=en

各関数ごとのスタックフレームサイズ（関数ごとにどれだけスタック領域を消費するか）  
関数呼び出し経路ごとの最大スタック使用量（どの経路でスタック消費が最大になるか）  
スタックオーバーフローのリスクがある関数や経路の特定  
スタック使用量の合計や最悪ケースの解析  

# arm linker --callgraph
https://developer.arm.com/documentation/101754/0624/armlink-Reference/armlink-Command-line-Options/--callgraph----no-callgraph?lang=en

# arm linker --callgraph_output=fmt
https://developer.arm.com/documentation/101754/0624/armlink-Reference/armlink-Command-line-Options/--callgraph-output-fmt?lang=en


# docker
ubuntu:22.04ベースで、arm compierをインストールする

docker インストール

https://docs.docker.com/engine/install/ubuntu/


docker image 取得

```
sudo docker image pull ubuntu:22.04
```

上記取得したimageは下記
https://hub.docker.com/layers/library/ubuntu/22.04/images/sha256-6f63292a7444f9346bf6ec6816dd93029dae021ee00cabb564c440417519680c


image 確認

```
sudo docker image ls
```


ubuntu:22.04 をベースに、

Dockerfile
```
FROM ubuntu:22.04

# RUN apt-get update && apt-get install -y build-essential

RUN apt update

# 依存関係の修復をしないとpythonが入らない
RUN apt --fix-broken install

RUN apt install -y vim
RUN apt install sudo
RUN apt install -y python3

COPY ./arm-compiler/arm-compiler-for-linux_24.10.1_Ubuntu-22.04_aarch64.tar /home
COPY ./arm-compiler/atfl-experimental-linux-aarch64.tar.gz /home

WORKDIR /home

RUN tar xvf arm-compiler-for-linux_24.10.1_Ubuntu-22.04_aarch64.tar
WORKDIR /home/arm-compiler-for-linux_24.10.1_Ubuntu-22.04
RUN ./arm-compiler-for-linux_24.10.1_Ubuntu-22.04.sh -a
RUN export PATH=/opt/arm/arm-linux-compiler-24.10.1_Ubuntu-22.04/bin:$PATH

RUN tar xzvf atfl-experimental-linux-aarch64.tar.gz

# ユーザー builder をホームディレクトリ付きで追加
RUN useradd -m -s /bin/bash builder
RUN echo 'builder:builder' | chpasswd
RUN usermod -aG sudo builder

# 必要に応じて、以降の処理を builder ユーザーで実行する場合
USER builder
WORKDIR /home/builder
RUN mkdir develop

# sudo passwd builder
```


# arm compiler

https://developer.arm.com/Tools%20and%20Software/Arm%20Compiler%20for%20Linux#Downloads


# cross compiler
## QEMU エミュレータ

```
sudo docker run --privileged --rm tonistiigi/binfmt --install all
```

## arm64 image build
```
sudo docker buildx build --platform linux/arm64 -t ubuntu_2204:arm64 .
```

## container run
```
sudo docker container run --platform linux/arm64 --name ubuntu_2204 --rm --interactive --tty ubuntu_2204:arm64
```