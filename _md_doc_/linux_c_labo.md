# build-tool インストール

```
sudo apt install build-essential
```


# gdb インストール

```
sudo apt install gdb
```

## 出力先制限解除

```
ulimit -c unlimited
```

## core出力先変更
```
echo 'core.%e.%p' | sudo tee /proc/sys/kernel/core_pattern
```