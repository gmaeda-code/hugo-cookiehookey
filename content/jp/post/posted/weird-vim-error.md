---
title: "vimの奇妙なエラー"
date: 2024-07-06
categories: [Tech]
tags: [Error]
description: ""
draft: false
---
nvimでファイルを編集をしようとすると､swapファイルを作成できない､というような一見よくわからないエラーが出たことがあった｡

## 奇妙なエラー

```bash
#aaaaa~aaaaは開こうとした任意のファイル
E303: Unable to open swap file for "aaaaa~aaaa", recovery impossible 
```
普通のテキストファイルなのに開けない｡
ファイルのpermissionは問題なし｡
swapディレクトリの指定も問題なし｡
他のファイルであればnvimで開ける｡
不思議なことに､開けなかったファイルを他のパスに移動させると開ける｡

## 原因

結局は､ファイルの名前が長すぎたことが原因だった｡
直接touchで長い名前のファイルを作ろうとすると明確なエラーが出るのだが､nvimだと名前が長いことを指摘してくれない｡
```bash
touch "aaaaa~aaaa"              
touch: cannot touch 'aaaaa~aaaa': Filename too long
```

swapファイルは､パスを含めるため､パスによりswapファイル名は長くなったり､短くなったりする｡
その関係で､このパスだと開けるし､別のパスでは開けないということが起こったようだ｡

ちなみに､もともとのファイル自体はwindowsで作成していた｡
OSによって対応できるファイル名の上限は違うので､windowsでは開けても､linuxでは開けないということだったらしい｡


## 参照
- [linuxにおけるファイル名の長さの上限](https://www.ubuntumint.com/find-limit-file-name-length-linux/)

