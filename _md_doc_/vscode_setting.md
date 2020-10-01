## ソースコード整形

キーボードショートカット
選択範囲のフォーマット

## Markdown

改行で改行する

本来はスペース２つで改行となる

以下に設定することで通常の改行で改行される

```json
    markdown.preview.breaks: true
```

## Snippets

https://github.com/microsoft/vscode/blob/1.43.0/extensions/markdown-basics/snippets/markdown.json

Markdown コード補完 有効化

setting.json

1 入力補完を有効
        "editor.quickSuggestions": true,
2 単語ベースの候補(ドキュメント内の単語に基づく候補)を無効
        "editor.wordBasedSuggestions": false,
3 スニペットと単語ベースの候補をを出すが、スニペットが常に先頭になるようにする
        "editor.snippetSuggestions": "top"

```json
    "[markdown]": {
        "editor.wordWrap": "on",
        "editor.quickSuggestions": true,
        "editor.wordBasedSuggestions": false,
        "editor.snippetSuggestions": "top"
    },
    "markdown.preview.breaks": true,
```
