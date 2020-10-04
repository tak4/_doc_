# Chrome Extention

## Official Site
https://developer.chrome.com/extensions

## Manifest File
https://developer.chrome.com/extensions/manifest

## Sample Extensions
https://developer.chrome.com/extensions/samples

### Sample Extensions Memo

* コンテキストメニュー追加  
Context Menus Sample  
Context Menus Sample (with Event Page)  

* コンテキストメニュー追加 テキスト選択時に表示  
Global Google Search  

```javascript
    chrome.contextMenus.create({
      id: locale.id,
      title: locale.title,
      type: 'normal',
      contexts: ['selection'],
    });
```
* 新しいタブを開く  
Cookie API Test Extension  

* ショートカットキー  
Tab Flipper  

* リンク先ダウンロード  
Download Selected Links  

## Background Page / Event Page / Content Page

全てJavaScript

* Background Page  
Chrome起動中は常駐する  

以下のように指定する
manifest.json
```javascript
  "background": {
    "scripts": [
      "js/background.js"
    ],
    "persistent": true
  }
```

* Event Page  
イベント発生時のみ起動する
元は Background Page しかなかったが、常駐を避けたい為、追加された。

以下のように指定する
manifest.json
```javascript
  "background": {
    "scripts": [
      "js/background.js"
    ],
    "persistent": false
  }
```

* Content Page  
表示しているページに差し込まれる
対象ページはフィルタ可能  
chrome.runtime や chrome.storage は使用可能だが、
chrome.tabs や chrome.browserAction は使用不可

以下のように指定する
manifest.json
```javascript
  "content_scripts": [
    {
      "matches": ["<all_urls>"],
      "js": ["content.js"]
    }
  ]
```
