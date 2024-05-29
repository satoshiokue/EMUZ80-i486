# EMUZ80-i486

電脳伝説さん(@vintagechips)のEMUZ80が出力するZ80 CPU信号をメザニンボードで組み替え、5V仕様のi486を動作させることができます。  

FoxTechさんがYoutubeで発表された"486 Breadboard Computer"のDynamic Bus sizing制御手法に感銘を受けて製作しました。  

https://youtu.be/wSiDSdHS2QQ?si=lTsH4jV_w0vX-F2U

HACKERDAY
IT’S A 486 COMPUTER, ON A BREADBOARD  
https://hackaday.com/tag/i486/  

![MEZi486](https://github.com/satoshiokue/EMUZ80-i486/blob/main/MEZi486.jpg)
 
ソースコードは電脳伝説さんのEMUZ80用main.cを元に改変してGPLライセンスに基づいて公開するものです。

## メザニンボード
https://github.com/satoshiokue/MEZi486  

## ファームウェア
emuz80_i486.cをEMUZ80で配布されているフォルダemuz80.X下のmain.cと置き換えて使用してください。  
ターゲットのPICを適切に変更してビルドしてください。  

## アドレスマップ
```
Memory
(PIC18F47Q83/PIC18F47Q84)
RAM   0x0000 - 0x1FFF 8KBytes
ROM   0x4000 - 0x6FFF Nascom BASIC
      0x7000 - 0x7FFF Universal Monitor

(PIC18F47Q43)
RAM   0x0000 - 0x0FFF 4KBytes
ROM   0x4000 - 0x6FFF Nascom BASIC
      0x7000 - 0x7FFF Universal Monitor

I/O
UART  0x0000   Data REGISTER
      0x0001   Control REGISTER
```

## PICプログラムの書き込み
EMUZ80技術資料8ページにしたがってPICに適合するemui486_Qxx.hexファイルを書き込んでください。  

emui486_Q43.hex ： PIC18F47Q43用  
emui486_Q8x.hex ： PIC18F47Q83/84用 　

またはArduino UNOを用いてPICを書き込みます。  
https://github.com/satoshiokue/Arduino-PIC-Programmer

## ファームウェア
8080/Z80用Nascon BASICのソースファイルを8088/8086用にコンバートして作成した Nascom BASICとUniversal Monitorを搭載しました。  

Vectorセットアップ処理はSBCV20データパックのV20BASIC.ASMを参考にしました。  

スイッチサイエンス - SBCV20 ルーズキット  
https://www.switch-science.com/products/6902/

Nascom BASIC 8086  
https://github.com/satoshiokue/8086_NASCOM_BASIC  

Universal Monitor  
https://electrelic.com/electrelic/node/1317

```
MEZi486 2.909MHz

Universal Monitor 8086
80386
] b

INTEL8080 Based x86 BASIC Ver 4.7b
Copyright (C) 1978 by Microsoft
1657 Bytes free
Ok
monitor

Universal Monitor 8086
80386
] 
```

パワーオンでUniversal Monitorが起動します。  
bコマンドでBASICが起動します。  
BASICからmonitorコマンドでUniversal Monitorがコールドスタートします。  

## 参考）EMUZ80
EUMZ80はZ80CPUとPIC18F47Q43のDIP40ピンIC2つで構成されるシンプルなコンピュータです。

![EMUZ80](https://github.com/satoshiokue/EMUZ80-6502/blob/main/imgs/IMG_Z80.jpeg)

電脳伝説 - EMUZ80が完成  
https://vintagechips.wordpress.com/2022/03/05/emuz80_reference  

EMUZ80専用プリント基板 - オレンジピコショップ  
https://store.shopping.yahoo.co.jp/orangepicoshop/pico-a-051.html
