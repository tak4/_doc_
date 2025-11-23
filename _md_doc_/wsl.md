# WSL

## Linux用 Windows サブシステム

コントロールパネル＞プログラムと機能＞Windowsの機能の有効化または無効化
Linux用 Windows サブシステム　を有効化
```
dism /Online /Enable-Feature /featurename:Microsoft-Windows-Subsystem-Linux /norestart
```

Linux用 Windows サブシステム　を無効化
```
dism /Online /Disable-Feature /featurename:Microsoft-Windows-Subsystem-Linux
```

Windowsの再起動が必要

## Virtual Machine Platform

有効化
```
dism /Online /Enable-Feature /FeatureName:VirtualMachinePlatform /ALL /norestart
```

無効化
```
Dism.exe /Online /Disable-Feature /featurename:VirtualMachinePlatform
```

Windowsの再起動が必要

## Hyper-V

WSLを利用するだけなら不要だが、WSLの仮想イメージを圧縮 Optimize-VHD する為に必要

```
dism /Online /Enable-Feature /FeatureName:Microsoft-Hyper-V-All /norestart
```

Windowsの再起動が必要


### VHDXという仮想ハードディスクファイルを最適化（圧縮）

ext4.vhdx の格納場所を確認する

```
(Get-ChildItem "$env:LOCALAPPDATA\Packages" -Recurse -Filter "ext4.vhdx").FullName
```

 $env:LOCALAPPDATA\Packages
環境変数 LOCALAPPDATA（通常は C:\Users\<ユーザー名>\AppData\Local）を展開したパスに、Packages を付けた場所を指
指定ディレクトリ以下を再帰的に走査し（-Recurse）、名前が ext4.vhdx のファイルだけを列挙します。

```
(Get-ChildItem "$env:LOCALAPPDATA\Packages" -Recurse -Filter "ext4.vhdx" | Select-Object -First 1).FullName
```
Select-Object -First 1
を行うことで、複数の FileInfo のうち、最初の 1 件だけを取り出す。

```
Optimize-VHD -Path [ext4.vhdxへのパス] -Mode Full
```

## デフォルトをWSL2に設定

```
wsl --set-default-version 2
```

デフォルトバージョンを確認する
```
wsl --status
```


## install

https://learn.microsoft.com/ja-jp/windows/wsl/install

Ubuntu-22.04 をインストール
```
wsl --install -d Ubuntu-22.04 
```

インストール可能なディストリビューションの確認
```
wsl --list --online
```

ディストリビューション削除
```
wsl --unregister Ubuntu-22.04
```


