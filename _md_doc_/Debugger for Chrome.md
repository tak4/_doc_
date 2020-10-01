# Debugger for Chrome

## インストール
https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome

## 設定
vscode 実行 タブ
タスク構成

    "configurations": [
        {
            "name": "Attach to Chrome",
            "port": 9222,
            "request": "attach",
            "type": "pwa-chrome",
            "webRoot": "${workspaceFolder}"
        },
        {
            "name": "Launch Chrome",
            "request": "launch",
            "type": "pwa-chrome",
            "url": "XXXXXX", 
            "webRoot": "${workspaceFolder}"
        },
    ]

Chrome設定

起動オプションに以下を付ける

--remote-debugging-port=9222

参考
https://kakkoyakakko2.hatenablog.com/entry/2018/06/13/003000


