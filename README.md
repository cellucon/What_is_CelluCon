# CelluCon　セルコン　とは

携帯電話網（セルラーネットワーク）を利用し、遠方のラジコン模型のライブ映像、GPS位置、センサ情報を確認して操縦できるシステムのことです。
* セルラーコントロール（CellularControl）短くしてセルコンとしました。 （CellでなくCelluとしたのはCellConという会社が既にあったので。）
* オープンソースプロジェクト　GNU General Public License v3.0　https://github.com/cellucon/readme/blob/master/LICENSE

**_システムの概念図_**
![image](https://github.com/cellucon/readme/blob/master/diagram.png)

* スマートフォンをラジコン模型に搭載させて、スマートフォンのカメラ映像とGPS、外部センサによる情報を、インターネットにつながったPCのWeb画面上から確認できます。
* PCにつないだゲームパッドを操作すると、スマートフォンのBluetoothより、ラジコンを操作するコマンドが発信され、ラジコンが操縦できます。
（PCのマウス操作だけでも操作できます）
* Bluetoothを受信するArduinoベースのマイコンが、Bluetooth操作コマンドでラジコンのサーボ、ESC（モーターコントローラー）を制御します。


## 操作するWeb画面（カメラ映像、位置情報、遠隔操作パネル)
![image](https://github.com/cellucon/readme/blob/master/web-pilot.png)


## スマートフォンを乗せたラジコン
![image](https://github.com/cellucon/readme/blob/master/rover.png)


(Arduinoで制御できるステッピングモーター
格安
## Droidrone（ドロイドローン)からの改名（2017）
* 言わずもがなですが、Droid（Android-OS）+ drone (ドローン)　で　Droidrone　と命名しました。
* 最近ドローンの世間の印象が悪いので名称考え中で（仮）としました。また、よくあるスマフォのWiFiで模型をコントロール方法と勘違いされるかもなので、Cellular network Pilot　とかがいいかもです。

#


https://osdn.jp/projects/opensource/wiki/licenses%2FApache_License_2.0

* Droidroneをオープンソースとして多くの人が試験、実験しやすいようにドキュメントを充実させていきます。
* ドキュメントは[Wiki](https://github.com/i386koba/Droidrone/wiki)にあります。
* 多くの方に、いろいろなことを検証していただきたいと考えています。
* いろいろな場面で実験して試されていくうちに、安定したシステムになると考えています。
* [プロジェクトの進め方について](https://github.com/i386koba/Droidrone/wiki/Project)

# 動作の様子 
2016.05.05 撮影
[![](http://img.youtube.com/vi/YdYnNappXGU/0.jpg)](https://youtu.be/YdYnNappXGU?t=55s)

