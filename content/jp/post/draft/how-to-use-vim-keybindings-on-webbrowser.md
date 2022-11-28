---
title: "Vimのキーバインドでブラウザを操作する"
date: 2022-11-27
categories: [Misc]
tags: [Think]
description: ""
draft: true
---

browser-vim

https://vim.fandom.com/wiki/Vim_key_bindings_for_web_browsers
#list
- tridactyl
- vimium(vimium-ff)
- surfingkeys
- vim vixen

#利用後の選択肢
- tridactyl
- vimium-ff
	- vimiumc?

#利用してみて
## tridactyl
FF全体を変えようとする?ので､サイトによっては衝突があったり､マウスが効かないことがある?ようだ｡
only ff
特には､問題(クラッシュ等)はなさそう｡
設定により､mozillaのページでも行けるよう｡デフォルトで回避策(脱出作みたいなの)はある｡
navigation,ignore,hint,command,visual等のモードがある｡
visual modeはパラグラフ単位で､マークアップがあればフォーカスされるようだ｡
www.google-analytics.comが起動する?
テキストの選択がしにくい､caretがffのデフォルトを想定しているようで切り替え･操作が不便
サーチはありだが､日本語入力を組み合わせると複雑になる｡

## vimium-ff
チートシートによくまとまっている
visual modeがターゲットを定めるような感じではなく､逐次的｡基本はsearchする形になるのだろう｡searchしてからのyankはできる｡
## vimiumc
これは､テレメトリみたいのはなさそうだ｡
基本的には､vimium-ffに機能が増したもののイメージ｡visualモードで選択がしやすいように拡張できる｡
searchで検索すにも､日本語に切り替えてとかやると面倒くさそう｡位置を先に固定できたほうがいい｡

#避けるもの
##surfingkeys
細かな単位でvisualモードが見られる｡単語単位｡
デフォルトの挙動で､設定画面を開くとyoutubeとgoogleにアクセスするようになっている感じで､怪しい?
insert modeという形で､vim的な動きをできるようにしている
かなり､シンプルかつ高機能に感じる｡
感触自体は､これが良さそう
youtube.com,google.comが起動する
高機能ではあるが､youtube,googleにクエリが行く

## vim vixen
ドキュメントの説明は､簡潔
visual､,テキストの選択はできない｡
navigation､hint,commandモードはある｡##google-analyticsに関しては
サイトにより､白枠が表示されたりする｡github,esrしか対応してないのでしょうがない感じ｡addonsのサイトが､特権ページでextensionができないのに対し､analyticsを仕掛けているから防げていないということだった｡
脱出装置はない｡FF自体のショートカットを合わせれば､十分と言えそう｡
hintモードでも､少し､遷移の選択がうまくできてなさそうなところがある｡
特に大きな問題はなさそう
検索等もうまくできず､あまり互換性がないかな?
compatibility with older ff 78esr
only ff
更新が1年前くらい

