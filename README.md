# CelluCon　セルコン　とは
* 携帯電話網（セルラーネットワーク）を利用し、遠方のラジコン模型のライブ映像、GPS位置、センサ情報を確認して操縦できるシステムのことです。
* セルラーコントロール（CellularControl）短くしてセルコン。 （CellでなくCelluとしたのはCellConという会社があったので。）
* オープンソースプロジェクトです。　GNU General Public License v3.0　https://github.com/cellucon/readme/blob/master/LICENSE

**_システムの概念図_**
![image](https://github.com/cellucon/readme/blob/master/diagram.png)
* スマートフォンをラジコン模型に搭載させて、スマートフォンのカメラ映像とGPS、外部センサによる情報を、インターネットにつながったPCのWeb画面上から確認できます。
* PCにつないだゲームパッドを操作すると、スマートフォンのBluetoothより、ラジコンを操作するコマンドが発信され、ラジコンが操縦できます。
（PCのマウス操作だけでも操作できます）
* Bluetoothを受信するArduinoベースのマイコンが、Bluetooth操作コマンドでラジコンのサーボ、ESC（モーターコントローラー）を制御します。

## スマートフォンで動かすアプリ
* Android 4.0.3以上、GPS,磁気センサー、Bluetooth のあるスマフォで実行できます。
* APKは　https://github.com/i386koba/CelluCon.Android/raw/master/app-debug.apk からスマフォにダウンロードして実行してください。
* アプリ名は「CellularRC」です。（旧アプリの名前です。そのうち変えます。2017．10.19）
* 現状、上記アプリはGooglePlayから提供していないため、Androidの設定で「提供元不明アプリを実行する」としてください。
* 起動するとGoogleIDを聞かれます.
![image](https://github.com/cellucon/readme/blob/master/GoogleID-select.png)
*GoogleIDを選択するか、追加してください。ログインしたGoogleIDのGoogleドライブにPeer.JSコネクションIDが保存されます。
* ソースコードは　https://github.com/i386koba/CelluCon.Android


## 操作するWeb画面（カメラ映像、位置情報、遠隔操作パネル)
![image](https://github.com/cellucon/readme/blob/master/web-pilot.png)
* https://i386koba.github.io/CelluCon.web/ からWeb画面を開けます。
![image](https://github.com/cellucon/readme/blob/master/CelluerRC-RUN.png)

* 航路の記録は　https://i386koba.github.io/CelluCon.web/mapLink.html から参照できます。
* ソースコードは　https://github.com/i386koba/CelluCon.web
　
## スマートフォンを乗せるラジコン
![image](https://github.com/cellucon/readme/blob/master/rover.png)
* TAMIYAのグラスホッパー、完成品を購入して、スマフォをつける改造しました。完成品はプロポが余ります。
* ラジコンの心得のある人なら完成品でなく、シャーシキットとサーボとESCを別購入すればあれば安上がりでプロポが余りません。

## Bluetoothを受信するArduinoベースのマイコン
* Arduinoで手作りした場合 https://github.com/i386koba/Droidrone-ino
* Arduinoスケッチ　https://github.com/i386koba/CellulCon.arduino
* Arduinoベースマイコン基板 https://github.com/i386koba/CelluCon.kicad

## セルコンを動作させるには。
* Bluetoothを受信するArduinoベースのマイコンを作成 https://github.com/i386koba/Droidrone-ino
* Arduinoスケッチ　https://github.com/i386koba/CellulCon.arduino　をマイコンに書き込み
* ラジコンを作成し、マイコンにサーボとESCをつなげる。回転センサはとりあえずなくてもよい。
* Androidスマフォに https://github.com/i386koba/CelluCon.Android よりアプリをインストール。
* アプリを起動すると、既存のGoogleIDを問い合わせされるので回答すると、WebRTC（PeerJS)のIDをGoogleドライブに自動アップロードする。
*　操作画面

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

### 非アンドロイド化
* Cordova https://cordova.apache.org/ 
* BluetoothがCordovaプラグインはBLE対応のみのようなのでArduino基板のBLE化も必要。

### スマフォを使わない方法
* ふつうはラズパイとなりますが、HDMIいらないし、Android 動けば楽なのかな。
* 気になるシングルボードコンピュータＰＩＮＥ６４　http://akizukidenshi.com/catalog/g/gM-12067/
* LTE通信モジュール Soracom PCI Express Mini Card (LTE Cat.1) https://soracom.jp/products/ec21-j/


## その他 
* 当初 Droid（Android-OS）+ drone (ドローン)　で　Droidrone　(ドロイドローン)としていましたが2017.10にセルコンに改名しました。
* オープンソースとして多くの人が試験、実験しやすいようにドキュメントを充実させていきたいです。
* 雑多なことは[Wiki](https://github.com/cellucon/readme/wiki)に書いていきます。
