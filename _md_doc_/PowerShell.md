# PowerShell

## ダウンロード
https://github.com/PowerShell/PowerShell#get-powershell

## バージョン確認
```
PS D:\develop\vbs\ipaddr>> $PSVersionTable
Name                           Value
----                           -----
PSVersion                      5.1.18362.752
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.18362.752
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Get-Module -FullyQualifiedName @{ModuleName="WebApplicationProxy"}  

## VSCode Extension

PowserShell  
https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell

PowerShell Integrated Console  
を管理者権限で実行するには、VSCodeを管理者権限で起動する必要がる

## ShortCut

管理者権限 PowerShell起動  
Win + X -> A

## Help

```ps1
Get-Help
Get-Help Get-NetAdapter
```

## Echo

echo は Write-Output のエイリアス  
```ps1
Write-Output '* ネットワークアダプタの一覧';
```

## ネットワークアダプタ取得

```ps1
Get-NetAdapter

# テーブル出力
Get-NetAdapter|Format-Table;

# リスト出力
Get-NetAdapter|Format-List;

# 名前指定
Get-NetAdapter -Name "Wi-Fi"

# Statusのみ取得
Get-NetAdapter -Name "Wi-Fi" | Select-Object -Property Status

# Wi-Fiという名前のネットワークアダプタを取得
Get-NetAdapter -Name "Wi-Fi"

# Wi-Fiという名前のネットワークアダプタを取得＋IpV4 に限定
Get-NetAdapter -Name "Wi-Fi" | Get-NetIpAddress -ADdressFamily IpV4 | Select-Object -Property IPAddress

# Wi-Fiという名前のネットワークアダプタを取得＋IpV4 に限定＋IPAdressとInterfaceAliasのみ選択取得
Get-NetAdapter -Name "Wi-Fi" | Get-NetIpAddress -ADdressFamily IpV4 | Select-Object -Property IPAddress,InterfaceAlias
```

## ルーティングテーブル

```ps1
# ルーティングテーブル出力
Get-NetRoute
Get-NetRoute -ADdressFamily IpV4
```

## DNSサーバー設定取得

Get-DnsClientServerAddress -InterfaceAlias "Wi-Fi"


## 5秒Sleep
```ps1
Start-Sleep 5
```

### DHCP有効化／無効化
```ps1
Set-NetIPInterface -InterfaceAlias "Wi-Fi" -AddressFamily IPv4 -Dhcp Enabled
Set-NetIPInterface -InterfaceAlias "Wi-Fi" -AddressFamily IPv4 -Dhcp Disabled
```

### IPv4 IPアドレスとネットマスクを削除
```ps1
Remove-NetIPAddress -InterfaceAlias "Wi-Fi" -AddressFamily IPv4
```
### デフォルトゲートウェイを削除
```ps1
Remove-NetRoute -InterfaceAlias "Wi-Fi" -AddressFamily IPv4
```
### DNSサーバー IPアドレスを削除
```ps1
Set-DnsClientServerAddress -InterfaceAlias "Wi-Fi" -ResetServerAddresses
```

### IPv4 IPアドレス／ネットマスク／デフォルトゲートウェイを設定
```ps1
New-NetIPAddress -InterfaceAlias "Wi-Fi" -AddressFamily IPv4 -IPAddress "192.168.1.2" -PrefixLength 24 -DefaultGateway "192.168.1.1"
```

### DNSサーバー IPアドレスを設定
```ps1
Set-DnsClientServerAddress -InterfaceAlias "Wi-Fi" -ServerAddress "192.168.1.1"
Set-DnsClientServerAddress -InterfaceAlias "Wi-Fi" -ServerAddress ("192.168.1.1","192.168.1.111")
```

## 実行ポリシー

```bash
Get-ExecutionPolicy
```

AllSigned（署名付きスクリプトのみ実行可）  
Bypass（検査迂回）  
RemoteSigned（ローカルスクリプトと署名付きのリモートスクリプトのみ実行可） 
Restricted（全て実行不可）  
Undefined（未定義）  
Unrestricted（全て実行可）  

以下でスクリプト実行可能となる。※変更には管理者権限必要

```bash
Set-ExecutionPolicy RemoteSigned
Set-ExecutionPolicy Bypass
Set-ExecutionPolicy Unrestricted
```

一時的に権限指定して実行する方法

```bash
powershell -ExecutionPolicy RemoteSigned -File .\for_all_files.ps1
```

## WebDAVサーバからのダウンロード
```
# ユーザー名とパスワードを入力
$cred = Get-Credential

# BASIC認証付きでアクセス
Invoke-WebRequest -Uri "https://example.com/protected/file.zip" -Credential $cred -OutFile "file.zip"
```

```
# ユーザー名とパスワードを直接指定
$username = "user"
$password = "pass"

# Base64エンコード
$pair = "$username`:$password"
$bytes = [System.Text.Encoding]::ASCII.GetBytes($pair)
$encoded = [Convert]::ToBase64String($bytes)

# ヘッダー付与してリクエスト
Invoke-WebRequest -Uri "https://example.com/protected/file.zip" `
  -Headers @{ Authorization = "Basic $encoded" } `
  -OutFile "file.zip"
```

## WebDAVサーバへのアップロード

```
# アップロードするローカルファイルのパス
$file = "C:\Users\User\Documents\report.pdf"

# WebDAVサーバのURL（アップロード先ディレクトリ）
$url = "https://example.com/webdav"

# 認証情報
$user = "username"
$pass = "password"

# ファイル名をURLに追加
$uploadUrl = "$url/" + (Split-Path $file -Leaf)

# ファイル内容をバイナリで読み込み
$stream = New-Object -ComObject ADODB.Stream
$stream.Type = 1 # バイナリモード
$stream.Open()
$stream.LoadFromFile($file)
$buffer = $stream.Read()

# HTTP PUTリクエストを作成
$http = New-Object -ComObject MSXML2.ServerXMLHTTP
$http.Open("PUT", $uploadUrl, $false, $user, $pass)
$http.Send($buffer)

# 結果確認
if ($http.status -eq 201 -or $http.status -eq 204) {
    Write-Host "Upload successful: $uploadUrl"
} else {
    Write-Host "Upload failed. Status: $($http.status) $($http.statusText)"
}
```

```
Invoke-WebRequest -Uri "https://example.com/webdav/report.pdf" `
  -Credential (Get-Credential) `
  -Method Put `
  -InFile "C:\Users\User\Documents\report.pdf"
```