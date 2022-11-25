---
title: "スマホとプライバシー1(問題の所在)"
date: 2022-05-22
lastmod: 2022-07-13
categories: [Tech]
tags: [Privacy,Mobile]
description: ""
draft: false
---

スマホには脆弱性があり､そ1れがプライバシー上の懸念事項となる｡スマホに脆弱性があることは､今までに何回か触れた｡[ファームウェアがクローズドソースであること](https://cookiehookey.neocities.org/why-do-we-have-to-buy-a-new-phone/)や､
[電話回線のSS7という通信プロトコル](https://cookiehookey.neocities.org/why-not-stop-using-sms-as-2fa/) だったり､
[やたらとBluetoothをONにするOS](https://cookiehookey.neocities.org/everytime-updating-ios-bluetooth-turns-on/) など｡今回は､それら脆弱性をスマホのプライバシーという文脈で整理しようと思う｡

まず第1章で､プライバシーの定義について考え､続く第2章で､スマホとプライバシーの関係性･イメージついて掴めるようにする(ほぼリンク)｡第3章では､なぜスマホが問題になるかについて説明する｡第4章は､第5章の前提知識として､スマホの構造について軽く触れる｡第5章がメインで､脆弱性を階層ごとに列挙している｡第6章はまとめというかコメントだ｡

今後､文章中の参照リンクは､適宜｢🔗｣で表記する｡

## プライバシーとはなにか
[別ページ参照](https://cookiehookey.neocities.org/the-definition-of-privacy/)



## スマホとプライバシーって?

プライバシー自体については､何となくイメージができただろう｡しかし､スマホとプライバシーの関連性は?というと､いまいちピンとこないかもしれない｡その場合には､以下のサイトが参考になる｡概要と言うには少し長いが､包括的に触れているサイトだ｡この先こうした情報源を参照しつつ考えていくので､今すぐ見る必要はない｡ただ､最初の動画はイメージを掴むには役立つと思う｡

- [【動画】概要:デバイス上で操作できることは遠隔でも操作できる｡](https://invidious.snopyta.org/watch?v=0dGqR4ue8dg)
- [スマホの脆弱性について(項目別に時系列で紹介)](https://www.gnu.org/proprietary/malware-mobiles.html)
- [スマホと､それを取り巻く業界まで含めた､脆弱性に関する論文](https://www.researchgate.net/publication/302065591_SoK_Privacy_on_Mobile_Devices_-_It%27s_Complicated/fulltext/572fa0fe08ae3736095c1d3f/SoK-Privacy-on-Mobile-Devices-Its-Complicated.pdf)
- [スマホのハードウェアや仕組みに関する脆弱性](https://restoreprivacy.com/controlling-communication-channels/)



## なぜスマホが問題になるのか

コンピューターという点では､LaptopやDesktopも同様に脆弱性にはさらされているはず｡では､なぜスマホを焦点に当てるのか? それは､スマホがとりわけSensitiveだからだ｡なぜか｡理由はスマホの特性とスマホのユーザー層にある｡

### スマホの特性

以下のような特徴から､DesktopやLaptop､単純な家電製品とも違うスマホ独特のプライバシー上の懸念が生じる｡

#### インターフェイスの違い

機能が豊富で､センサーが多種多様である｡そのおかげで､現在地を正確に把握できたり､指紋でロック解除できたり｡画面をタップで操作することができたりする｡外部機器を用意しないでもビデオ通話ができたりする一方で､センサーが一緒になっているので取り外せない｡

#### 常に持ち歩く

スマホの多機能さと持ち運び易さが相まって､常に持ち歩く｡必要性がなくても､外出する際に忘れたら､わざわざ家に取りに帰る｡異世界に転生してもなお､持ち歩く人がいるらしい｡Laptopも持ち運べるが､スマホほどの携帯性はない｡

#### 常に電源を入れている

Desktop, Laptopでも､特にサーバーであれば常に電源が入っているだろう｡スマホは連絡ツールとして機能することもあり､大抵の場合､常に電源は入っているし､それがcommon senseとなっている｡センサーが豊富で､常に持ち歩き､常に電源が入っている｡仮に､それを管理する方法を知らない(orない)としたら? 危ういだろう｡

#### 収益モデルの違い

スマホの収益モデルは､従来のデバイスとはアプローチが異なる｡ハードウェアや､ソフトウェア､サービスを販売して対価を得る仕組みとは違って広告を収益モデルとしていることが多い｡これまでに述べたスマホの特性と､それ以外の要素も含め､トラッキングにはうってつけのデバイスとなっている｡特にターゲティング広告を行っている業者にはスマホは人気で､ユーザーの情報が第2の通貨として機能している｡大抵の場合､利用者は､いつのまにかトラッキングに同意している｡

こうした背景も相まって､スマホ業界はCash cow(儲かるビジネス)となり､PCや電化製品よりも開発が活発に行われている｡これからも､スマホとそれを取り巻く環境は､プライバシー的な懸念は今まで通り二の次にして､急速な変化を遂げていくだろう｡


### スマホのユーザー層

今までのコンピューターには比類しないほど､スマホはトラッキングには最適と言える｡一方で､スマホ利用者の大半は､コンピューターについての知識や仕組みに対しての理解が不足してるように感じる｡DesktopやLaptopを経由してスマホを利用している人は､ある程度知識があるかもしれないが､特にいきなりスマホから入った人はデジタルリテラシーに不足するところがあるだろう｡極端に言えば､守る術を知らない人が､トラッキングツールを持っているようなものだ｡危うい｡これが､(デジタル)プライバシーを語る上で､スマホに焦点を当てる理由だ｡


### 表にまとめてみると(イメージ)


|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
|     | センサー | 持ち運び | 常時電源 | 広告収益 | リテラシー不足 |
| 電化製品 | -   | ?   | -   | -   | -   |
| Desktop | -   | -   | -   | ?   | ?   |
| Laptop | -   | ?   | -   | ?   | ?   |
| スマホ | ✔   | ✔   | ✔   | ✔   | ✔   |


```
Legend:
 - : なし(ほぼなし)
 ? : 物や使い方によるところが大きい
 ✔ : 大いに当てはまる
```

## スマホの構造･階層

前章で､スマホを取り上げる理由は説明したが､そのスマホの脆弱性を語るには､仕組みの理解していた方がわかりやすい｡ここでは､スマホがどの様な構造で成り立っているかというところについて､一応触れておく｡

### ハードウェアの構造

![hardware](/img/hardware.png)
https://replicant.us/freedom-privacy-security-issues.php
より｡

上図は､スマホのハードウェアの簡略図で､SoC(System On a Chip)というところを中心として各コンポーネントが存在していることを表している｡Modem(BP:Baseband Processor､Baseband modemとも言う)が､モバイル回線を受信する｡SoC[(🔗)](https://wikiless.org/wiki/System_on_a_chip?lang=en)は､PCで言えばマザーボードにあたるが､この回路に周辺パーツが集まっている｡図で言えば､RAMやストレージ､その他のコンポーネント(GPSとかカメラ､マイクetc)が取り付けられている｡

### スマホの階層

![abstraction-of-the-components](/img/abstraction-of-the-components.png)
[SoK-Privacy-on-Mobile-Devices-Its-Complicated](https://www.researchgate.net/publication/302065591_SoK_Privacy_on_Mobile_Devices_-_It%27s_Complicated/fulltext/572fa0fe08ae3736095c1d3f/SoK-Privacy-on-Mobile-Devices-Its-Complicated.pdf)のFig. 1より

図は､各階層の要素を示している｡ユーザーの入出力(操作)が一番表層にあり､深層にハードウェアがある｡


## 脆弱性の存在

この章から､スマホに内在する脆弱性について取り上げていく｡
最初の導入部分の後は､Webレベルの脆弱性に触れ､次にスマホの階層で言うところのアプリレベルから深層のハードウェアへと向かって行く｡そして､デバイスを飛び出して､通信キャリアなどのスマホを取り巻く環境について言及する｡

### スマホを所有することはできない｡

ユーザーの知らぬところで､物事･プロセスは進んでいる｡使うという主体ではなく､使われるという客体の意味でユーザーという用語が存在する｡現状､ユーザーはデータ収集に利用されているだけのようにも感じられる｡データ収集に協力した見返りに､一部キャッシュバックでも貰えれば満足なのかも知れないが､そもそも何が起こっているのか知らない場合も多そうだ｡

人間は感じ取れるものだけが存在していると思いこむ｡例えば､Alexaが勝手に音楽を流したとしたら､どう思うだろう｡そういうバグだと思うかも知れない｡しかし､もしかしたら人間には聞き取れない高周波で音声的に命令が下されたのかも知れない｡聞き取れないのだから､耳が塞がれた状態で誰かが操作しているのと同じ状況だ｡スマホではそうした状況が起こっている｡ソースコードを見ることができるというのも一つの感覚器官のようなものだが､スマホではその感覚器官が塞がれている事が多い｡そのため､問題があるかどうかも知覚できないし､考えることもできない｡何が行われていても気が付かないことが大半だ｡

感覚器官という点では､無線も同様のことが言える｡ケーブルと違って見えないため本当にOFFなのかは確かめられない｡OFFのふりをしてONということもある[(🔗)](https://arstechnica.com/information-technology/2022/05/researchers-devise-iphone-malware-that-runs-even-when-device-is-turned-off/)｡
LANケーブルの場合だったら､抜けばいいとなる｡電源を落としたければ､バッテリーパックを取り外せばいいとなる｡でもスマホでそれができるだろうか? 電源も落とせず､無線をOFFにできない｡というより､OFFなのかわからない｡

とりわけハードウェアは､一筋縄では解消できない問題が多い｡例えば､各コンポーネントがそれぞれのパーティーで作られているというところからも､複雑性が生まれる｡1つのコンポーネントの脆弱性が､それ単体では問題ない別のコンポーネントの脆弱性を引き出すということもある[(🔗)](https://www.researchgate.net/publication/302065591_SoK_Privacy_on_Mobile_Devices_-_It%27s_Complicated/fulltext/572fa0fe08ae3736095c1d3f/SoK-Privacy-on-Mobile-Devices-Its-Complicated.pdf)｡

何が起こっているか分からないもの､コントロールできないものを所有していると言えるのだろうか｡高度に複雑化､プロプライエタリという形でブラックボックス化されたものは､購入したからと言って､所有したことにはならない｡スマホは謳う"You don't own me"と｡だとすると､スマホは誰のもの? という疑問が湧いてくるのも不思議ではない｡


### Webレベル

WEBレベルに関しては､Desktop､Laptopと共通するので､同様の脆弱性がある｡同じ脆弱性にさらされる割には､DNSフィルタリング含め､APIがOSによって規制されていることもあり､PCと比較すると対抗手段が限られる｡

他方､WEBサービス上には､あらゆる方向からトラッキングを試みる組織がいる｡Facebookは､カメラの傷のパターンから､フィンガープリントをするようなパテントを取っていたり､なにそれと思うようなトラッキングの発想がたくさんある｡

その他のプライバシーに関連するであろうWeb技術や慣習は色々あるが､スマホに限った話ではないので詳細は割愛する｡

一例)

- browser fingerprinting(ブラウザの肥大化が原因)
- Webビーコン
- hyperlink auditing
- cname cloaked tracker
- JS([リンク先をon clickで変更する](https://cookiehookey.neocities.org/rakuten-link-redirect/)､3rd Partyリソース(コントロールができてない) etc)
- CDN([SSLはどこいった](https://community.cloudflare.com/t/does-cloudflare-proxy-servers-decrypt-my-data/145691)､[SSLのkeyは誰のもの?](https://community.cloudflare.com/t/cloudflare-private-key-for-ssl-certificate/96475) etc)
- Respect your privacyと言うものの､Protectはしないマーケティング重視のWebサービス(プライバシー重視ならオプトイン)
- reCAPTCHA

### アプリレベル

アプリやサービスがオープンソースでない､フリーソフトウェアでない場合､まずデータを収集していると考えたほうがいい｡広告用のライブラリが充実しているため､大抵は3rd partyライブラリが入っている｡1st partyと同等の権限を所有するため､情報が横流しされているのと同じようなもの｡そうしたデータを狙って､3rt partyライブラリを専門で開発する人たちもいて､多くの開発者はそのライブラリを利用する[(🔗)](https://www.researchgate.net/publication/302065591_SoK_Privacy_on_Mobile_Devices_-_It%27s_Complicated/fulltext/572fa0fe08ae3736095c1d3f/SoK-Privacy-on-Mobile-Devices-Its-Complicated.pdf)｡

- OEMによっては､Facebookなどプライバシー上懸念のあるアプリ(bloatware)が､プリインストールされる一方､消せないようにされている｡

- アプリは､ロケーション情報などをやたらとトラッキングするが､入手した情報がどう使われるかは管理できない[(🔗)](https://www.nytimes.com/interactive/2018/12/10/business/location-data-privacy-apps.html)｡
個人情報には結びつかないという主張もあるが､生データにアクセスすることで､特定することもできる｡

- Gogleプレイストアのアプリが､マルウェアを含むコードをダウンロードをできた｡プロプライエタリだからこそできた例といえる｡フリーでない場合のリクスがある[(🔗)](https://www.gnu.org/proprietary/malware-mobiles.html#M201908270)｡
フリーでないために､知らぬ間に悪用されていることには事欠かない｡

- パーミッションをバイパスするアプリ｡OSが安心だとしても､アプリ自体の問題もある｡アクセス権のあるアプリを媒介する[(🔗)](https://www.gnu.org/proprietary/malware-mobiles.html#deception)｡

- Wifiネットワークの許可を通じて､ルーターのMACアドレスから位置情報にアクセスする[(🔗)](https://nakedsecurity.sophos.com/2019/07/10/android-apps-sidestepping-permissions-to-access-sensitive-data/)｡

- アプリでは､SSLのエラーの警告が出ないという話も聞く､オープンソースであれば確認はできるのだろうが｡

#### "プライバシーを重視する"は売り文句

これは､次のシステムレベルにも共通することだが､プライバシーを重視しますという主張は大抵の場合､ユーザー視点ではない｡例えば､Braveというブラウザは､トラッキングをブロックするが､特定のサイト(提携企業?)はホワイトリスト化されている｡

iOSはアプリをストアに出す際には､審査を受ける仕組みがある｡iOSが許可するAPIには､PublicとPrivateがあるが､Private APIはユーザー情報に密接に関わるため､審査は通らない｡そもそも公式にドキュメントされていないAPIである｡しかし､Enterprise accountで契約をすれば､審査プロセスがなくなる｡つまり､Private APIが使いたい放題になる裏ルートのようなものがある[(🔗)](https://www.researchgate.net/publication/302065591_SoK_Privacy_on_Mobile_Devices_-_It's_Complicated/fulltext/572fa0fe08ae3736095c1d3f/SoK-Privacy-on-Mobile-Devices-Its-Complicated.pdf)｡

最近のプライバシービジネスというのは､外からのプライバシーには守ります｡でも､中からは侵食しますといったものが多い｡第三者をはねのけ､広告やトラッキングを独占するための売り文句になっている｡お金を払って提携すれば例外に加えてもらえる｡その一方で､トラッキングから守るための正当な道具(DNSフィルタリングのAPI)は規制される｡


#### クローズドソースのリスク

大抵のアプリはクローズドソースであるが､大手だから安心!とはいかない｡Whatsupでは､電話をかけるだけで､相手が電話にでなくてもマルウェアを送り込み､デバイスからデータを盗み取れる脆弱性があった[(🔗)](https://www.nytimes.com/2019/05/13/technology/nso-group-whatsapp-spying.html)｡

プライバシーの観点からE2EEは重要ではあるが､E2EE=安心とはならない｡クローズドソースでは､何の暗号化方式か､強度はどうか､暗号化キーの保存場所はどこか､どのタイミングで暗号化するかといったことはわからない｡暗号化していると言いつつ､デフォルトのクラウドバックアップ先には平文で保存されることもある[(🔗)](https://www.wired.com/story/encrypted-messaging-isnt-magic/)｡
オープンで[reproducible](https://reproducible-builds.org/)でもない限り､セキュリティシアターで終わるのが落ちだ｡

暗号化方式として､IBMやFacebookといった広告企業が､凖同型暗号の開発に力を入れているのは興味深い[(🔗)](https://adguard.com/ja/blog/homomorphic-encryption-era.html)｡
セキュリティ上のメリットはあっても､プライバシー上は懸念事項になる[(🔗)](https://www.immuta.com/articles/homomorphic-encryption-alone-is-security-not-privacy/)｡
マーケティングというのは､マジックのようなもので､欠点から目をそらし利点にばかり目を向けされる｡そして､いつの間にかそれを望み始めている｡実に見事だ｡E2EEで暗号化しているのでセキュリティ上安心ですよと主張することで､プライバシーからは目をそらさせる｡凖同型暗号を広告企業が使うことは､プライバシー上は､単なるミスディレクションでしかない｡




### システムレベル

アプリレベルでも触れたが､アプリのAPIはOSに握られている｡アプリが何を行っているか､どこに通信しているかは､一部の人(テクノロジーの仕組みを知る人たち)にしかわからない｡しかし､DNSクエリを見たとしてもAPIが制限されているために､すべては見れない､わからない｡そしてわからないうちにデータを取られている｡

アプリにはそれぞれ､パーミッションやサンドボックス化等の仕組みがあるが､バイパスできたり､ざるなところがある｡

クローズドソースのアプリが多いということは､どう動作するかの確証が得られないということだ｡にもかかわらず､システム側でパーミッションの管理が柔軟にできない点があるが､それは意図的なのだろうか?

iOSとAndroidが寡占しているため､パッケージの管理方法や設計､決定には､従うしかない｡


### ハードウェアレベル

以前にも触れたが､ハードウェアも同様にクローズドソースであり､システムレベルと違い､オープンソースへの書き換えは困難である｡ローレベルであるため､ユーザーは気づかれずに(遠隔)操作され得る｡

#### 各レベル･各コンポーネントのアクセス範囲

各コンポーネントは､それぞれの領域にアクセス権を持っている｡他のコンポーネントを経由することで､表よりは広くアクセスできる｡

![SoK_Privacy_on_Mobile_Devices_Table_1](/img/SoK_Privacy_on_Mobile_Devices_Table_1.png)
[SoK: Privacy on Mobile Devices – It’s Complicated](https://www.researchgate.net/publication/302065591_SoK_Privacy_on_Mobile_Devices_-_It%27s_Complicated/fulltext/572fa0fe08ae3736095c1d3f/SoK-Privacy-on-Mobile-Devices-Its-Complicated.pdf)のTable1より｡


#### 2つ目のOS

Baseband modem含めハードウェアには､ファームウェアが含まれている｡ファームウェアはAP(Application Processor,Main Processor, CPU)上では実行されず､コンポーネントのRAM･プロセッサーで実行されるため､Main processorとは別のコンピューターが動いていることを意味する[(🔗)](https://www.osnews.com/story/27416/the-second-operating-system-hiding-in-every-mobile-phone/)｡
普通にOSを入れて動かせるため､modemにLinuxOSを走らせてホスティングすることもできる[(🔗)](https://nns.ee/blog/2021/04/01/modem-blog.html)｡

クローズドソースである限り､ハードウェアで何が行われているかわわからない｡SoCのコンポーネント同士はリソースを共有することが多いため(メモリーとか)､データ流出にも繋がりうる｡AP上で実行しているわけではないので､検知もできない｡仮に､｢アプリもオープンソースで､OSもオープンソース､E2EEで安心にやりとりできる｣と考えたとしても､それは､システムレベル以上での話で､ローレベルでメモリーに直接､暗号化キー等を問い合わせられた場合には対応できない｡ユーザーのデバイスはまさにE2EEのE(End)側なので､まさにココを捉えられたらE2EEの意味が崩壊する｡ローレベルのリクエストは､認証があるわけでもなく､ユーザーが気付くものでもないため､守る方法はない｡そういう意味では､どのOSが良いかと考える以前の話だ｡こうしたファームウェアのリスクは､オープンソースを推進するプロジェクトでは指摘されている[(🔗)](https://wiki.postmarketos.org/wiki/Firmware_Risks)｡

クローズドソースだから､脆弱性を利用できるのは､ソースコードを知っている信頼できる企業だけだから大丈夫でしょ!とは言えない｡まずその企業が当てになるかどうかというのもあるが､一旦置いておく｡先程も触れた､Whatsupの場合､サードパーティにあたるNSOは､クローズドソースのアプリの脆弱性をsurveillanceに利用した｡世界には､脆弱性を大金をつぎ込んで探し周り､利用するためにあえて報告しないパーティーが存在する｡クローズドソースだから､脆弱性を利用できるのは一部の人だけだ､とはならない｡


#### 計画性のある脆弱性

クローズドソースではあるものの､動作するためにもファイル自体はデバイス内にあるし､オンラインでも見つけられる[(🔗)](https://github.com/TheMuppets)｡
ただ､バイナリファイルであるため､実際のソースコードを見るには専用のソフト(IDAなど)でリバースエンジニアリングをする必要がある｡

実際､リバースエンジニアリングにより､ソースコードを解読したReplicantというプロジェクトによると､バックドアが仕掛けられていて､BPがファイルにアクセスし､読み書きを行えたことがわかっている[(🔗)](https://www.fsf.org/blogs/community/replicant-developers-find-and-close-samsung-galaxy-backdoor) [(🔗)](https://redmine.replicant.us/projects/replicant/wiki/SamsungGalaxyBackdoor)｡[^1]


[^1]:この発表に対しては､意図的なものではないだろうから､バックドアではないし､この脆弱性によって遠隔操作できる訳ではないという主張がある[(🔗)](https://arstechnica.com/information-technology/2014/03/virtually-no-evidence-for-claim-of-remote-backdoor-in-samsung-galaxy-phones/)､[(🔗)](https://www.androidpolice.com/2014/03/13/security-researcher-dan-rosenberg-calls-bullshit-on-samsung-backdoor-vulnerability-published-by-fsf/)｡
フリーウェアを推し進める文脈で発表されたためプロプラであるというだけで批判的になっているという主張も理解はできる｡ただ､利用された証拠を出せと言っても､証拠が残る類のものではないだろうし､OTAでファームウェアのアップデートが遠隔で行えるだろうから､見つかったコード以上の脆弱性は発生し得る｡そうなるとやはり､プロプラであること自体にリスクはあり得るよなと思う｡落ち着くところとしては､バックドアなのかはわからないし､この脆弱性で遠隔操作ができるのかも決定的ではないというところだろう｡



2つOSがあり､そこにバックドアがある｡バグの形を取りつつ20年以上修正されないのはバックドアを書いていることに等しい｡BPはAPよりも強い権限を持つため､悪用された場合APで走るOSやアプリの書き換え､削除といったこともできる｡BPをIsolationでもしていない限り､RAM､マイク､GPSなどを含む各コンポーネントにアクセスできる｡それも､大抵の場合､すべてリモートでできる[(🔗)](https://www.fsf.org/blogs/community/replicant-developers-find-and-close-samsung-galaxy-backdoor)｡
これが､導入部に掲載した動画の､｢あなたのデバイス上でできることは､すべてリモートでできる｣というセリフに当てはまる｡BasebandがIsolationされていれば､緩和はできるだろうが､バックドアがあることには変わりない｡そもそも､Isolationを確約しているデバイスはあまりない｡仮に確約していてもハードウェアがクローズドソースならば､ドキュメントの正しさを確かめようがない｡バックドアがあれば､電源が落ちた状態でも通信ができる点に関しては､Isolationがどうとかの話ではない[(🔗)](https://www.gnu.org/proprietary/malware-mobiles.html#back-doors)｡




#### OSはいくつあるの?

ちなみに､OSは2つどころではない｡最近のプロセッサーは独自のOSを含んでいる｡例えば､Intel ME, AMD PSPはプロセッサーに独立したシステムがあり､メモリにアクセスできる｡AppleにおいてもAPを補助する意味でcoprocessorがあるが､デバイスがオフだと思っていても常に動いていたりするため[(🔗)](https://www.researchgate.net/publication/302065591_SoK_Privacy_on_Mobile_Devices_-_It%27s_Complicated/fulltext/572fa0fe08ae3736095c1d3f/SoK-Privacy-on-Mobile-Devices-Its-Complicated.pdf)､本当にオフなのかわかりづらい｡

#### 無線全般にリスクがある

Basebandがいつでもどこでもアクセスされうるという点で､一番リスクがある｡しかし､範囲が限られたとしても､無線全般で遠隔でのexploitが起こり得る｡Basebandの脆弱性は､それ単体にとどまらず､BluetoothやWi-fiを通じて､間接的に利用され得る[(🔗)](https://techcrunch.com/2019/11/08/android-baseband-flaws/)｡


#### BootromとBootloader

Bootromはプロプライエタリで変更はできない｡Bootloaderも大抵はフリーではないが[(🔗)](https://cascardo.eti.br/blog/GNU_on_Smartphones_part_II/)､
フリーなものもある｡ただ､Verified bootが有効な場合､Bootromは署名に一致したものしか読み込まないため､フリーなBootloaderに置き換えられない｡この場合､プロプライタリのソフトウェア(Bootloader)にプロセッサーの全コントロール権限を与えてしまうことになる[(🔗)](https://replicant.us/freedom-privacy-security-issues.php)｡

一部Googleの端末(とXiaomiも?)だけがVerified bootの鍵を独自に設定できるようだ｡

#### Kernel

カーネルはフリーの場合でも､ユーザースペースのHardware abstraction librariesは､デバイスによるが大抵プロプライエタリらしい[(🔗)](https://replicant.us/freedom-privacy-security-issues.php)｡

#### SIM

MISP(Mobile Internet Service Provider, 通信キャリア)は､SIMの機能を遠隔でアップデートできるようだ｡ブラウザを開かせたり､GPSやBPやAPとの通信もできる[(🔗)](https://www.researchgate.net/publication/302065591_SoK_Privacy_on_Mobile_Devices_-_It%27s_Complicated/fulltext/572fa0fe08ae3736095c1d3f/SoK-Privacy-on-Mobile-Devices-Its-Complicated.pdf)｡

#### ハードウェアの脆弱性は､非常に危うい

それぞれのコンポーネントが､目的以外の動作･侵害を行えたりするため､非常に複雑だ｡デバイスによるところも多いだろうし､正直複雑過ぎて､よくわからない｡ただ､根本的な脆弱性がハードウェアにはあるということだ｡単純に､この機能で対策しましょうという､特に表層のテクノロジー的な解決は困難だ｡スマホはそもそも､重要なデータを扱ったり保存する場所ではないのかも知れない｡

脆弱性の原因は､クローズドソースであることに由来すると思う｡クローズドソースであることのメリットは､支配力を維持したいパーティーにだけある｡オープンソースのコンポーネントでデバイスを構成しようとするプロジェクトでさえも､modemにはBLOBを含めなければFCCやCEといったCertificateを取得できない｡取得できなければ､販売して出荷することもできない｡modemのファームウェアをオープンソースにするプロジェクトはあるため[(🔗)](https://github.com/Biktorgj/pinephone_modem_sdk)､インストールし直すことはできるが､それでも一部はクローズドでなければいけないようだ(TZ Kernel and ADSP firmwareとか)｡
もちろん今後もデフォルトでインストールされることはないだろう[(🔗)](https://liliputing.com/2021/04/open-source-pinephone-modem-firmware-now-supports-audio-gps-and-power-management.html)｡
その理由として､"various legal constraints"と説明されているが､その不思議なワードについては､Redditでも話題に上がっていた[(🔗)](https://libreddit.tiekoetter.com/r/pinephone/comments/muomyw/open_source_pinephone_modem_firmware_now_supports/)｡


電波関連は規制があるがゆえに､バックドアのためだという話や､単純に無線周波数の規制のためとか､はっきりとしない｡スマホ関連は､レギュレーションやパテントが多いため､オープンには語られない｡ただ､ありえるはなしはありえる｡起こり得ることは起こり得る｡ 脆弱性がそのままの理由がなんであれ､そこに脆弱性は存在する｡


### スマホと大量消費社会

別の記事[(🔗)](https://cookiehookey.neocities.org/why-do-we-have-to-buy-a-new-phone/)で､2~3年に1回､スマホを買い換えなければいけない理由について考えた｡
修理しづらいようになっていたり､セキュリティの更新をできなくすることで､購入を促される｡私達がデバイスを買い換える理由は､単にデバイスが壊れ､使えなくなったからではない｡大量消費社会｡意図的に長く使えないようにされ､消費の循環を強制されているからだ｡

PCの方はと言うと､"スマホの特性"で触れたように､プライバシー上スマホほどSensitiveではなく､less sensor､less businessの印象だ｡WindowsのOSサポート期間も10年ぐらいと比較的長い[(🔗)](https://wikiless.org/wiki/Comparison_of_Microsoft_Windows_versions?lang=en#Windows_NT)｡
グラフィックやUIの肥大化なのか､年月を経るごとに必要要件は高くなるため､どれぐらい使用できるかはデバイスによる｡確かに､Linux系のOSのDebianを基準にすると[(🔗)](https://wikiless.org/wiki/Debian?lang=en#Hardware)､
Windowsのハードウェア要件[(🔗)](https://wikiless.org/wiki/Comparison_of_Microsoft_Windows_versions?lang=en#Hardware_requirements)は高いようにも感じるが､特段厳しいようには､あまり見えない｡
とは言うものの､PCの買い替えを促す意図自体は､スマホ同様あるだろう｡メーカーは､PCにWinodwsをインストールする際にライセンスを購入する必要があり､マージンが発生するからだ｡スマホ業界よりは､マシという程度だ｡


PCであれば､デバイスが故障してもスマホよりは修理しやすいだろうし､10年くらいは使用できるため､中古でも十分賄える｡スマホでは､なかなかこのようには行かないだろう｡





### 無線のリスク

ハードウェアレベルの無線の項目でも一部触れているが､それとはまた違う方向で見る｡

#### Bluetoothの脆弱性

幅広い機種にBluetoothは使用されている｡スマホだけではなく､PCやIoTといったどのデバイスでも､同じような仕組みなので､脆弱性を同様に利用できる｡Bluettoothのプロセスは権限が強いので､事実上デバイスの掌握になる｡インターネットを使わないので､Air-gapしたデバイスも対象になりうる｡Bluetoothは､Wi-fiほど調査されていないため脆弱性はより多い｡

BlueBorneという方法では､ペアリングされている必要もなく､探索モードである必要もない｡ただBluetoothが有効になっていさえすれば良く､ユーザーの動作(タップ､クリックとか)を必要としない｡MITMとして､リモートでコードを実行させることもできる｡Bluetoothは､ペアリングされていない機器に対してもサーチは常にしていて､MACアドレスを撒き散らしている｡それを元にしてOSがわかり､脆弱性が利用されるようだ[(🔗)](https://www.armis.com/research/blueborne/)｡

IP通信ではないので､Firewallも有効ではなく､セキュリティ的に対抗する仕組みはない｡パッチを当てるか､OFFにするか､根本的にセキュリティの仕組みができるまで利用を控えるかが対策として言える｡


#### 位置情報の特定

位置情報の特定方法は様々ある[(🔗)](https://wikiless.org/wiki/Positioning_system?lang=en)｡
GPSやモバイル回線は､それ自体が機能するために位置情報が必要なので､位置情報の特定ができることは大前提として､それらを用いなくても位置情報はわかる[(🔗)](https://wikiless.org/wiki/Indoor_positioning_system?lang=en)｡
モールとか複数階ある屋内施設とかでも､何階にいるかわかる｡BluetoothやWifi､その他電磁場[(🔗)](https://wikiless.org/wiki/Magnetic_positioning?lang=en)などスマホが持ちうるセンサーの多くが使われてる[(🔗)](https://wikiless.org/wiki/Mobile_phone_tracking?lang=en)｡
自宅内でも､細かい場所がわかるかも知れない｡別の視点では､Social graphというと､オンライン上の関係図を構築するというイメージがあるが､位置情報がわかれば蓄積し､オフラインでのSocial graphも作れるだろう｡

#### Wi-Fiを利用した位置情報
Wifiを利用した位置情報システムについて触れる｡Wifiであるため､特にGPSや携帯の電波がなくても､スマホの位置がわかる[(🔗)](https://wikiless.org/wiki/Wi-Fi_positioning_system?lang=en)｡
Google等は､世界中のAP(アクセスポイント)のSSIDやMACアドレスのデータベースを持っており､そこに位置情報を紐付けている｡つまり､この緯度･経度の座標にはこのSSIDがあるといったようなデータベースを持っている｡そのため､データベースにあるSSIDの受信圏内にスマホが入ると､GPSやモバイル回線がなくても位置情報がわかる｡

データベースの収集方法は､Google streetview carで行っていたこともあるが､問題になった[(🔗)](https://gigazine.net/news/20100516_google_wifi_data_collection/)｡
それ以外には､スマホが利用されている｡例えば､WifiとGPSが有効のスマホであれば､位置情報と周辺にあるSSIDの紐付けが簡単にできる｡このデータベースの収集にはAPのパスワード情報は必要なく､スマホが近くを通りSSIDを受信するだけで十分だ[(🔗)](https://www.lifewire.com/wifi-positioning-system-1683343)｡
AppleやGoogleといったベンダー以外にも､アプリでGPSやWifiのパーミッションあれば､アプリ側でも収集できるのかも知れない｡スマホ自体が､周辺環境の収集デバイスになりデータベースを構築する｡今度はデータベースを元に､GPS等が無効でも､周辺環境から位置情報を特定できるようになっている｡



#### Bluetoothを利用した位置情報

Bluetoothも例外ではない[(🔗)](https://qz.com/1169760/phone-data/)｡
データベースのために周辺環境も収集し､今度はデータベースから特定される｡
もちろん､Google以外に､AppleもBluetoothを利用した位置情報システムはある｡

#### 位置情報プラスアルファ

Wifiは常に､スマホに登録したSSID以外にも､付近のすべてのWifiと通信している｡スキャン時に､デバイス自体の情報(MACアドレスなど)を伝えている｡そのため､モールなどでネットワーク元が同じだとすると､今まで述べたベンダー側以外に､AP(アクセスポイント)側にも移動の経路を伝えていることになる｡

### モバイル回線のリスク

モバイル回線の脆弱性については､[SMS認証はやめてくれ](https://cookiehookey.neocities.org/why-not-stop-using-sms-as-2fa/)で触れている｡
SS7という通信プロトコル自体の脆弱性の部分が大きい[(🔗)](https://www.theguardian.com/technology/2016/apr/19/ss7-hack-explained-mobile-phone-vulnerability-snooping-texts-calls)｡
最近はGSM･CDMAから4G､5Gとなっているが､cell towerから後ろの電話回線のプロトコルは変わらない｡SS7ハブへのアクセスができれば､場所を問わず脆弱性を利用できる｡VoLTEであればIP通信になるが､双方が対応していない場合は不完全だ｡

Cell toworまでの経路にも脆弱性はあり､GSMでは正しいcell towerかどうかの認証する前にIMSIやUIDを伝えている｡4G､5Gでも似たような脆弱性はあるようだ｡
Stingray(IMSI catcher)等の仕組みがあれば､強制的に中継させ､2gにDowngradeさせた上で､通常通り通信させることもできる[(🔗)](https://theintercept.com/2020/07/31/protests-surveillance-stingrays-dirtboxes-phone-tracking/)｡
その場合､encryptionをできず､すべて筒抜けになるし､気が付かない｡マルウェアを埋め込むこともできる｡


### 通信キャリアのリスク

位置情報は､長年記録されている[(🔗)](https://www.nytimes.com/2017/06/05/us/politics/supreme-court-cellphone-tracking.html)｡
基本的に､アプリやキャリアとか関係なく､集めたデータは利用する｡自社内の広告のためかも知れないし､サードパーティにデータを販売するのかも知れないし｡データを抽象化するかも知れないが､しないかも知れない｡抽象化もユーザーが期待するほどではないかも知れない｡仕組み上､電話番号を起点としてリアルタイムで場所(接続中のセルタワー)がわかるが､アメリカではキャリアが情報を第三者に提供しているようだ[(🔗)](https://www.vice.com/en/article/nepxbz/i-gave-a-bounty-hunter-300-dollars-located-%20phone-microbilt-zumigo-tmobile)｡

キャリアが販売したデータをまた別のパーティーに売るサービスがある｡Securusというサービスでは､なりすましかも知れないのに大した精査もなく､当局だと主張する相手に位置情報を売っていた｡実際当局も令状なく情報が手に入るため､利用していたようだ｡キャリアは販売先の情報管理まで精査はしていない[(🔗)](https://www.vice.com/en/article/evk484/securus-law-enforcement-track-phones-senator-wyden-letters),[(🔗)](https://www.vice.com/en/article/gykgv9/securus-phone-tracking-company-hacked)｡

通信キャリアが､We take privacy seriouslyと言っても､まったくそうは思えないところは多い｡下記のような会社にデータを売っていた｡

> 認証もなく､同意もなく､携帯を誤差10m~2kmくらいで特定できる｡利用にはWarrant等の書類が必要と言いつつ､その書類が本物かは確認しなかったり､位置情報にはスマホ利用者側の同意が必要だといいつつ､APIでリクエストすると同意を求めずに利用できたりする｡モラルの面でも怪しいところがある｡直接取引がないのに､大手の会社のロゴを使ってたりする｡

We take privacy seriouslyは単なる宣伝文句であり､その発言は30年以上も前の法律をベースにしていたようだ[(🔗)](https://krebsonsecurity.com/2018/05/tracking-firm-locationsmart-leaked-location-data-for-customers-of-all-major-u-s-mobile-carriers-in-real-time-via-its-web-site/)｡

法整備されたとしても､アプリのパーミッション同様､バイパスの方法はあるだろう｡少なくとも､通信キャリアのモラルは当てにならない｡


### 国家組織･国際組織

世界には大金をつぎ込み脆弱性を探し回る企業や組織があるが､その脆弱性を報告したり､修正したりはしない｡なぜなら利用するために探しているからだ｡探すだけでなく､脆弱性を埋め込んだり､仕掛けてもいる｡

最新のセキュリティアップデートをしたところで､意図的に仕掛けられたクローズドソースの脆弱性を利用できる組織があるとするならば､それを見つけ出したサードパーティがランサムウェアに利用すると言ったこともあり得る｡最近は､Webブラウジングを通してのマルウェア混入も多いようだ｡

#### スパイツール

N組織から盗まれたマルウェアがランサムウェアに用いられた｡脆弱性を見つけた段階で指摘をしていれば､問題はなかったが､あえて残しておいたままだった｡利用できる脆弱性を見つけるのに躍起になってはいるものの､それを修正する意図はない[(🔗)](https://www.independent.co.uk/news/uk/home-news/nhs-cyber-attack-edward-snowden-accuses-nsa-not-preventing-ransomware-a7733941.html)｡

ファームウェアが利用された例[(🔗)](https://www.wired.com/2015/02/nsa-firmware-hacking/)｡
ファームウェアに入り込まれたら､システムに対して､強大な力を発揮させてしまう｡

国境をまたぐ時､スマホやパソコンを渡さないといけないが､ハードウェアにスパイツールを入れられる可能性がある[(🔗)](https://cryptome.org/2014/05/nsa-customs.htm)｡



#### 製造段階のリスク

製造段階での盗聴機器､混入のリスクもある[(🔗)](https://www.bloomberg.com/news/features/2018-10-04/the-big-hack-how-china-used-a-tiny-chip-to-infiltrate-america-s-top-companies)｡
以下は一部抜粋｡

> 2015年アメリカの国防関連の情報を扱う企業のサーバー(Elemental Technologies)のマザーボードにマイクロチップが取り付けられていた｡取り付けられていた機器のネットワークに気づかれずにアクセスできるようにするものだった｡調査の結果､サーバー等にマザーボードを供給する会社であるSupermicroの中国の下請けメーカーの工場で挿入されたものと判明した｡工場の管理者に賄賂を渡したり､脅すことにより設計の変更を強要した｡
>
 > よく見るソフトウェアレベルのものよりも深刻なもので､より細工が困難で､より深刻なダメージを生む｡プロダクトを細部まで理解した上でコンポーネントに細工を施すことから､国家レベルの所業であり､人民解放軍のハードウェア攻撃を専門とする部門の関与が疑われる｡大きさは､ペンの先ぐらいのものであり､見た目は他のコンポーネントなりすましていたり､他の部品で覆い隠すようにしたものもあった｡
>
> Baseboard Management Controllerという異常時に利用されるような権限が強いチップに接続することができたため､セキュリティの権限を無効にしたり､暗号化キーを入手したり､ネットワーク上の新たな侵入経路を作り､外部のコードを実行したりできた｡何を行ったかログみたいなものがあるわけではないが､設置させたまま監視をした場合､疎通確認みたいものだけ行っていたことがあるようだ｡実際になにかを行うと言うより､必要なときが来たときに実行するのか､すでに実行した後なのか｡
>
> Supermicroのマザーボードはハードウェア界でいう､マイクロソフトのWindowsくらいの利用者があり､大手企業や政府含めアメリカの30社ぐらいが影響を受けたと考えられる｡ハードウェアから攻められた場合､基本的には検知することはできず､ネットワーク上の異常な動作でようやく何かがおかしいとはわかるが､その段階であっても何が原因かまではわからない｡

題材としては､スマホではなくサーバーの話であったが､同様のことはスマホでも起こりうるだろう｡つまり､製造段階でのハッキングだ｡あとは動機があるかだけだ｡Elementalの場合は､政府や国防関連のサーバーとして利用されているということをマーケティングの一環として公表していたために､ターゲットにされた感がある｡

ハッキングの対策では､スマホもPCも同様に､ソフトウェアが重視される傾向があり､ハードウェアは見過ごしがちだ｡ISPやレンタルサーバーでも､企業側が感知できないところで､ハッキングの影響を受けてる場合も有り得る｡

大きく分けると､コンピューターの装置をスパイマシンに変える方法は2つある｡1つは､メーカーから顧客に運ばれる段階でデバイスに埋め込む､N組織などアメリカのスパイが好む方法で後で少し触れる｡もう1つは､製造のまさに最初の段階で埋め込む方法で､今回の例のように中国など製造が集中しているところができる方法だ｡

この出来事からわかることは､サプライチェーンが一部に集中している事自体にリスクがあるということだ｡製造拠点を中国に頼りすぎなのだろう｡一極集中すると起きうることである｡コストを重視しすぎるあまり､費用的に安いところに大手が集まる｡大手になればなるほど､政府が効率的に介入できる｡

ファーウェイやZTEは中国でも大手のルーターやモバイル機器の製造会社だが､アメリカを筆頭に避ける流れが生じている｡EUはEUで､アメリカのコードを警戒するようになっている｡地産地消のように地元での機器の開発を模索するようになっている[(🔗)](https://archive.ph/https://necunos.com/blog/open-hardware-is-secure-hardware/)｡
ハードウェアの段階でも分散は重要なのだろう｡仮に分散されていたとしたら､効果は激減するだろうから､費用対効果は下がる｡スマホもPCみたいに自作できたらより分散できそうだ｡




#### 流通経路のリスク

製造段階でのマルウェア等の混入が得意な国がいれば､流通段階での混入が得意な国もある｡ターゲットにされた場合､郵送品とかが狙われる場合もある｡特にコンピューターのハードウェアに関しては､途中で入手し､スパイツールをインストールしてから配達する方法がある[(🔗)](https://www.wired.com/2015/02/kapersky-discovers-equation-group/)､
[(🔗)](https://cryptome.org/2014/05/nsa-customs.htm)｡
荷物をインターセプトされている企業がそれを知っているのか､関与しているのかははっきりとしない｡個人相手なら､Amazonとか一極集中した企業を利用していれば､この手法もだいぶ効率がいいだろう｡

> *Government is inherently more dangerous than corporations*

#### 日本とSurveillance

日本とN組織との関係は､戦後1950年代から続く｡今では､大使館や軍基地が諜報の活動拠点･オフィスである｡そこでは､アジアを中心に世界の諜報の足がかりにもなったり､スパイツールの製造も行われている｡巨大なアンテナを設置することで､電話やFAX､インターネットのデータを傍受している｡基本的な目標としては､すべてを集めることにある｡この回線だけ見ます､というのはないだろう｡日本は､国内の拠点の管理を許可するとともに､建設費を提供している｡監視を管理する仕組みはない｡日本のロビー活動も､電話やネットの傍受により､筒抜けだった｡警視庁が情報提供することもある｡相手側からは､一部情報の共有や､日本側へのスパイツールの提供､諜報活動の訓練指導があった[(🔗)](https://theintercept.com/2017/04/24/japans-secret-deals-with-the-nsa-that-expand-global-surveillance/)､[(🔗)](https://web.archive.org/web/20190605220702/http://www.nhk.or.jp/gendai/articles/3965/)｡

Surveillanceの仕組み自体は､安全保障､テロリズム対策､人命救助というが､同時に人からパワーを奪うための仕組みでもある｡Surveillanceは､本来は公共の安全のためであったが､今ではその仕組み自体を守る仕組みとしても機能している｡公には語られず､影で機能する｡政府に対する不正を公言しようにも､そうした仕組みのために､政府からの報復を恐れることになる｡政府が人々を恐れることはあっても､人々が政府を恐れるという構図はどうも居心地が悪い｡

> *“When exposing a crime is treated as committing a crime, you are being ruled by criminals!”*

> *“Now national security really means the security of the system, the institution of government”*


## まとめ
これまでに挙げた脆弱性はもちろん全部ではないが､幅広く触れてきた｡｢それはスマホだけの脆弱性じゃないよね｣という部分もあるが､"スマホの特性"や"情報リテラシーの低さ"がそこにレバレッジをかけている｡
ここに記していない脆弱性については､スマホとプライバシーって?に掲載したリンクを見てもらえればより詳しく書いてある｡


調べるほどに､企業が語ることと現実には差があり､ユーザーの認識とも差がある｡今まで見えていたものが希望なら､ここに記したことは絶望だろう｡企業のトラッキング等を除いても､クローズドソースを守る口実(安全保障､CSAM､パテント)が脆弱性を生み･許容し･維持し､サードパーティに利用される現実がある｡ただ､これをもって､スマホを使うのはやめようという風にはなれない現実もある｡もちろん､使わないという手はあるが､スマホはすでにインフラ化してしまった｡脆弱性なんて無縁でしょ?といいつつ使うのが愚かならば､脆弱性があるから使わないというのも愚かなのかも知れない｡仕方無しに使うとしても､どのように使っていくのが良いのだろうか｡答えはすぐに出ない｡



