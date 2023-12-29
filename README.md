# mypkg
千葉工業大学未来ロボティクス学科の2023年度ロボットシステム学の練習用リポジトリである.

![test](https://github.com/kohsei-ta/mypkg/actions/workflows/test.yml/badge.svg)

## インストール法

* クローン

当リポジトリをインストールしたい任意のディレクトリで操作する.
```
$ git clone https://github.com/kohsei-ta/mypkg.git
```

* インストールの確認
```
$ ls
```

ディレクトリに`mypkg`が存在していればOK.

次に`mypkg`の中にファイルが存在するかを確認する.
```
$ cd mypkg
$ ls
```
```
mypkg  package.xml  resource  setup.cfg  setup.py  test
```
上記のようになっていればOK.

# 機能説明と実行

## talker
* 機能

0.5秒おきに数字をカウントし、トピック/countupを通じて送信する.

* 実行

```
$ ros2 run mypkg talker 
```
下には何も表示されない.

* 別端末でros2のサブスクライブ

別の端末を開き以下を実行する.
```
$ ros2 topic echo /countup
```

* 結果

```
data: 50
---
data: 51
---
・・・
```

## listener

* 機能

/countupからメッセージを受け取り表示する.

* 実行と結果

listenerの実行とその結果は次の「talkerとlistenerの動作確認」にある.

## talkerとlistenerの動作確認

* talkerの実行

一つ目の端末で以下を実行する.
```
$ ros2 run mypkg talker
```

* listenerの実行

別の端末を開き以下を実行する.
```
$ ros2 run mypkg listener
```

* 結果

```
[INFO] [1703485802.104979021] [listener]: Listen: 20
[INFO] [1703485802.592628904] [listener]: Listen: 21
[INFO] [1703485803.094116753] [listener]: Listen: 22
・・・
```

## ローンチファイルの実行と結果

launchファイルを使用することで、talkerとlistenerの実行を同時に行うことができる.

* 実行
```
$ ros2 launch mypkg talk_listen.launch.py
```
* 結果
```
[INFO] [launch]: All log files can be found below /home/...
[INFO] [launch]: Default logging verbosity is set to INFO
[INFO] [talker-1]: process started with pid [974]
[INFO] [listener-2]: process started with pid [976]
[listener-2] [INFO] [1703574542.456174715] [listener]: Listen: 0
[listener-2] [INFO] [1703574542.943050229] [listener]: Listen: 1
[listener-2] [INFO] [1703574543.442637826] [listener]: Listen: 2
・・・
```

# 必要なソフトウェア
* Python
  * テスト済み:3.10
* ROS2 Humble

# テスト環境
* Ubuntu 22.04.2 LST

# ライセンス
* このソフトウェアパッケージは，3条項BSDライセンスの下，再頒布および使用が許可されます.
* このパッケージのコードは，下記のスライド（CC-BY-SA 4.0 by RyuichiUeda)のものを，本人の許可を得て自身の著作としたものです.
    * [ryuichiueda/my_slides/robosys_2022](https://github.com/ryuichiueda/my_slides/tree/master/robosys_2022)
* © 2023 Kohsei Takaoka
