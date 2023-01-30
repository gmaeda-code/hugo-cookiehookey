---
title: "Windowsをインストールする"
date: 2023-01-30
categories: [Tech]
tags: [Hint,Scribble,Windows]
description: ""
draft: false
---

Linux系のOSを利用していて､Windowsのインストールメディア(USBメモリ)を作成することを想定する｡

## ISOを入手する
- https://www.microsoft.com/software-download/

上記サイトより､ISOを入手する｡


## USBメモリにコピー
linux系のOSみたいに､下記のようにddを使うことはできないようだ｡
```shell
dd if=path/to/gnu-linux-os-version-x86_64.iso of=/dev/sdx 
```

### woeusbを用いる
- https://github.com/WoeUSB/WoeUSB#run-from-source

OSのパッケージからインストールしてもいい｡
```shell
sudo woeusb --device /path/to/windows-image.iso /dev/sdX
```

これで､Windowsのインストールメディアは準備できたはずだ｡

## bootloaderからインストールメディアを読み込む
起動後にメーカーのロゴが出ているときに､delete,f12,f11,f10,esc,f1,f2,f3キーあたりを連打していれば､biosやuefiの画面に入る｡
後は､bootloaderから読み込むようにする｡

オフライン状態で､進めれば､Microsoftのアカウントを作成せずに利用できる｡


## telemetryをなくす
- https://www.geckoandfly.com/25083/free-tools-disable-stop-windows-spying-tracking-you/

Windowsにはtelemetryがデフォルトで有効になっているおり､突発的にかなりのリソースを食うことがある｡
それを防止するためには､上記リンクにあるようなツールが有効だろう｡

## プロダクトキーについて
Linux系のOS等をインストールした後でも､もともとWindowsが入っていた場合は､motherboardを交換していない限り､自動で認証されるようだ｡

Windowsがインストールされた状態で､プロダクトキーを知りたい場合は､コマンドから､もしくはregeditから確認できる｡
下記サイト参照: 
- https://www.techrepublic.com/article/3-simple-ways-to-find-your-windows-10-product-key/
