# WSH

## VBScript Doc
https://docs.microsoft.com/ja-jp/previous-versions/windows/scripting/cc364460(v=msdn.10)?redirectedfrom=MSDN

## Wiki
https://techinfoofmicrosofttech.osscons.jp/index.php?WMI

## Script Center
https://gallery.technet.microsoft.com/scriptcenter

## CreateObject
CreateObjectは、プログラムIDを引数にとり、そのプログラムIDで表されるCOMオブジェクトのインスタンス（実体）を作成して、そのオブジェクトを返すメソッドである。ここでいう「プログラムID」とは、Windows環境で利用可能なコンポーネントに付けられた名前である。クラスIDの一覧は、レジストリのHKEY_CLASSES_ROOT以下に記述されている

## WMI（Windows Management Instrumentation）
WMI（Windows Management Instrumentation）とは、WBEM（Web-based Enterprise Management）の標準仕様に従ってマイクロソフトが実装したWindowsシステムを管理するためのインターフェイスである。WSHスクリプトなどから呼び出すことで、Windowsの管理などを実行できる。

## wbemtest
WMI  
名前空間への接続、各種クラスの参照からメソッドの実行までスクリプトやプログラムを書くことなく動作テストが行える

接続押下  

名前空間  
root\cimv2

クエリ
Select * From Win32_NetworkAdapterConfiguration Where IPEnabled = True

