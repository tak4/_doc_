# Node.js

## インストール
https://nodejs.org/ja/

## バージョン確認
```
node --version
```

## スレッドモデル／イベントループ方式

スレッドモデル
リクエストごとにスレッドを起動する
Apache 等が採用

イベントループ
リクエストはQueueに溜められる
溜められたリクエストは、Queueからリクエストを取り出すスレッド(A)から取り出され、
処理を行うスレッド(B)に渡される。
(A)は(B)から結果を受け取る

Node.jsではイベントループ形式を採用

## npm

node package modules
https://www.npmjs.com/

node.js のパッケージマネージャ



## パッケージインストール

ユーザー別(フォルダ)インストール
npm install [package name]

実行したフォルダに以下のフォルダが作成されてその中にインストールされる
node_modules

実行したフォルダの上位フォルダに上記のフォルダがある場合は、
そのフォルダにインストールされるらしい

システムへインストール
npm install -g [package name]

## node.js + Chrome Extension

https://qiita.com/abcang/items/10750e3fb8453d5e0944

## PDF Parse

http://dotnsf.blog.jp/archives/1075957643.html


https://www.npmjs.com/package/pdf-parse

install 
npm install pdf-parse

