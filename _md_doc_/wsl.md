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

## 仮想マシン プラットフォーム

有効化
```
dism /Online /Enable-Feature /FeatureName:VirtualMachinePlatform /ALL /norestart
```

無効化
```
Dism.exe /Online /Disable-Feature /featurename:VirtualMachinePlatform
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


