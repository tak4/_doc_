/* Exported functions --------------------------------------------------------*/

/** @defgroup I2C_Exported_Functions I2C Exported Functions
  * @{
  */

/** @defgroup I2C_Exported_Functions_Group1 Initialization and de-initialization functions
 *  @brief    Initialization and Configuration functions
 *
@verbatim
 ===============================================================================
              ##### Initialization and de-initialization functions #####
 ===============================================================================
    [..]  This subsection provides a set of functions allowing to initialize and
          deinitialize the I2Cx peripheral:
      (+) User must Implement HAL_I2C_MspInit() function in which he configures
          all related peripherals resources (CLOCK, GPIO, DMA, IT and NVIC).
      (+) Call the function HAL_I2C_Init() to configure the selected device with
          the selected configuration:
        (++) Communication Speed
        (++) Duty cycle
        (++) Addressing mode
        (++) Own Address 1
        (++) Dual Addressing mode
        (++) Own Address 2
        (++) General call mode
        (++) Nostretch mode
      (+) Call the function HAL_I2C_DeInit() to restore the default configuration
          of the selected I2Cx peripheral.
@endverbatim
  * @{
  */

/**
  * @brief  Initializes the I2C according to the specified parameters
  *         in the I2C_InitTypeDef and initialize the associated handle.
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *                the configuration information for the specified I2C.
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_Init(I2C_HandleTypeDef *hi2c)


/* エクスポートされた関数 --------------------------------------------------------------------------------*/．

/** @defgroup I2C_Exported_Functions I2C エクスポートファンクションズ
  * @{
  */

/** @defgroup I2C_Exported_Functions_Group1 初期化・非初期化関数
 * 初期化・設定関数について
 *
アババティム
 ===============================================================================
              初期化・非初期化関数 ##### 初期化・非初期化関数 ##### 初期化・非初期化関数
 ===============================================================================
    [このサブセクションは、初期化および初期化を行うための一連の関数を提供します。
          I2Cxペリフェラルをdeinitializeする：
      (+) ユーザーは、HAL_I2C_MspInit()関数を実装し、その中で、以下の設定を行わなければならない。
          関連するすべてのペリフェラルリソース（CLOCK、GPIO、DMA、IT、NVIC）。
      (+) 関数HAL_I2C_Init()を呼び出して、選択したデバイスを以下のように構成する。
          を選択すると、選択した設定になります：
        (++) 通信速度
        (++) デューティサイクル
        (++) アドレス指定モード
        (++) 自分のアドレス1
        (++) デュアル・アドレス・モード
        (++) 自分のアドレス2
        (++) 一般通話モード
        (++) ノストレッチャーモード
      (+) 関数HAL_I2C_DeInit()を呼び出して、デフォルトの設定を復元する。
          選択したI2Cxペリフェラルの
エンドベルバティム
  * @{
  */

/**
  * @brief 指定されたパラメータに従って、I2Cを初期化する。
  * I2C_InitTypeDef に格納され、関連するハンドルを初期化する。
  * @param hi2c I2C_HandleTypeDef構造体へのポインタ。
  * 指定された I2C の設定情報を取得する。
  * @retval HALステータス
  */
HAL_StatusTypeDef HAL_I2C_Init(I2C_HandleTypeDef *hi2c)



/**
  * @brief  DeInitialize the I2C peripheral.
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *         the configuration information for the specified I2C.
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_DeInit(I2C_HandleTypeDef *hi2c)


/**
  * @brief I2Cペリフェラルを初期化する（DeInitialize）。
  * @param hi2c I2C_HandleTypeDef構造体へのポインタを含む。
  * 指定された I2C の設定情報を取得する。
  * @retval HALステータス
  */
HAL_StatusTypeDef HAL_I2C_DeInit(I2C_HandleTypeDef *hi2c)



/**
  * @brief  Initialize the I2C MSP.
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *         the configuration information for the specified I2C.
  * @retval None
  */
