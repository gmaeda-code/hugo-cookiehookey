---
title: "固定デバイス名を設定する"
date: 2026-07-21
categories: [Tech]
description: ""
draft: false
---

## 問題点
デバイスは､差し込む順番により､/dev/input/下において､event0になったり､event1になったりと名称が変わる｡
キーバインドを変更する際､指定先のデバイス名が変わってしまうと適用されない｡

## 解決方針
udevを用いて､参照先をエイリアスという形式で固定できるようにする｡
具体的には､/etc/udev/rules.d/下にudevルールを記載したファイルを作成することで固定する｡

## 解決ステップ
参照したいデバイスの情報を集める

### evtestコマンドで､udevルールに必要なデバイスのパスを取得する

evtestコマンドでエイリアス設定をしたいデバイスのパスを取得します｡

```bash
$ evtest
No device specified, trying to scan all of /dev/input/event*
Not running as root, no devices may be available.
Available devices:
/dev/input/event0:	AT Translated Set 2 keyboard
/dev/input/event1:	Video Bus
/dev/input/event2:	ETPS/2 Elantech Touchpad
/dev/input/event3:	ELECOM ELECOM BlueLED Mouse
/dev/input/event4:	ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard
/dev/input/event5:	ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard Mouse
/dev/input/event6:	ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard System Control
/dev/input/event7:	ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard Consumer Control
/dev/input/event8:	ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard
/dev/input/event9:	ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard Keypad
〜省略〜
Select the device event number [0-30]:
```

ここでは､下記デバイスを固定したいものとします｡

`/dev/input/event4:	ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard`

このままでは､毎回デバイスのパス､つまりevent4が変わり得ます｡

### udevadmコマンドで､デバイス情報を取得する

先程取得した固定したいデバイスのパスを用いて､そのデバイス情報をudevadmコマンドで取得します｡

```bash
udevadm info -a -n /dev/input/event4
ATTRS{phys}=="usb-0000:03:00.3-3.4/input0"
ATTRS{name}=="ADATA Technology Co., Ltd XPG Summoner Gaming Keyboar
d"
〜省略〜
```

指定したパスにあるデバイス情報が一覧で出ます｡
同じ名称のデイバイスがなければ､名前(name)だけでも指定できます｡
今回は､先程のevtestの出力の通り､同じデバイス名があるので､別の情報(phys)も用いて､絞ります｡


### udevルールの記述

/etc/udev/rules.d/下に､udevルールを記述したファイルを用意します｡

```bash
$ pwd
/etc/udev/rules.d

$ ls -l
-rw-r--r-- 1 root root  761 Jun 19 16:06 99-input-custom.rules

$ cat 99-input-custom.rules
SUBSYSTEM=="input", ATTRS{name}=="ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard", ATTRS{phys}=="usb-0000:03:00.3-3.4/input0", SYMLINK+="input/event-keyboard1"
```

ルールを記述したら､リロードのため､下記を実行します

```bash
$ sudo udevadm control --reload-rules && sudo udevadm trigger
# もしくは下記コマンド
$ sudo udevadm control --reload && sudo udevadm trigger --action=add

```
その後､エイリアスで固定したデバイス(udevルール内のSYMLINK+=で指定したデバイス名)が表示されるか確認します｡

```bash
$ evtest
No device specified, trying to scan all of /dev/input/event*
Not running as root, no devices may be available.
Available devices:
/dev/input/event-keyboard1:	ADATA Technology Co., Ltd XPG Summoner Gaming Keyboard
〜省略〜

```
表示されていれば､参照先のデバイスを､指定したデバイス名(event-keyboard1)にすることができます｡

### その他の方法
lsusbコマンドを用いて､デバイス情報(ベンダーID､プロダクトID)を取得する方法もあるみたいです｡


## 参考にしたサイト
- https://zenn.dev/karaage0703/articles/d6759ea297dbf8
- https://get.vial.today/manual/linux-udev.html
