---
title: "入力の効率化"
date: 2023-07-22
categories: [Tech]
tags: [Hint, Keyboard]
description: ""
draft: false
---

キーボード配列､キーバインドといったPC入力の効率化について触れようと思う｡

## キーボードレイアウトを効率化
### 直接入力
日本ではqwertyが主流となっているが､PCになった現在ではデフォルトであるということ以外に特にメリットはないように思う｡
入力の効率を重視したレイアウトには､dvorakを始め､colemak､workmanなど種々存在するので､自分にあったものに変えるとだいぶ楽になる｡

私の場合､qwertyからdvorakに変更することで､多少入力は速くなった｡
ただ､どちらかというと入力が楽､疲れにくいという方が実感に近い｡

### 日本語入力
日本語入力においては､ローマ字入力以外には､かな入力や親指シフトなどが有名どころとして挙げられる｡
かな入力はqwertyのローマ字入力と比べても､指を大きく動かす必要があるため､速度は出ても､疲れやすい｡
親指シフトは､ローマ字入力の順打鍵に対し､同時打鍵であるため､だいぶ癖がある印象だ｡

私は､同時打鍵の新下駄配列(中指シフト)をしばらく試したことがあったが､順打鍵の方があっていると感じた｡
単純にdvorakのローマ字入力にするだけでも､日本語入力は､楽に速くなる｡
今では､dvorakベースの[jlod](https://www.mikage.to/jlod/)を利用している｡

### 実現方法
#### windowsの場合
[dvorakj](https://blechmusik.xii.jp/dvorakj/)というソフトがある｡

#### linuxの場合
guiなら､設定のキーボードレイアウトあたりから変更できると思う｡
cliの場合､`setxkbmap dvorak`と入力する｡

日本語入力を直接入力とは別(jlodなど)にする場合は､IME(fcitx5のmozcなど)で､ローマ字表を設定するか､インポートする｡
[nlod](https://gothub.no-logs.com/ncaq/nlod)というjlodから更に改変された配列のデータはネットにあった｡

## キーバインド
ここまでで､文字入力の効率化について触れた｡
次は､キーボード操作を効率化する方法について扱う｡

入力に対して､出力を変えると楽に操作できる｡
例えば､次のようにすると､手を移動させずにカーソル移動できる｡
```
    無変換+s:←
    無変換+d:↓
    無変換+f:→
    無変換+e:↑
```

さらに､SandSを設定すれば､shiftキーを小指で押さずに済む｡
```
    space単体: space
    space+文字: 大文字
```

その他capslockをcontrolキーにしたり､vimユーザーならcaps単体をescにするなどのノウハウがある｡

キーバインドを実現する方法によってできることには制限があるが､下記のようにいろいろ組み合わせて効率化できる｡
- 単体のときの出力
- 長押しのときの出力
- 他のキーと複合のときの出力

### 実現方法
#### windows
[autohotkey](https://www.autohotkey.com/)を用いる｡先程のdvorakjもautohotkeyのスクリプトだ｡
ちなみに[mousegestureL](https://hp.vector.co.jp/authors/VA018351/mglahk.html)は､autohotkeyをマウスにまで拡張していて､マウスのカーソル操作も効率化できる｡

#### linux
[xkeysnail](https://gothub.no-logs.com/mooz/xkeysnail)や[input-remapper](https://gothub.no-logs.com/sezanzeb/input-remapper)､[kmonad](https://gothub.no-logs.com/david-janssen/kmonad)などがある｡
xmodmapやxcapeは､authotkeyに比べると機能が限定的に感じる｡
マウス操作に関しては､easystrokeがあるにはあるが､xorg関連?のエラーが出て､使えなかった｡

## まとめ
直接入力､日本語入力､キーバインディングを変えることで入力を効率化について暑かった｡
その他､IMEやWindow managerのショートカット､ブラウザの拡張機能などを組み合わせるとより操作しやすくなるだろう｡






