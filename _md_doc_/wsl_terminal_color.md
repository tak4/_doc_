# WSLターミナル文字色

## ファイルやディレクトリの文字色

### dircolors による設定

.dircolorsファイルは、Linuxのlsコマンドなどでファイルやディレクトリを色分け表示するための設定ファイル

主にホームディレクトリ（~/.dircolors）に配置し、ユーザーごとにカスタマイズ可能

色は、属性値：カラーコード であらわす

[Man page of DIR_COLORS](https://linuxjm.sourceforge.io/html/LDP_man-pages/man5/dir_colors.5.html)

ホームディレクトリで現在の設定を出力する

```bash
dircolors -p > ~/.dircolors
```

上記ファイルを編集し、以下のコマンドにて設定した色が反映される。

```bash
eval $(dircolors -b ~/.dircolors)
```

上記の意味は以下

背景色を含めて環境変数(LS_COLORS)の値を出力する

```bash
dircolors -b
```

背景色を含めて~/.dircolorsの設定内容を出力する

```bash
dircolors -b ~/.dircolors
```

$()は、コマンド置換

コマンドの出力を別のコマンドの引数として渡す

eval は渡された内容をシェルスクリプトとして実行する

```bash
eval $(dircolors -b ~/.dircolors)
```

## プロンプトの文字色

### ~/.bachrc を編集して、環境変数 PS1に設定する

```bash
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;36m\]\w\[\033[00m\]\$ '
```