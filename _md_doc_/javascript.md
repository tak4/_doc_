# JavaScript

## ドキュメント

JavaScript Primer
https://jsprimer.net/

JavaScript Promiseの本
https://azu.github.io/promises-book/

## スクリプトタグの位置

HTML bodyタグの最後に書く
HTML要素を読み込んでから出ないと要素(<body>等)に対するDOM操作などができない
よって、headタグの中にて、
document.body.textContent
とやるとbodyが無いので、エラーとなる

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="utf-8">
  <title>JavaScript Basics</title>
</head>
<body>

  <script>
    document.body.textContent = "Hello World";
  </script>
</body>
</html>
```

## モジュール

type="module"
とすることで、名前空間が分離され、const変数が重複しない
また、moduleとすることで、読み込みが遅延する為、headタグ内に書いてもOK
全てのhtml要素が読み込まれた後にmoduleが読み込まれる

```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <meta charset="utf-8" />
    <title>JavaScript Basics</title>
  </head>
  <body>
    <script type="module">
      const text = "Hello World";
    </script>
    <script type="module">
      const text = "Hello World Hello";
      document.body.textContent = text;
    </script>
  </body>
</html>
```

## モジュール export / import

別のモジュールでexportしたものをimportする

./index.html
```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <meta charset="utf-8" />
    <title>JavaScript Basics</title>
  </head>
  <body>
    <script type="module" src="./index.js"></script>
    <script type="module" src="./index2.js"></script>
  </body>
</html>
```

./index.js
```javascript
export const helloText = "Hello World";
```

./index2.js
```javascript
import { helloText } from "./index.js";

document.body.textContent = helloText;
```


## 即時関数

関数を定義すると同時に実行するための構文
スコープ定義として用いられる

```javascript
(function () {
    //処理
}());
```


## React

公式サイト
https://ja.reactjs.org/

Chrome 拡張
React Developer Tools

ローカルのファイルでデバッグするには、「管理」から以下を有効にする必要がある
ファイルの URL へのアクセスを許可する



