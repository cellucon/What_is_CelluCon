# CelluCon　セルコン　とは
* 携帯電話網（セルラーネットワーク）を利用し、遠方のラジコン模型のライブ映像、GPS位置、センサ情報を確認して操縦できるシステムのことです。
* セルラーコントロール（CellularControl）短くしてセルコンとしました。 （CellでなくCelluとしたのはCellConという会社が既にあったので。）
* オープンソースプロジェクトです。　GNU General Public License v3.0　https://github.com/cellucon/readme/blob/master/LICENSE

**_システムの概念図_**
![image](https://github.com/cellucon/readme/blob/master/diagram.png)
* スマートフォンをラジコン模型に搭載させて、スマートフォンのカメラ映像とGPS、外部センサによる情報を、インターネットにつながったPCのWeb画面上から確認できます。
* PCにつないだゲームパッドを操作すると、スマートフォンのBluetoothより、ラジコンを操作するコマンドが発信され、ラジコンが操縦できます。
（PCのマウス操作だけでも操作できます）
* Bluetoothを受信するArduinoベースのマイコンが、Bluetooth操作コマンドでラジコンのサーボ、ESC（モーターコントローラー）を制御します。

## 操作するWeb画面（カメラ映像、位置情報、遠隔操作パネル)
![image](https://github.com/cellucon/readme/blob/master/web-pilot.png)
* https://i386koba.github.io/CelluCon.web/ からWeb画面を開けます。
* 航路の記録は　https://i386koba.github.io/CelluCon.web/mapLink.html から参照できます。
* ソースコードは　https://github.com/i386koba/CelluCon.web
　
## スマートフォンで動かすアプリ
* ソースコードは　https://github.com/i386koba/CelluCon.Android
* スマフォはフリーテルのFTJ152Aつかいました。
* Android 4.0.3以上、GPS,磁気センサー、Bluetooth のあるスマフォなら使えます。

## スマートフォンを乗せるラジコン
![image](https://github.com/cellucon/readme/blob/master/rover.png)
TAMIYAのグラスホッパー、完成品を購入しました。
完成品でなくシャーシキットとサーボとESCあれば心得のある人なら安上がりです。

## Bluetoothを受信するArduinoベースのマイコン
* Arduinoスケッチ　https://github.com/i386koba/CellulCon.arduino
* Arduinoベースマイコン基板 https://github.com/i386koba/CelluCon.kicad

## セルコンを動作させるに必要なこと

## 動作の様子 2016.05.05 撮影
https://youtu.be/YdYnNappXGU?t=55s


## 現状の問題点
### 軌跡の誤差

### 両ホイールの回転計設置による

### RTKによる数センチメートル誤差のGPS軌跡

### 空を飛ぶものは違法？

### SkyWayの移行


## 近い将来の展望
### PID制御

### スマフォにPC側のカメラ映像を映してコミュニケート

### スマフォを使わない方法
* ふつうはラズパイとなりますが、HDMIいらないし、Android 動けば楽なのかな。
* 気になるシングルボードコンピュータＰＩＮＥ６４　http://akizukidenshi.com/catalog/g/gM-12067/
* LTE通信モジュール Soracom PCI Express Mini Card (LTE Cat.1) https://soracom.jp/products/ec21-j/


## その他 
* 当初 Droid（Android-OS）+ drone (ドローン)　で　Droidrone　(ドロイドローン)としていましたが2017.10にセルコンに改名しました。
* オープンソースとして多くの人が試験、実験しやすいようにドキュメントを充実させていきたいです。
* 雑多なことは[Wiki](https://github.com/cellucon/readme/wiki)に書いていきます。
