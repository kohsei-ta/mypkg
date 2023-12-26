# mypkg
千葉工業大学未来ロボティクス学科の2023年度ロボットシステム学の練習用リポジトリです.

## インストール法

* クローン

当リポジトリをインストールしたい任意のディレクトリで操作していく.
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

## 実行とメッセージの確認

* ros2 runで実行

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

## talkerとlistenerの動作確認

* talkerの実行

一つ目の端末で以下を実行する.
```
$ ros2 run mypkg talker
```

別の端末を開き以下を実行する.
```
$ ros2 run mypkg talker
```

* 結果

```
[INFO] [1703485802.104979021] [listener]: Listen: 20
[INFO] [1703485802.592628904] [listener]: Listen: 21
[INFO] [1703485803.094116753] [listener]: Listen: 22
・・・
```

## ローンチファイルの実行

```
$ ros2 launch mypkg talk_listen.launch.py
```
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

## testコマンド

以下のコマンドで'test'というディレクトリに移動する.
```
$ cd test
```

10秒間ノードを実行し、listenerが出力するべき行を探すというもの.
```
$ ./test.bash
```
```
(略)
Summary: 2 packages finished [1.63s]
  1 package had stderr output: mypkg
[listener-2] [INFO] [1703575077.713144188] [listener]: Listen: 10
```

# 必要なソフトウェア
* Python

# テスト環境
* Ubuntu 22.04.2 LST

# ライセンス
* このソフトウェアパッケージは，3条項BSDライセンスの下，再頒布および使用が許可されます.
* このパッケージのコードは，下記のスライド（CC-BY-SA 4.0 by RyuichiUeda)のものを，本人の許可を得て自身の著作としたものです.
    * [ryuichiueda/my_slides/robosys_2022](https://github.com/ryuichiueda/my_slides/tree/master/robosys_2022)
* © 2023 Kohsei Takaoka
