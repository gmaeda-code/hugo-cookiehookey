---
title: "Vimのキーバインドでブラウザを操作する"
date: 2022-11-27
categories: [Tech]
tags: [Geeky]
description: ""
draft: true
---

Vimのキーバインド､hjkl等でブラウジングする方法について､拡張機能を用いた方法を扱う｡


## vimキーバインドの拡張機能
参考:
- [Vim_key_bindings_for_web_browsers](https://vim.fandom.com/wiki/Vim_key_bindings_for_web_browsers)
- [vimperatorの代替](https://github.com/vimperator/vimperator-labs)

選択肢はいくつかある｡
- [tridactyl](https://github.com/tridactyl/tridactyl)
- [vimium](https://github.com/philc/vimium)
- [vimium-c](https://github.com/gdh1995/vimium-c)
- [surfingkeys](https://github.com/brookhong/Surfingkeys)
- [vim vixen](https://github.com/ueokande/vim-vixen)


## 印象
### tridactyl
他の拡張機能と比べても､多機能だが､その分ブラウザのいろいろな部分に影響がありそう｡
単純にキー操作をvimでしたいというだけなら､手に余るかも｡

### vimium,vimiumc
vimiumに機能を多くした版がvimium-cのようだ｡シンプルで使いやすいと感じる｡

### surfingkeys
一番自分には使い勝手があっているように感じた｡
例えば､visualモードで細かくテキストを選択するとき､他の拡張機能ではパラグラフごとなのだが､surfingkeysは単語ごとに選択できる｡
その他､入力formでもvimで操作できる｡

しかし､設定画面を開いたり､ことある毎にyoutubeやgoogleにアクセスしようとしていて､変な感じがする｡

設定からはリクエストのタイミング等の変更はできないので､ソースを変更しようとしたが､firefoxでは署名が有効でないと拡張機能を読み込んでくれない｡
署名をmozillaにしてもらうには､アカウント登録や認証が必要になる｡
署名なく利用するには､nightlyかdeveloper edition､もしくはESR?､最新のFFでも一時的ならdebugモードで使う必要がある｡
自由とセキュリティが相反する一つの例になった｡

手間がかかるので､この拡張機能は選択肢からは外した｡

### vim vixen
visualモードでテキストの選択とかはできない｡あと､esrでないと対応してないようだ｡選択からは外す｡


## まとめ
vimium-cあたりが使いやすそう｡機能を求めるならtridactylになるのかな｡


