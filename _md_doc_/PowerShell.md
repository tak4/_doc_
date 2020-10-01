# PowerShell

## ダウンロード
https://github.com/PowerShell/PowerShell#get-powershell

## バージョン確認

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

Start-Sleep 5




### DHCP有効化／無効化
Set-NetIPInterface -InterfaceAlias "Wi-Fi" -AddressFamily IPv4 -Dhcp Enabled
Set-NetIPInterface -InterfaceAlias "Wi-Fi" -AddressFamily IPv4 -Dhcp Disabled

### IPv4 IPアドレスとネットマスクを削除
Remove-NetIPAddress -InterfaceAlias "Wi-Fi" -AddressFamily IPv4
### デフォルトゲートウェイを削除
Remove-NetRoute -InterfaceAlias "Wi-Fi" -AddressFamily IPv4
### DNSサーバー IPアドレスを削除
Set-DnsClientServerAddress -InterfaceAlias "Wi-Fi" -ResetServerAddresses

### IPv4 IPアドレス／ネットマスク／デフォルトゲートウェイを設定
New-NetIPAddress -InterfaceAlias "Wi-Fi" -AddressFamily IPv4 -IPAddress "192.168.1.2" -PrefixLength 24 -DefaultGateway "192.168.1.1"
### DNSサーバー IPアドレスを設定
Set-DnsClientServerAddress -InterfaceAlias "Wi-Fi" -ServerAddress "192.168.1.1"
Set-DnsClientServerAddress -InterfaceAlias "Wi-Fi" -ServerAddress ("192.168.1.1","192.168.1.111")


