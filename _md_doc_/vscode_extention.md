# vscode extention

## サンプルコード
https://github.com/vscode-textbook/extensions


## npm のアップデート
`npm install -g npm`

## 拡張機能ひな形作成
`yo code`

### VSCode拡張機能の構成管理ファイル

package.json

拡張機能がロードされるイベントを定義

```json
	"activationEvents": [
		"onCommand:extension.helloWorld"
	],
```

拡張したい機能をコントリビューションポイントに登録

```json
	"contributes": {
		"commands": [
			{
				"command": "extension.helloWorld",
				"title": "Hello World"
			}
		]
	},
```

コマンドパレット表示条件指定

```json
	"contributes": {
		"menus": {
			"commandPalette": [
				{
					"command": "extension.helloWorld",
					"when": "editorLangId == tyhpescript"
				}
			]
		}
```

キーバインド

```json
	"contributes": {
		"keybindings": [
			{
				"command": "extension.helloWorld",
				"key": "ctrl+shift+h",
				"mac": "cmd+shift+h",
				"when": "editorTextFocus"
			}
		]
```

### 拡張機能の実行

拡張機能のルートフォルダでvscode起動

`code .`

実行　F5

### コマンドの追加

package.json

コントリビューションポイントを追加

```json
	"contributes": {
		"commands": [
```

アクティベーションイベントを追加
```json
	"activationEvents": [
```

src/extention.ts

コマンドの登録

```json
vscode.commands.registerCommand(
	'コマンド名　extension.xxxxx',
	処理
)
```

### 拡張機能のインストール

1. Extensionsフォルダにインストール
.vscode/extensions に以下を置く

2. パッケージ(.vsix)のインストール
3. Marketplaceからのインストール


### テスト

実行
Extention Tests

コマンドラインでは以下 vscodeを終了させておく必要あり
npm run test

実行されるコマンドは以下に記載されている
package.json
	"scripts": {

テストの起点となるスクリプト
runTest.js
runTest.ts をコンパイルして生成される


テストの追加
以下にテストコードを追加する
./src/test/suite


## 構成要素

### アクティベーション

アクティベーションイベントの種類
https://code.visualstudio.com/api/references/activation-events


### コントリビューションポイント

### VS Code API

https://github.com/microsoft/vscode/blob/master/src/vs/vscode.d.ts

### 言語サーバー

https://docs.microsoft.com/ja-jp/visualstudio/extensibility/language-server-protocol?view=vs-2019


## 機能実装方法

### ユーザー設定

package.json

contributes に configuration を追加
データは永続化される
vscode の 設定メニュー 拡張機能 からも設定可能

```json
  "contributes": {

    "configuration": {
      "title": "Sample Configuration",
      "type": "object",
      "properties": {
        "sampleconfig.stringitem": {
          "type": "string",
          "default": "hello",
          "description": "Sample String Item"
        },
        "sampleconfig.numberitem": {
          "type": "number",
          "default": "10",
          "description": "Sample Number Item"
        },
        "sampleconfig.booleanitem": {
          "type": "boolean",
          "default": false,
          "description": "Sample Boolean Item"
        }
      }
    }
```



## 設定データの永続化方法

1. Memento API を利用した Key-Value 型データの保存
https://code.visualstudio.com/api/references/vscode-api#Memento

参照
```TypeScript
		let val =  context.workspaceState.get(COUNTER_KEY, 0);  // default 0
```
更新
```TypeScript
		context.workspaceState.update(COUNTER_KEY, counter);
```

2. カスタムのオブジェクトファイルを専用ストレージパスに保存

テキストやバイナリなどの形式で保存する
以下でパス取得ができるのでデータを保存する

ストレージパス参照
```TypeScript
		console.log(`Workspace Storage Path: ${context.storagePath}`);
		console.log(`Global Storage Path: ${context.globalStoragePath}`);
```

## VSIXパッケージの作成

準備
vsceのinstallは以下で行う
`npm install -g vsce`

package.json

publisher の設定が必要

```json
{
    "name": "markdown-snippet",
    "displayName": "markdown-snippet",
    "publisher": "yokawasa",
```

README.md の記載が必要

記載例
```markdown
# 拡張機能サンプル: Markdown スニペット (Markdown Code Snippet)
```

以下のコマンドで作成する 上記準備を行っていないとエラーとなる

`vsce package`

## VSIXパッケージのインストール

拡張機能表示
コマンドドロップダウン VSIXからインストール

コマンドラインは以下 うまくいかない？
`code --install-extension xxxxxx.vsix`

