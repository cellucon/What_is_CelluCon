# CelluCon　セルコン　とは
* セルラーコントロール（CellularControl）のことで携帯電話網（セルラーネットワーク）を利用し、遠方のラジコン模型のライブ映像、GPS位置、センサ情報を確認して操縦できるシステムのことです。短くしてセルコン。
* オープンソースプロジェクトとしています。　GNU General Public License v3.0　https://github.com/cellucon/readme/blob/master/LICENSE
 （2017年10月時点）
 
**_システムの概念図_**
![image](https://github.com/cellucon/readme/blob/master/diagram.png)
* スマートフォンをラジコン模型に搭載させて、スマートフォンのカメラ映像とGPS、外部センサによる情報を、インターネットにつながったPCのWeb画面上から確認できます。
* PCにつないだゲームパッドを操作すると、スマートフォンのBluetoothより、ラジコンを操作するコマンドが発信され、ラジコンが操縦できます。
（PCのマウス操作だけでも操作できます）
* Bluetoothを受信するArduinoベースのマイコンが、Bluetooth操作コマンドでラジコンのサーボ、ESC（モーターコントローラー）を制御します。

## セルコンを動かすまで
* [wiki](https://github.com/cellucon/What_is_CelluCon/wiki)にまとめてあります。
* [Qiita](https://qiita.com/i386koba/items/873869926bde7614b128) にも投稿あります。

## ソース
* Androidアプリのソースコードは　https://github.com/i386koba/CelluCon.Android
* 操作するWeb画面のソースコードは　https://github.com/i386koba/CelluCon.web
* Arduinoスケッチの参考　https://github.com/i386koba/CellulCon.arduino 
* Arduinoベース専用マイコン基板（KiCAD） https://github.com/i386koba/CelluCon.kicad

## 動作の様子 2016.05.05 撮影
https://youtu.be/YdYnNappXGU?t=55s

## 現状の問題点と近い将来の展望

### 軌跡の誤差
* GPSは10mほどの誤差があり、小さなラジコンを操作するには不便です。
* 国産GPS みちびき使えば　数センチの精度になるとニュースで聞いた！　(実はみちびきを受信するだけではだめだった)
* みちびき対応スマフォかいましたが、ほとんど精度良くなりません。後述するようにネットワーク型RTK測量でないとダメなようです。

#### ネットワーク型RTK測量による数センチメートル誤差のGPS軌跡
* ネットワーク型RTK測量とは、利用者が現場で取得した衛星データと、周辺の電子基準点の観測 データから作成された補正情報を組み合わせ、リアルタイムでcm級の測量を効率的に行う方式です （RTK：リアルタイム・キネマティック）。
* GPSモジュール（u-blox8）でRTKできるとのこと.ラジコンに搭載したu-blox GPSデータをWebRTCで送信し、Web画面のPCにも u-blox GPSを取り付けて、PCでrtklibで計算すればよいのかと思います。
* 上記課題として https://github.com/i386koba/CelluCon.RTK でやっていく予定です（2017.10時点）。

#### ホイールの回転計によるトレース精度向上。
* 移動距離はまぁ正確ですが、方向はスマフォの地磁気センサによる角度で、くるくる回るとすぐズレます。
* 方向陀サーボの角度と、両ホイールの回転計での回転差を計算して正確に位置を割り出すのが目的。
* GPSが取れない室内などでは有益です。
* 上記課題として https://github.com/i386koba/CelluCon.trace でやっていく予定です（2017.10時点）。

### 自動操縦
* 自動操縦はWeb画面のGoogleMapに軌跡を描くことで、その線をトレースする機能は作成しましたが、現在地がいまいちなので、いまいちの所からいまいちな所にしか移動できません。

### 携帯電話を空に飛ばすのは違法らしい。
* 引用元：総務省 – 電波利用ホームページ 4.よくある質問（Ｑ＆Ａ）http://www.tele.soumu.go.jp/j/sys/others/uav/
* 携帯電話等を無人航空機に搭載した試験を行いたいのですが、誰でも免許申請できますか。
* 実用化試験局の免許人は携帯電話等事業者となりますので、携帯電話等事業者以外は免許申請を行うことはできません。
* 携帯電話等事業者ってSORACOMとか入るんでしょうか。持ちかけてみるべきか？

### SkyWayの移行について
* 2013年12月よりトライアル提供をおこなっておりましたSkyWayを、さらなるニーズに応えるため2017年9月7日より商用サービスとして提供を開始しました。
* 商用提供に伴い、トライアル提供を行っておりました旧SkyWayは2018年3月をもってサービス終了予定です。
https://support.skyway.io/hc/ja/articles/115012252947-SkyWay%E6%AD%A3%E5%BC%8F%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E5%8C%96%E3%81%AE%E3%81%8A%E7%9F%A5%E3%82%89%E3%81%9B%E3%81%A8%E3%81%8A%E9%A1%98%E3%81%84
* とのことで、2018年3月以降、Skywayを商用利用してつづけるか、ほかの接続サービスにするか、接続サービスサーバーを立げるか未定（2017.10時点）です。

### 映像ライブ共有　
時雨堂 WebRTC SFU Sora 開発ログ　より
https://gist.github.com/voluntas/e914aa245fc26f3133c2#sfu
SFU は Selective Forwarding Unit の略で、簡単に言えば SFU というサーバが動画を配信者に変わって複数の視聴者に配信してくれる仕組みです。


### スマフォ（Java）PID制御、遠隔PIDパラメータチューニング
* スマフォの加速度センサを用いてBluetoothにつながっているサーボモーターをPID制御する。まずは倒立2輪車に挑戦中。
* スマフォセンサ情報はWeb画面のPCで取り込んで解析し、最適なPIDパラメーターを計算する仕組み。
* Web画面で解析したPIDパラメーターをスマフォのPID計算式に遠隔代入してパラメーターの最適値をリアルタイムで検証する。
* PIDのオートチューニングをやりやすくする仕組み。
* 上記課題として https://github.com/i386koba/CelluCon.PID でやっていく予定です（2017.10時点）。

### スマフォにPC側のカメラ映像を映してコミュニケート
* セルコンのスマフォに、Web画面PCのカメラ映像を表示すれば、自走式のテレビ電話（表現が古いですが…）ができます。
* もともとWebRTCが双方向なのですぐできます。
* 現状でもWeb画面PCの音声はセルコンのスマフォのスピーカーから音声出力できます。
* 音声出力はセラコンを不審に思う人に遠方から説明する機能としてつけましたが、よけい不気味で不審に思うと言われました。
* このテレビ電話の利用は室内が多いかと思いますのでGPS位置情報は期待できません。
* このためセンサトレース https://github.com/i386koba/CelluCon.trace の技術が必要かと。
* 上記課題として https://github.com/i386koba/CelluCon.Commu でやっていく予定です（2017.10時点）。

### 非アンドロイド化
* AndroidアプリをWebアプリに移行
* Cordova https://cordova.apache.org/ 
* BluetoothがCordovaプラグインはBLE対応のみのようなのでArduino基板のBLE化も必要。
* 上記課題として https://github.com/i386koba/CelluCon.WebApp でやっていく予定です（2017.10時点）。

### スマフォを使わない方法
* ふつうはラズパイとなりますが、HDMIいらないし、WebRTCが動くSBCならなんとか。
* 気になるSBC PINE64　http://akizukidenshi.com/catalog/g/gM-12067/
* LTE通信モジュール Soracom PCI Express Mini Card (LTE Cat.1) https://soracom.jp/products/ec21-j/ が安い。しかし5Mbps。
* http://momo.shiguredo.jp/  Momo があればブラウザがなくとも、比較的安価で手に入る Raspberry Pi 2 Model B (※1) と Web カメラを使って、WebRTC による映像の配信ができます 。
* 上記課題として https://github.com/i386koba/CelluCon.SBC でやっていく予定です（2017.10時点）。


## その他 
* 当初 Droid（Android-OS）+ drone (ドローン)　で　Droidrone　(ドロイドローン)としていましたが2017.10にセルコンに改名しました。
* CellでなくCelluとしたのはCellConという会社があったので。（けど cellucon という会社もありました）
* オープンソースとして多くの人が試験、実験しやすいようにドキュメントを充実させていきたいです。
* プロジェクト全体の雑多なことは[Wiki](https://github.com/cellucon/readme/wiki)に書いていきます。
