# Null-modem emulator(com0com)
https://com0com.sourceforge.net/

# minicom ubuntu install
https://help.ubuntu.com/community/Minicom

# ubuntu serial port check
ls -la /dev/ttyS*

# minicom connect
sudo minicom -D /dev/ttyS1

# tcu_muxer
https://developer.nvidia.com/docs/drive/drive-os/6.0.7/public/drive-os-linux-sdk/common/topics/util_setup/TegraCombinedUARTandthetcu_muxerUtility1.html

Tegra Combined UART 
muxer 複数の信号を一つにまとめる装置やソフトウェア

tcu_muxerの概要と役割
tcu_muxerは、NVIDIAの自動車向けプラットフォーム「DRIVE OS」環境で利用されるユーティリティであり、主にデバッグ情報の取り扱いを効率化するために設計されています。

仕組みと動作原理
NVIDIAのSoC（System on Chip）には複数のプロセッサ（例：CCPLEX、R5、SPEなど）が搭載されており、それぞれがデバッグ情報やログを出力します。

Tegra Combined UART（TCU）は、これら複数プロセッサからのデバッグ情報を一つの物理UART（シリアル通信）経由でまとめて出力（多重化）します。

tcu_muxerはホストPC上で動作し、この多重化されたデータを受け取り、各プロセッサごとの情報に分離（デマルチプレクス）します。

主な用途
各プロセッサ（例：RCE、BPMP、SCE、SPE、TZ、CCPLEXなど）ごとに仮想端末（pseudo terminal）を作成し、個別にシェルアクセスやデバッグログの取得が可能になります。

仮想化環境では、CCPLEXクラスタ内の各VM（仮想マシン）ごとにコンソールを分離し、個別のデバッグ情報を取得できます。

```
tcu_muxer -g 17 -b 16 -d /dev/ttyUSB1
```

# cu
sudo apt update
sudo apt install cu

cu -l /dev/ttyS5 -s 9600

