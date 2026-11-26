---
title: "LINEがブラウザで使えなくなる"
date: 2026-11-25
categories: [Tech]
tags: [Error]
description: ""
draft: false
---

# 導入
ブラウザの拡張機能でメッセージアプリのLINEを使っていたが､最近ログインしたら､ブラウザで使えなくなる旨が表示された[^1]｡

対応方法についてのメモ｡

# linux環境での移行先
公式のヘルプセンターにも記述があるが､スマホ､デスクトップ､タブレットのアプリが選択肢として挙げられる｡[^1]
つまり､ブラウザではなく､ネイティブアプリを使うことになる｡

私の場合､linuxのPCで引き続き利用したいので､windowsのデスクトップ用アプリをインストールする｡

# linux環境でwindowsソフトを使う
一般に､VMを用いずに､windowsのソフトをlinux環境で使う場合､wineが有名である｡

その他､ベースは共通するが､wine､bottles､steamのprotonでも同様に利用できるようだ｡

私は､最近は､flatpakでbottlesをインストールして使っている｡

細かいbottlesの使い方は検索してもらえればいろいろでてくる[(例えば)](https://tanoike.com/how-to-install-windows-soft-on-linux-using-bottles)｡

# DLL署名のエラー
LINE公式サイトからexeファイルをダウンロードして､bottlesからインストールする｡
しかし､起動すると､signature関連のエラーが出た(エラー文面は忘れた)｡

signature関連のエラー対応については､以下のサイトを参考にさせてもらった｡

- [HyprlandにLINEをインストールする](https://zenn.dev/snacy/articles/1d78d767a13d3a)
- [【Linux / Steam Deck】Wine・Bottles環境でWindows版LINEを動作させる方法（署名エラー回避スクリプト付き）](https://181bit.blogspot.com/2026/09/linux-steam-deckwinebottleswindowsline.html)


[^1]: https://help.line.me/line/smartphone?contentId=200001456
