# マイコン

[Renesas Engineer School | Renesas](https://www.renesas.com/jp/ja/support/engineer-school)

[GPIO | Renesas](https://www.renesas.com/jp/ja/support/engineer-school/mcu-programming-peripherals-01-gpio)

## シリアル通信

[シリアル通信 | Renesas](https://www.renesas.com/jp/ja/support/engineer-school/mcu-programming-peripherals-03-serial-communication)

## 非同期式／同期式

### USART

**Universal Synchronous Asynchronous Receiver Transmitter**

ユーエスアート

USART (Universal Synchronous/Asynchronous Receiver/Transmitter)は、シリアル通信に使用されるハードウェアデバイスであり、通常はマイクロコントローラなどのデジタル回路に搭載されています。USARTは、非同期通信と同期通信の両方をサポートし、UARTよりも高度な機能を備えています。

USARTは、データを同期させるために外部クロックを使用できます。また、通信速度の高速化、エラーチェック、フロー制御、マルチプロセッサ通信などの機能をサポートしています。USARTは、通常、3本以上の信号線を使用して、データの送受信に必要な情報を転送します。

USARTには、通常、以下の信号線が含まれます。

1. RX (Receiver)：データを受信するために使用される線です。
2. TX (Transmitter)：データを送信するために使用される線です。
3. RTS (Ready To Send)：送信準備が完了したことを通知するための線です。
4. CTS (Clear To Send)：データを送信してもよいことを通知するための線です。
5. CLK (Clock)：外部クロックを提供するための線です。

USARTは、通常、高速通信やエラーチェックなど、より高度なシリアル通信が必要な場合に使用されます。USARTは、コンピュータや周辺機器、通信機器、センサーなどのデバイスとの通信に使用されます。USARTの使用は、UARTよりも複雑であるため、より高度なシリアル通信を必要とする場合に使用されます。

## 非同期式

### UART

Universal Asynchronous Receiver/Transmitter

ユーアート

調歩同期式

全二重通信／半二重通信

UART (Universal Asynchronous Receiver-Transmitter)は、シリアル通信に使用されるハードウェアデバイスであり、通常はマイクロコントローラなどのデジタル回路に搭載されています。UARTは、データの送信と受信を処理することができます。

UARTは、データを同期せずに転送する非同期シリアル通信をサポートしています。この方式では、データの送信側と受信側のクロックが同期されていなくても、データを正常に送受信できます。UARTは、通常、2本の信号線を使用して、データの送受信に必要な情報を転送します。

UARTには、通常、以下の信号線が含まれます。

1. RX (Receiver)：データを受信するために使用される線です。
2. TX (Transmitter)：データを送信するために使用される線です。
3. RTS (Ready To Send)：送信準備が完了したことを通知するための線です。
4. CTS (Clear To Send)：データを送信してもよいことを通知するための線です。

UARTは、非常に一般的な通信プロトコルであり、シリアル通信に使用されます。多くのマイクロコントローラにはUARTが搭載されており、コンピュータや周辺機器、通信機器、センサーなどのデバイスとの通信に使用されます。また、UARTは、通信速度やデータのビット数などのパラメータを設定できるため、様々な用途に対応することができます。

## 同期式

### I2C

Inter-Integrated Circuit

アイ・スクエアード・シー

2C (Inter-Integrated Circuit)は、簡単な2本の信号線を使用して、マイクロコントローラや周辺デバイス間の通信を行うシリアル通信規格の1つです。

I2Cには、通常2本の信号線が含まれます。

1. SDA (Serial Data Line)：データの送受信に使用されます。
2. SCL (Serial Clock Line)：データの同期に使用されます。

I2Cは、マスターデバイスがデータの送信を開始すると、スレーブデバイスがデータを受信するための準備をします。マスターがクロック信号を送信すると、スレーブがSDA線からデータを読み取り、同時に自身のデータをSDA線に送信します。このようにして、データの送信と受信が同期して行われます。通信が終了すると、マスターがSDA信号線を高い電圧に戻し、スレーブは通信終了を検出します。

I2Cは、SPIよりも低速な通信を提供しますが、通信に必要な信号線の本数が少なく、複数のデバイスを接続することができます。また、I2Cには各デバイスに固有のアドレスがあり、複数のデバイスを同じバスに接続しても、それらを個別に識別することができます。

I2Cは、小さなデータ転送に適しており、センサーやディスプレイ、EEPROMなどのデバイスに広く使用されています。また、I2Cは、簡単にマイクロコントローラと周辺デバイスを接続できるため、プロトタイピングや実験に最適です。

### SPI

Serial Peripheral Interface

エス・ピー・アイ

MOSI, MISO, SCLK, CS の4つの信号線による通信規格

SPI (Serial Peripheral Interface) は、マイクロコントローラや周辺デバイス間の通信に広く使用されるシリアル通信規格の1つです。SPIは、簡単で高速なデバイス間の通信に最適な方法であり、単方向または双方向の通信に使用されます。

SPIには、通常4本の信号線が含まれます。

1. MOSI (Master Output Slave Input)：マスターからスレーブへのデータ送信用の信号線です。
2. MISO (Master Input Slave Output)：スレーブからマスターへのデータ送信用の信号線です。
3. SCK (Serial Clock)：マスターからのクロック信号で、データの送受信を同期するために使用されます。
4. SS (Slave Select)：スレーブデバイスの選択用の信号線です。

SPIでは、マスターデバイスがデータの送信を開始すると、スレーブデバイスがデータを受信するための準備をします。マスターがクロック信号を送信すると、スレーブがMOSI線からデータを読み取り、同時に自身のデータをMISO線に送信します。このようにして、データの送信と受信が同期して行われます。通信が終了すると、マスターはSS信号線を高い電圧に戻し、スレーブは通信終了を検出します。

SPIは、高速かつ堅牢な通信を提供し、多くのマイクロコントローラと周辺デバイスに実装されています。また、SPIは、各デバイスに固有の制御信号線を持っているため、同じバス上に複数のデバイスを接続することができます。これにより、SPIを使用して複数のデバイスを制御することができます。

### CAN

CAN (Controller Area Network)は、車載ネットワークや産業用制御システムなどの分野で広く使用される、シリアル通信の規格の一つです。CANは、マルチマスター・マルチスレーブの分散型ネットワークトポロジーで構成されており、最大1Mbpsのデータレートで通信することができます。

CANは、2本の信号線(CAN_High, CAN_Low)を使用して、データの送受信を行います。この2本の線は、差動信号であり、ノイズや干渉からデータを保護するために使用されます。CANは、フレームと呼ばれるパケット形式でデータを送受信します。フレームには、ID、データ、コントロールビット、CRCなどの情報が含まれています。

CANの特徴として、以下が挙げられます。

1. フォールトトレラント性：CANは、多重化されたエラー検出機能を備えており、誤りの発生や伝搬を検出することができます。これにより、ノイズや信号の干渉に耐性があり、高い信頼性を持つことができます。
2. リアルタイム性：CANは、高速でリアルタイムなデータ通信が必要なアプリケーションに適しています。CANは、1つのフレームが最大8バイトであるため、通信速度を高速にすることができます。
3. 簡易性：CANは、2本の信号線を使用するため、配線が簡単で、車載ネットワークや産業用制御システムなどの分野でよく使用されています。

CANは、車載ネットワークや産業用制御システムなど、高度な通信が必要な分野で広く使用されています。CANは、マイクロコントローラやデジタル回路に実装することができ、高速・高信頼性のデータ通信を実現することができます。

### SDIO

SDIO (Secure Digital Input Output)は、Secure Digital (SD) カードを用いた拡張機能の一つであり、SDカードのインターフェースにI/O機能を追加することで、様々な周辺機器やセンサーとの接続を可能にします。

SDIOは、SDカードと同じピン配置を使用していますが、SDカードとは異なり、データ転送速度は最大50Mbpsまでサポートしています。また、SDカードと同様に、SDIOカードにはセキュリティ機能が備わっており、SDIOの規格に従ったカードリーダーを使用することで、データの暗号化や著作権保護が可能です。

SDIOは、携帯電話、タブレット、デジタルカメラ、ポータブルゲーム機など、様々な機器で利用されています。例えば、携帯電話では、Wi-FiやBluetooth、NFCなどの通信機能や、GPS、センサー類などがSDIOを介して接続されています。

SDIOは、I/O機能をSDカードに追加することで、携帯性や省電力性などの利点を持ち、様々な周辺機器やセンサーとの接続を可能にするため、モバイルデバイスの拡張性を向上させます。

### MMC

MMC (MultiMediaCard) は、小型のフラッシュメモリーカードの一種で、主に携帯電話、デジタルカメラ、ポータブル音楽プレイヤー、タブレットなどの携帯電子機器で利用されます。

MMCは、SDカードと同様のインターフェースを持ち、ピン数も同じですが、SDカードよりも小型であり、容量も小さいため、主に携帯電話やデジタルカメラなどで利用されています。

MMCは、読み取り速度が比較的速く、データの書き込み速度も高いため、データの保存や転送に適しています。また、SDカードと同様に、MMCにも著作権保護技術が導入されており、デジタル著作物の保護にも役立ちます。

ただし、現在はSDカードの普及により、MMCはあまり使用されていません。また、MMCはSDカードよりもピンの数が少なく、機能も限定的であるため、拡張性に欠けるという欠点もあります。

### SPDIF

SPDIF (Sony/Philips Digital Interface)は、デジタルオーディオ信号を伝送するための規格であり、主にコンシューマー向けのオーディオ機器で使用されています。

SPDIFは、Toslink光ファイバーまたは同軸ケーブルを介してデジタル信号を伝送します。信号は、PCM（パルス符号変調）、Dolby Digital、DTSなどの圧縮音声形式に対応しています。

同軸ケーブルでは、電気信号が中心の銅線を通じて伝送され、アウターシールドによって電気的ノイズから保護されます。一方、Toslink光ファイバーは、光ファイバーを通じて信号を伝送するため、電気的ノイズから完全に隔離されます。

SPDIFは、家庭用AV機器やコンピュータのサウンドカードなど、多くのオーディオ機器で利用されています。SPDIFによって、高品質のデジタルオーディオ信号を伝送することができ、スピーカーシステムやホームシアターシステムなどの音響機器で使用されることが多いです。

### JTAG

JTAG (Joint Test Action Group)は、半導体デバイスのテストや診断、プログラミングなどの目的で使用される標準的なテストアーキテクチャです。

JTAGインタフェースは、特定のピンを介して半導体デバイスにアクセスすることができます。このインタフェースを使用することで、半導体デバイス内部の信号線やレジスタにアクセスし、テストや診断、プログラムの実行が可能になります。

JTAGは、複数の半導体デバイスを同時に接続し、統合された回路全体をテストすることも可能です。また、JTAGには多くの機能が含まれており、半導体デバイスのテストや診断に役立ちます。たとえば、IDコードの読み取り、チェーンの検出、信号のマニピュレーションなどがあります。

JTAGは、マイクロコントローラやFPGA、ASICなど、多くの半導体デバイスで利用されています。また、JTAGインタフェースは、ボードレベルテスト、生産テスト、開発、修正など、幅広い用途で使用されています。

### PCI Express

PCI Express (Peripheral Component Interconnect Express)は、デスクトップコンピューターやサーバーなどのコンピューターシステムで使用される高速シリアルインターフェースです。

PCI Expressは、データ転送にシリアル伝送を使用し、バス幅を拡張し、通信速度を向上させることができます。PCI Expressは、複数のレーンで構成されており、各レーンは個別にデータを転送することができます。これにより、1つのPCI Expressスロットで複数のデバイスを接続し、高速データ転送を実現することができます。

PCI Expressは、高速データ転送が必要なグラフィックカード、ネットワークカード、ストレージデバイスなどの拡張カードに広く使用されています。また、PCI Expressは、高速通信が必要な組み込みシステムやオンボードのデバイスの接続にも使用されます。

PCI Expressには、さまざまな規格があります。主要な規格には、PCI Express 1.0、2.0、3.0、4.0、5.0などがあり、それぞれの規格で通信速度が異なります。最新の規格であるPCI Express 5.0では、1レーンあたり20Gbpsの通信速度を実現することができます。

### FPGA

FPGA（Field Programmable Gate Array）は、デジタル回路を実装するためのプログラマブルな論理デバイスです。FPGAは、ASIC（Application-Specific Integrated Circuit）やプロセッサーなどの標準的なICとは異なり、ユーザーが設計した回路をFPGAにロードすることにより、機能を実現することができます。

FPGAは、ハードウェアの開発において柔軟性と高性能を提供します。FPGAを使用することで、異なる入出力インターフェースを持つ複数のデバイスを接続するためのブリッジや、高速信号処理アルゴリズムを実行するためのデジタル信号処理機能など、多くの異なるアプリケーションを実現することができます。

FPGAは、ハードウェア設計を行うための専用の開発ツールが提供されています。このツールにより、回路の設計、シミュレーション、実装、検証が行えます。FPGAのプログラミング言語には、Verilog HDLやVHDLが一般的に使用されます。

FPGAは、高速な処理が必要なアプリケーションや、リアルタイム処理が必要なアプリケーション、高い信頼性が求められるアプリケーションなどに広く使用されています。FPGAのアプリケーション例には、ビデオ処理、ネットワーク通信、医療機器、産業制御、航空宇宙、自動車などがあります。

### FMC

FMC（Flexible Memory Controller）は、外部メモリの接続をサポートするコントローラであり、主にARM Cortex-Mシリーズのマイクロコントローラに搭載されています。FMCは、SDRAM、NORフラッシュ、NANDフラッシュ、SRAM、PSRAMなどのメモリタイプをサポートしています。

FMCは、メモリアクセスに必要な制御信号を発生させることで、外部メモリとの通信を制御します。FMCは、メモリアクセスを高速化するための機能をサポートしており、例えば、バーストモードやページモードなどの機能を利用することで、メモリアクセスの効率を向上させることができます。

FMCは、SDRAM、NORフラッシュ、NANDフラッシュ、SRAM、PSRAMなどのメモリタイプに対応するコントローラを持っており、それぞれのメモリタイプに合わせたインターフェースを提供します。FMCは、各メモリタイプのアドレス指定、データ転送、タイミングなどを制御するための回路を内蔵しています。

FMCの設定は、各メモリタイプに対して異なるため、適切な設定が必要です。設定には、メモリタイプ、アドレス指定、データ転送速度、タイミング、バーストモード、ページモードなどが含まれます。FMCの設定は、マイコンの内部フラッシュメモリに書き込まれた設定レジスタによって行われます。

FMCは、高速なメモリアクセスが必要なアプリケーションで使用されます。例えば、画像処理、オーディオ処理、データ処理などがあります。FMCを使用することで、高速で効率的なメモリアクセスが可能になります。また、FMCを使用することで、マイコン内蔵のフラッシュメモリやRAMの容量を超える大容量のメモリにアクセスすることもできます。

### EEPROM

EEPROM（Electrically Erasable Programmable Read-Only Memory）は、データを記憶し、電気的に消去・書き換えができる不揮発性のメモリです。EEPROMは、通常、IC（Integrated Circuit）の形態で提供されます。

EEPROMは、ROM（Read-Only Memory）と比較して、プログラマブルであり、データの書き換えが可能です。また、EPROM（Erasable Programmable Read-Only Memory）と比較して、電気的に消去・書き換えができるため、繰り返し使用することができます。EEPROMは、ROMとEPROMの良いところを合わせたものと言えます。

EEPROMは、電源を切ってもデータが保持されるため、不揮発性メモリとして使われます。また、EEPROMには、一般的に多数のアドレスがあり、1バイト単位でデータを書き込むことができます。データの読み出しには、シリアル通信や並列通信などのインタフェースが使用されます。

EEPROMは、携帯電話、デジタルカメラ、音声機器、車載エレクトロニクス、センサーデータの格納など、様々なアプリケーションに使用されます。また、マイクロコントローラなどのシステムでも、EEPROMを使用して設定データやユーザーデータを保存することができます。

### Ethernet PHY

Ethernet PHYは、Ethernet Physical Layer Transceiver（イーサネット物理層トランシーバ）の略称で、Ethernet接続を実現するための物理層の回路を指します。Ethernetは、LAN（Local Area Network）を実現するための標準的な通信プロトコルであり、Ethernet PHYはこのプロトコルを物理的に実現するための回路です。

Ethernet PHYは、Ethernetデータを物理信号に変換するための回路であり、ネットワークケーブルとコンピューターの間でデータを送受信するための役割を担います。具体的には、Ethernet PHYは、送信データを電気信号に変換し、ネットワークケーブルを介して送信します。また、受信データを電気信号からEthernetデータに変換し、コンピューターに送信する役割も担います。

Ethernet PHYは、イーサネットの標準規格であるIEEE 802.3に準拠した回路として実装されます。Ethernet PHYは、10BASE-T、100BASE-TX、1000BASE-Tなど、異なるイーサネット規格に対応するために異なる回路が用意されています。Ethernet PHYは、通常、マイクロコントローラー（MCU）やプロセッサーに接続され、ネットワーク接続を実現するためのネットワークインターフェースとして機能します。

Ethernet PHYは、ネットワーク接続の品質に大きな影響を与えるため、高速で信頼性の高いデータ転送を実現するためには、高品質なEthernet PHYを使用することが重要です。Ethernet PHYは、ネットワークインターフェースチップなどに内蔵されている場合が多く、多くのネットワーク機器に広く使用されています。

### IOE

IOE（Input/Output Expander）は、マイクロコントローラーなどのマイコンボードで使用される入出力拡張チップのことを指します。IOEを使用することで、マイコンボードのピン数が足りなくなった場合に、追加の入出力ピンを提供することができます。

IOEには、I2CやSPIなどのシリアル通信インタフェースを使用して制御するものが一般的です。これらの通信インタフェースを通じて、IOEが提供する各ピンの入出力状態を制御することができます。

IOEには、TIのPCF8574やMicrochipのMCP23017などが代表的な製品です。これらの製品は、8ビットまたは16ビットの入出力拡張を提供し、I2Cインタフェースを介して制御されます。

IOEは、マイコンボードに接続される様々なデバイスの制御に使用されます。例えば、LED、スイッチ、LCD、7セグメントディスプレイ、モーターなどが挙げられます。IOEを使用することで、これらのデバイスをマイコンボードに直接接続することができ、ハードウェアの設計が簡素化されます。

### PWM

PWM (Pulse Width Modulation) は、デジタル信号をアナログ信号に変換するための一種の技術です。 PWMは、信号のON時間（パルス幅）を調整することで、平均的な電圧または電流を制御します。このため、PWMは、電気的なエネルギーの効率的な制御に広く使用されています。

PWM信号は、定期的に繰り返されるパルス信号です。パルスのON時間とOFF時間が交互に繰り返され、それぞれの時間の比率で平均的な出力が制御されます。たとえば、ON時間が長く、OFF時間が短い場合、平均的な出力は高くなります。

PWMは、アナログ信号の出力をシミュレートするため、特に電気モーターの制御に広く使用されています。 PWMを使用することで、モーターの回転速度やトルクを制御することができます。PWMを用いてモーターを制御する場合、PWM信号の周波数は一般的に数キロヘルツから数十キロヘルツの範囲で設定されます。

また、PWMは、LEDの明るさの制御や、オーディオシステムのアンプの音量調整など、さまざまなアプリケーションで使用されます。PWM信号の周波数やパルス幅を制御することで、出力信号の特性を変化させることができます。

### SSR

SSR (Solid State Relay) は、電子回路を用いたリレーの一種で、外部信号に応じてスイッチングを行うための装置です。GPIO信号で制御する場合、デジタル信号を入力として受け取り、出力側に接続された負荷の電源をON/OFF制御します。

SSRは、通常の機械的リレーに比べて、スイッチング速度が速く、寿命が長く、騒音や振動がないというメリットがあります。また、SSRは電気的な絶縁があるため、高電圧や高電流の制御に適しています。

SSRの動作原理は、トライアックやSCRなどの半導体素子を用いたものが一般的です。入力信号がONになると、半導体素子が閉じ、負荷に電流が流れるようになります。逆に、入力信号がOFFになると、半導体素子が開き、負荷に電流が流れなくなります。

GPIO信号でSSRを制御する場合、デジタル信号をSSRの入力端子に接続し、プログラムからGPIOを制御することでON/OFF制御を行います。SSRを使用する際には、負荷の電源や電圧・電流値、SSRの定格電圧などを適切に設定する必要があります。また、SSRの使用にあたっては、電気的な安全性や耐久性を考慮する必要があります。

### ADC

ADCは、アナログ信号をデジタル信号に変換することができるデバイスです。アナログ信号は、連続的な電圧や電流の値を取り得る信号であり、例えば温度、光、音声、加速度などのセンサーからの信号はアナログ信号として出力されます。デジタル信号は、0と1の二つの値しか取らない信号であり、コンピュータやマイコンなどのデジタル回路で処理されます。ADCは、アナログ信号をデジタル信号に変換することで、センサーからの信号をデジタル回路で処理することを可能にします。

ADCは、一般的にはアナログ入力ピンに接続され、アナログ信号をサンプリングし、デジタル信号に変換します。変換の精度は、ビット数で表され、例えば10ビットADCは、2の10乗（1024）の電圧段階に分割して変換を行います。つまり、入力電圧は1024の段階に分割され、最終的に0から1023までの数字で表現されます。これらの数字は、デジタル回路で計算や処理が可能な形式になります。

ADCは、一般的にはマイコンに内蔵されている場合が多く、アナログピンからの入力に対して一定の時間間隔でサンプリングを行い、変換結果をレジスタやメモリに格納します。変換精度や変換速度、入力電圧範囲、入力インピーダンス、インタフェースなどが異なる種類のADCがあります。選択するADCは、応用に応じて、要求される精度、速度、消費電力、コストなどに応じて選択する必要があります。

DAC

DACとは、Digital to Analog Converterの略で、デジタル信号をアナログ信号に変換するための回路のことを指します。

デジタル信号は、0と1の2つの状態で表現されますが、アナログ信号は連続的な値を取るため、デジタル信号をアナログ信号に変換する必要があります。DACは、デジタル信号をアナログ信号に変換するための回路で、主に音声信号の再生や、制御系におけるアナログ出力などに利用されます。

DACの主な構成要素は、デジタル入力信号をアナログ出力信号に変換するためのR-2R回路やR-C回路、オペアンプ、低ノイズ電源などです。一般的には、デジタル信号を入力し、DAC内の回路によってアナログ信号に変換され、アンプを通じて増幅された後、出力されます。

DACは、ビット数や変換速度、精度、電源電圧、入力インタフェースなど、さまざまな仕様があります。また、アナログ回路やデジタル回路に組み込まれる場合もあり、用途に合わせて適切なDACを選択する必要があります。

## 割り込み

[割り込み | Renesas](https://www.renesas.com/jp/ja/support/engineer-school/mcu-programming-peripherals-04-interrupts)

## その他

### IrDA

IrDA (Infrared Data Association)は、赤外線を使用してデータを送信するための規格および技術です。IrDAは、コンピュータや携帯電話などのデバイス間で、高速なデータ通信を可能にするために開発されました。

IrDAは、データ転送速度が115.2 kbpsから16 Mbpsまでの範囲で使用でき、通信距離は通常1メートル以内です。また、IrDAは、赤外線を使用するため、無線での通信でありながら、電波妨害に対する耐性が高いという利点があります。

IrDAには、通信を開始する前にデバイス間で手動で接続する必要があります。この手動接続は、通信のセキュリティを高めるためのもので、デバイス間で直接通信することを確認し、第三者が通信に干渉できないようにするためです。

IrDAは、一般的に、ノートパソコンやスマートフォンなどの小型デバイスで使用され、ファイルの転送やデバイスの同期など、様々な目的に使用されます。IrDAは、BluetoothやWi-Fiなどの無線通信技術に比べて、安全性が高く、エネルギー効率が良いため、一部の用途ではまだ使用されています。

IRQ

Interrupt ReQuest

SDA

シリアルデータ

SCL

シリアルクロック

GPCLK

汎用クロック出力

データを送受信するために使用する信号線

MOSI

Master Output Slave Input

マスターからスレーブに対してデータを送信するために使用

MISO

Master Input Slave Output

スレーブからマスターに対してデータを送信するために使用

SCLK

クロック

CS

チップセレクト

ID_SD

ID_SC

外部にEEPROMというデータを保存するための部品を接続するピン

PWM

Pulse Width Modulation

パルス幅を変えることで、FETなどの素子に流れる電流の時間を変化させ、ヒーターやモーターを制御する信号

### DAC

DAC Decoder信号名

VCC

GND

BCK

DIN

LCK