__weak void HAL_I2C_MspInit(I2C_HandleTypeDef *hi2c)
{

/**
  * @brief I2C MSPを初期化する。
  * @param hi2c I2C_HandleTypeDef構造体へのポインタを格納する。
  * 指定された I2C の設定情報を取得する。
  * @retval なし
  */
__weak void HAL_I2C_MspInit(I2C_HandleTypeDef *hi2c)
{

/**
  * @brief  DeInitialize the I2C MSP.
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *         the configuration information for the specified I2C.
  * @retval None
  */
__weak void HAL_I2C_MspDeInit(I2C_HandleTypeDef *hi2c)
{

 /**
  * @brief I2C MSPを初期化する。
  * @param hi2c I2C_HandleTypeDef構造体へのポインタを含む。
  * 指定された I2C の設定情報を取得する。
  * @retval なし
  */
__weak void HAL_I2C_MspDeInit(I2C_HandleTypeDef *hi2c)
{


/**
  * @brief  Register a User I2C Callback
  *         To be used instead of the weak predefined callback
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *                the configuration information for the specified I2C.
  * @param  CallbackID ID of the callback to be registered
  *         This parameter can be one of the following values:
  *          @arg @ref HAL_I2C_MASTER_TX_COMPLETE_CB_ID Master Tx Transfer completed callback ID
  *          @arg @ref HAL_I2C_MASTER_RX_COMPLETE_CB_ID Master Rx Transfer completed callback ID
  *          @arg @ref HAL_I2C_SLAVE_TX_COMPLETE_CB_ID Slave Tx Transfer completed callback ID
  *          @arg @ref HAL_I2C_SLAVE_RX_COMPLETE_CB_ID Slave Rx Transfer completed callback ID
  *          @arg @ref HAL_I2C_LISTEN_COMPLETE_CB_ID Listen Complete callback ID
  *          @arg @ref HAL_I2C_MEM_TX_COMPLETE_CB_ID Memory Tx Transfer callback ID
  *          @arg @ref HAL_I2C_MEM_RX_COMPLETE_CB_ID Memory Rx Transfer completed callback ID
  *          @arg @ref HAL_I2C_ERROR_CB_ID Error callback ID
  *          @arg @ref HAL_I2C_ABORT_CB_ID Abort callback ID
  *          @arg @ref HAL_I2C_MSPINIT_CB_ID MspInit callback ID
  *          @arg @ref HAL_I2C_MSPDEINIT_CB_ID MspDeInit callback ID
  * @param  pCallback pointer to the Callback function
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_RegisterCallback(I2C_HandleTypeDef *hi2c, HAL_I2C_CallbackIDTypeDef CallbackID, pI2C_CallbackTypeDef pCallback)


/**
  * ユーザーI2Cコールバックを登録します。
  * 弱い定義済みコールバックの代わりに使用されます。
  * @param hi2c I2C_HandleTypeDef 構造体へのポインタを指定します。
  * 指定された I2C の設定情報を取得する。
  * @param CallbackID 登録するコールバックのID。
  * このパラメータは、以下の値のいずれかとすることができる：
  * HAL_I2C_MASTER_TX_COMPLETE_CB_ID マスターTx転送完了コールバックID。
  * @arg @ref HAL_I2C_MASTER_RX_COMPLETE_CB_ID マスターRx転送完了コールバックID
  * @arg @ref HAL_I2C_SLAVE_TX_COMPLETE_CB_ID スレーブ受信転送完了コールバックID
  * @arg @ref HAL_I2C_SLAVE_RX_COMPLETE_CB_ID スレーブRx転送完了コールバックID
  * @arg @ref HAL_I2C_LISTEN_COMPLETE_CB_ID リッスンコンプリートコールバックID
  * @arg @ref HAL_I2C_MEM_TX_COMPLETE_CB_ID メモリTx転送コールバックID
  * @arg @ref HAL_I2C_MEM_RX_COMPLETE_CB_ID メモリRx転送完了コールバックID
  * @arg @ref HAL_I2C_ERROR_CB_ID エラーのコールバック ID。
  * @arg @ref HAL_I2C_ABORT_CB_ID アボートコールバック ID
  * @arg @ref HAL_I2C_MSPINIT_CB_ID MspInit コールバック ID
  * @arg @ref HAL_I2C_MSPDEINIT_CB_ID MspDeInit コールバック ID
  * param pCallback コールバック関数へのポインタを指定します。
  * @retval HALステータス
  */
HAL_StatusTypeDef HAL_I2C_RegisterCallback(I2C_HandleTypeDef *hi2c, HAL_I2C_CallbackIDTypeDef CallbackID, pI2C_CallbackTypeDef pCallback)



/**
  * @brief  Unregister an I2C Callback
  *         I2C callback is redirected to the weak predefined callback
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *                the configuration information for the specified I2C.
  * @param  CallbackID ID of the callback to be unregistered
  *         This parameter can be one of the following values:
  *         This parameter can be one of the following values:
  *          @arg @ref HAL_I2C_MASTER_TX_COMPLETE_CB_ID Master Tx Transfer completed callback ID
  *          @arg @ref HAL_I2C_MASTER_RX_COMPLETE_CB_ID Master Rx Transfer completed callback ID
  *          @arg @ref HAL_I2C_SLAVE_TX_COMPLETE_CB_ID Slave Tx Transfer completed callback ID
  *          @arg @ref HAL_I2C_SLAVE_RX_COMPLETE_CB_ID Slave Rx Transfer completed callback ID
  *          @arg @ref HAL_I2C_LISTEN_COMPLETE_CB_ID Listen Complete callback ID
  *          @arg @ref HAL_I2C_MEM_TX_COMPLETE_CB_ID Memory Tx Transfer callback ID
  *          @arg @ref HAL_I2C_MEM_RX_COMPLETE_CB_ID Memory Rx Transfer completed callback ID
  *          @arg @ref HAL_I2C_ERROR_CB_ID Error callback ID
  *          @arg @ref HAL_I2C_ABORT_CB_ID Abort callback ID
  *          @arg @ref HAL_I2C_MSPINIT_CB_ID MspInit callback ID
  *          @arg @ref HAL_I2C_MSPDEINIT_CB_ID MspDeInit callback ID
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_UnRegisterCallback(I2C_HandleTypeDef *hi2c, HAL_I2C_CallbackIDTypeDef CallbackID)

/**
  * I2C コールバックの登録を解除する。
  * I2Cコールバックは、弱い定義済みコールバックにリダイレクトされます。
  * @param hi2c I2C_HandleTypeDef 構造体へのポインタを指定します。
  * 指定された I2C の設定情報を取得する。
  * @param CallbackID 登録解除されるコールバックのID。
  * 本パラメータには、以下のいずれかの値を指定することができます：
  * このパラメータは、以下の値のいずれかを指定することができる：
  * @arg @ref HAL_I2C_MASTER_TX_COMPLETE_CB_ID マスターTx転送完了コールバックID
  * @arg @ref HAL_I2C_MASTER_RX_COMPLETE_CB_ID マスターRx転送完了コールバックID
  * @arg @ref HAL_I2C_SLAVE_TX_COMPLETE_CB_ID スレーブ受信転送完了コールバックID
  * @arg @ref HAL_I2C_SLAVE_RX_COMPLETE_CB_ID スレーブRx転送完了コールバックID
  * @arg @ref HAL_I2C_LISTEN_COMPLETE_CB_ID リッスンコンプリートコールバックID
  * @arg @ref HAL_I2C_MEM_TX_COMPLETE_CB_ID メモリTx転送コールバックID
  * @arg @ref HAL_I2C_MEM_RX_COMPLETE_CB_ID メモリRx転送完了コールバックID
  * @arg @ref HAL_I2C_ERROR_CB_ID エラーのコールバック ID。
  * @arg @ref HAL_I2C_ABORT_CB_ID アボートコールバック ID
  * @arg @ref HAL_I2C_MSPINIT_CB_ID MspInit コールバック ID
  * @arg @ref HAL_I2C_MSPDEINIT_CB_ID MspDeInit コールバック ID
  * @retval HALステータス
  */
HAL_StatusTypeDef HAL_I2C_UnRegisterCallback(I2C_HandleTypeDef *hi2c, HAL_I2C_CallbackIDTypeDef CallbackID)



/**
  * @brief  Register the Slave Address Match I2C Callback
  *         To be used instead of the weak HAL_I2C_AddrCallback() predefined callback
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *                the configuration information for the specified I2C.
  * @param  pCallback pointer to the Address Match Callback function
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_RegisterAddrCallback(I2C_HandleTypeDef *hi2c, pI2C_AddrCallbackTypeDef pCallback)


/**
  * スレーブアドレス一致 I2C コールバックを登録します。
  * 弱い HAL_I2C_AddrCallback() 定義済みコールバックの代わりに使用されます。
  * @param hi2c I2C_HandleTypeDef 構造体へのポインタを指定します。
  * 指定された I2C のコンフィギュレーション情報です。
  * @param pCallback アドレス一致コールバック関数へのポインター
  * @retval HALステータス
  */
HAL_StatusTypeDef HAL_I2C_RegisterAddrCallback(I2C_HandleTypeDef *hi2c, pI2C_AddrCallbackTypeDef pCallback)



/**
  * @brief  UnRegister the Slave Address Match I2C Callback
  *         Info Ready I2C Callback is redirected to the weak HAL_I2C_AddrCallback() predefined callback
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *                the configuration information for the specified I2C.
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_UnRegisterAddrCallback(I2C_HandleTypeDef *hi2c)


/**
  * スレーブアドレスマッチI2Cコールバックの登録を解除する。
  * Info Ready I2C Callbackは、弱いHAL_I2C_AddrCallback()の定義済みコールバックにリダイレクトされます。
  * @param hi2c I2C_HandleTypeDef 構造体へのポインタを指定します。
  * 指定された I2C の設定情報を取得する。
  * @retval HALステータス
  */
HAL_StatusTypeDef HAL_I2C_UnRegisterAddrCallback(I2C_HandleTypeDef *hi2c)




/** @defgroup I2C_Exported_Functions_Group2 Input and Output operation functions
 *  @brief   Data transfers functions
 *
@verbatim
 ===============================================================================
                      ##### IO operation functions #####
 ===============================================================================
    [..]
    This subsection provides a set of functions allowing to manage the I2C data
    transfers.
    (#) There are two modes of transfer:
       (++) Blocking mode : The communication is performed in the polling mode.
            The status of all data processing is returned by the same function
            after finishing transfer.
       (++) No-Blocking mode : The communication is performed using Interrupts
            or DMA. These functions return the status of the transfer startup.
            The end of the data processing will be indicated through the
            dedicated I2C IRQ when using Interrupt mode or the DMA IRQ when
            using DMA mode.
    (#) Blocking mode functions are :
        (++) HAL_I2C_Master_Transmit()
        (++) HAL_I2C_Master_Receive()
        (++) HAL_I2C_Slave_Transmit()
        (++) HAL_I2C_Slave_Receive()
        (++) HAL_I2C_Mem_Write()
        (++) HAL_I2C_Mem_Read()
        (++) HAL_I2C_IsDeviceReady()
    (#) No-Blocking mode functions with Interrupt are :
        (++) HAL_I2C_Master_Transmit_IT()
        (++) HAL_I2C_Master_Receive_IT()
        (++) HAL_I2C_Slave_Transmit_IT()
        (++) HAL_I2C_Slave_Receive_IT()
        (++) HAL_I2C_Mem_Write_IT()
        (++) HAL_I2C_Mem_Read_IT()
        (++) HAL_I2C_Master_Seq_Transmit_IT()
        (++) HAL_I2C_Master_Seq_Receive_IT()
        (++) HAL_I2C_Slave_Seq_Transmit_IT()
        (++) HAL_I2C_Slave_Seq_Receive_IT()
        (++) HAL_I2C_EnableListen_IT()
        (++) HAL_I2C_DisableListen_IT()
        (++) HAL_I2C_Master_Abort_IT()
    (#) No-Blocking mode functions with DMA are :
        (++) HAL_I2C_Master_Transmit_DMA()
        (++) HAL_I2C_Master_Receive_DMA()
        (++) HAL_I2C_Slave_Transmit_DMA()
        (++) HAL_I2C_Slave_Receive_DMA()
        (++) HAL_I2C_Mem_Write_DMA()
        (++) HAL_I2C_Mem_Read_DMA()
        (++) HAL_I2C_Master_Seq_Transmit_DMA()
        (++) HAL_I2C_Master_Seq_Receive_DMA()
        (++) HAL_I2C_Slave_Seq_Transmit_DMA()
        (++) HAL_I2C_Slave_Seq_Receive_DMA()
    (#) A set of Transfer Complete Callbacks are provided in non Blocking mode:
        (++) HAL_I2C_MasterTxCpltCallback()
        (++) HAL_I2C_MasterRxCpltCallback()
        (++) HAL_I2C_SlaveTxCpltCallback()
        (++) HAL_I2C_SlaveRxCpltCallback()
        (++) HAL_I2C_MemTxCpltCallback()
        (++) HAL_I2C_MemRxCpltCallback()
        (++) HAL_I2C_AddrCallback()
        (++) HAL_I2C_ListenCpltCallback()
        (++) HAL_I2C_ErrorCallback()
        (++) HAL_I2C_AbortCpltCallback()
@endverbatim
  * @{
  */

/**
  * @brief  Transmits in master mode an amount of data in blocking mode.
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *                the configuration information for the specified I2C.
  * @param  DevAddress Target device address: The device 7 bits address value
  *         in datasheet must be shifted to the left before calling the interface
  * @param  pData Pointer to data buffer
  * @param  Size Amount of data to be sent
  * @param  Timeout Timeout duration
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_Master_Transmit(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size, uint32_t Timeout)


/** @defgroup I2C_Exported_Functions_Group2 入出力操作関数
 * データ転送機能
 *
アットバーバティム
 ===============================================================================
                      ##### IO演算機能 #####。
 ===============================================================================
    [..]
    このサブセクションは、I2Cデータを管理するための一連の機能を提供します。
    を転送します。
    (#) 転送には2つのモードがあります：
       (++) ブロッキングモード ： ポーリングモードで通信を行います。
            すべてのデータ処理のステータスは，同じ関数で返される
            転送終了後
       (++) ノーブロッキングモード．割り込みを使用して通信を行う
            またはDMAを使用します。これらの関数は、転送開始のステータスを返す。
            データ処理の終了を示すのが、この関数です。
            インタラプトモード使用時は専用のI2C IRQを、DMAモード使用時はDMA IRQを使用します。
            DMA モードで使用します。
    (#) ブロッキングモードの関数は ：
        (++) HAL_I2C_Master_Transmit()
        (++) HAL_I2C_Master_Receive()
        (++) HAL_I2C_Slave_Transmit()
        (++) HAL_I2C_Slave_Receive()
        (++) HAL_I2C_Mem_Write()
        (++) HAL_I2C_Mem_Read()
        (++) HAL_I2C_IsDeviceReady()
    (#) 割り込みによるノーブロッキングモードの機能は以下の通りです：
        (++) HAL_I2C_Master_Transmit_IT()
        (++) HAL_I2C_Master_Receive_IT()
        (++) HAL_I2C_Slave_Transmit_IT()
        (++) HAL_I2C_Slave_Receive_IT()
        (++) HAL_I2C_Mem_Write_IT()
        (++) HAL_I2C_Mem_Read_IT()
        (++) HAL_I2C_Master_Seq_Transmit_IT()
        (++) HAL_I2C_Master_Seq_Receive_IT()
        (++) HAL_I2C_Slave_Seq_Transmit_IT()
        (++) HAL_I2C_Slave_Seq_Receive_IT()
        (++) HAL_I2C_EnableListen_IT()
        (++) HAL_I2C_DisableListen_IT()
        (++) HAL_I2C_Master_Abort_IT()
    (#) DMAによるノーブロッキングモードの関数は以下の通りです：
        (++) HAL_I2C_Master_Transmit_DMA()
        (++) HAL_I2C_Master_Receive_DMA()
        (++) HAL_I2C_Slave_Transmit_DMA()
        (++) HAL_I2C_Slave_Receive_DMA()
        (++) HAL_I2C_Mem_Write_DMA()
        (++) HAL_I2C_Mem_Read_DMA()
        (++) HAL_I2C_Master_Seq_Transmit_DMA()
        (++) HAL_I2C_Master_Seq_Receive_DMA()
        (++) HAL_I2C_Slave_Seq_Transmit_DMA()
        (++) HAL_I2C_Slave_Seq_Receive_DMA()
    (#) 非ブロッキングモードでは、転送完了コールバックのセットが提供されます：
        (++) HAL_I2C_MasterTxCpltCallback()
        (++) HAL_I2C_MasterRxCpltCallback()
        (++) HAL_I2C_SlaveTxCpltCallback()
        (++) HAL_I2C_SlaveRxCpltCallback()
        (++) HAL_I2C_MemTxCpltCallback()
        (++) HAL_I2C_MemRxCpltCallback()
        (++) HAL_I2C_AddrCallback()
        (++) HAL_I2C_ListenCpltCallback()
        (++) HAL_I2C_ErrorCallback()
        (++) HAL_I2C_AbortCpltCallback()
エンデバーバティム
  * @{
  */

/**
  * @brief マスタモードでブロッキングモードのデータ量を送信する。
  * @param hi2c 以下の内容を含む I2C_HandleTypeDef 構造体へのポインタ。
  * 指定された I2C の設定情報を取得する。
  * @param DevAddress 対象デバイスのアドレスです： デバイスの7ビットのアドレス値
  インターフェイスを呼び出す前に、データシートの*を左にシフトする必要があります。
  * param pData データバッファへのポインタ
  * @param Size 送信するデータ量。
  * @param Timeout タイムアウト時間
  * @retval HALステータス
  */
HAL_StatusTypeDef HAL_I2C_Master_Transmit(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size, uint32_t Timeout)



/**
  * @brief  Receives in master mode an amount of data in blocking mode.
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *                the configuration information for the specified I2C.
  * @param  DevAddress Target device address: The device 7 bits address value
  *         in datasheet must be shifted to the left before calling the interface
  * @param  pData Pointer to data buffer
  * @param  Size Amount of data to be sent
  * @param  Timeout Timeout duration
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_Master_Receive(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size, uint32_t Timeout)


/**
  * @brief マスタモードでブロッキングモードのデータ量を受信する。
  * @param hi2c I2C_HandleTypeDef 構造体へのポインタ。
  * 指定された I2C の設定情報を取得する。
  * @param DevAddress 対象デバイスのアドレスです： デバイスの7ビットのアドレス値
  インターフェイスを呼び出す前に、データシートの*を左にシフトする必要があります。
  * param pData データバッファへのポインタ
  * @param Size 送信するデータ量。
  * @param Timeout タイムアウト時間
  * @retval HALステータス
  */
HAL_StatusTypeDef HAL_I2C_Master_Receive(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size, uint32_t Timeout)



/**
  * @brief  Transmits in slave mode an amount of data in blocking mode.
  * @param  hi2c Pointer to a I2C_HandleTypeDef structure that contains
  *                the configuration information for the specified I2C.
  * @param  pData Pointer to data buffer
  * @param  Size Amount of data to be sent
  * @param  Timeout Timeout duration
  * @retval HAL status
  */
HAL_StatusTypeDef HAL_I2C_Slave_Transmit(I2C_HandleTypeDef *hi2c, uint8_t *pData, uint16_t Size, uint32_t Timeout)

