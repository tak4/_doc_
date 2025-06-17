# arm linker --info-topic
https://developer.arm.com/documentation/100070/0609/linker-command-line-options/--info-topic--topic---?lang=en


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
RUN apt-get install -y vim
RUN apt-get install sudo

COPY ./arm-compiler/arm-compiler-for-linux_24.10.1_Ubuntu-22.04_aarch64.tar /home
WORKDIR /home
RUN tar xvf arm-compiler-for-linux_24.10.1_Ubuntu-22.04_aarch64.tar

# ユーザー builder をホームディレクトリ付きで追加
RUN useradd -m -s /bin/bash builder
RUN echo 'builder:builder' | chpasswd
RUN usermod -aG sudo builder

# 必要に応じて、以降の処理を builder ユーザーで実行する場合
USER builder
WORKDIR /home/builder
RUN mkdir arm-compiler

# sudo passwd builder

```

image build
```
sudo docker image build --tag ubuntu_2204:build-essential --file ./Dockerfile .
```

container run
```
sudo docker container run --name ubuntu_22_04 --rm --interactive --tty ubuntu_2204:build-essential bash
```


# arm compiler

https://developer.arm.com/Tools%20and%20Software/Arm%20Compiler%20for%20Linux#Downloads



