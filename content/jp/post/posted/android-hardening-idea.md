---
title: "Androidのプライバシー対策"
date: 2022-06-07
categories: [Tech]
tags: [Privacy,Mobile,Android]
description: ""
draft: false
---

[別記事で､](https://cookiehookey.neocities.org/smartphone-and-privacy2/)Pinephone､Librem5といった端末をモバイルデバイスの選択肢として挙げたが､既に大勢が持っているAndroidデバイスで利用することも検討してみたい｡Torのブログで､そうした試みがあるため､参考にしている[(🔗)](https://blog.torproject.org/mission-impossible-hardening-android-security-and-privacy/)､[(🔗)](https://blog.torproject.org/mission-improbable-hardening-android-security-and-privacy/)｡
恐らく､OSのバージョンにより､違いががある｡



## 不要なコンポーネントを取り除く
スマホにあるセンサー､コンポーネントは大体以下の通り｡対策の考察については､[torのコメント](https://blog.torproject.org/mission-improbable-hardening-android-security-and-privacy/#comment-221260)が参考になる｡

- マイク
- baseband
- カメラ
- 加速度計（加速度センサー）
- ジャイロスコープ（ジャイロセンサー）
- 磁気センサー
- GPS
- 生体認証センサー(指紋)
- 近接センサー
- 環境光センサー
- Wifi
- Bluetooth
- NFC

ソフトウェア的に電源を落とすだけで機能が完全にOFFになるわけではなく､かと言ってバッテリーを簡単に取れるわけでもない｡そのため､不要なコンポーネント･センサーは物理的に除外し､適宜外部化(ルーター､マイクetc)する｡baseband含めた無線関連は､位置情報を使用できなくなる可能性があるので､よく検討すること｡使う可能性のあるセンサー･コンポーネントは､テープで塞いだり(カメラ)､ファラデーケージ(電波系)を利用することで物理的に対処できる｡

キルスイッチや､isolationの確認ができるならば､ハードウェア改造の必要性は下がるが､Androidスマホにキルスイッチはないしだろうし､modemからのisolationが確約されたデバイスは少ない｡basebandを含まないとされるWifiのタブレット等を使うのもあり｡センサーが少ないdumbphoneでもマイクは意図せず動作しうるので[(🔗)](https://www.cnet.com/news/privacy/fbi-taps-cell-phone-mic-as-eavesdropping-tool/)､スマホ同様に対処する｡

分解方法は､"機種名"+"teardown"とか"repair"といったキーワードで検索すれば､動画が出てくる｡[ifixit](https://www.ifixit.com/)で､コンポーネントが大体わかるので､不要なものは取り外す｡
下記のようにマイクはきれいに取れなくても､問題なく使えなくなる｡通話時はイヤホンマイクを差し込むことで対応する｡
![mobile-teardown-mic](/img/mobile-teardown-mic.png)




## 不要なファームウェアの削除

前章のように物理的に取り除くことに加えて､ファームウェアの削除での対処もする｡

私の場合マイク同様に､RF関連のコンポーネントを物理的に取り外そうとしたが､できなかった｡LTEのカバーは簡単に外せたが､GSMの方はカバー自体が固くて取り外せなかった｡そのため､TWRPのCLIでmodemのファームウェア削除で対処を試みた｡ちなみに､firmwareを削除すると､コンポーネント自身で電源を落とせないので､電力消費は多くなるかも?

```bash
# バックアップ
cd /dev/block/platform/.../by-name #｢...｣の部分は機種による｡
dd if=./modem of=/sdcard/modem #拡張子.imgはなくてもよさそう｡ 
# 復元するとき
dd if=/sdcard/modem of=./modem

# 削除
dd if=/dev/zero of=./modem
```
modemの削除がうまく行くと､"Settings" -> "About phone" が "Baseband version: Unknown"になるらしいが､私の場合は､TWRP上のCLIで削除した段階で､システムが起動しなくなった｡




## システム
マーケティングのためなのかパッケージ化されたOSは､プライバシー上問題があるアプリをデフォルトで含んでたりするため､カスタムROMを利用する｡ReplicantとかGrapheneOSとか｡

FDEやFBEが有効かとか､一通りSettingsはチェックすること｡


## 利用方針

サービス利用時には､OPSEC的なところを重視する｡冒頭の[テーマ･方針](https://cookiehookey.neocities.org/smartphone-and-privacy2/#テーマ方針)として触れた部分である｡必要最小限で構成し､それを必要なときだけ利用するなど｡

## ネットの接続方法

パケット交換方式でのみ通信を許可するために､機内モードにし､modemを外部化する｡モバイルルータ(FLOSSが望ましい)で電波を受信し､それをスマホにつなげる｡スマホとモバイルルーター間の接続方法は無線ではなく有線(LAN)のほうが望ましいが､Wifiであればbasebandよりはマシだと思っている｡通信はSSLで暗号化されるように注意する｡

スマホが複数台ある場合､1台をルーターとして使用することはありだが､スマホ(ルーター)自体が多機能で､センサーや高精度なGPSを備えている点は考慮したい｡


## Wifiトラッキングの対処
Wifiを利用したトラッキングについては別記事で触れた｡

モバイルルーター側では､SSIDを設定する際に､下記のように設定することで､SSIDのデータベースからoptoutできる[(🔗)](https://www.kuketz-blog.de/empfehlungsecke/#wifi-optout)｡
`<SSID>_optout_nomap`

スマホ側では､Wifiは他の機能同様デフォルトOFFで､必要なときだけONにする｡それを助ける意味で､指定したWifiを受信しなくなったらWifiを自動でOFFにする機能がある[(🔗)](https://www.kuketz-blog.de/empfehlungsecke/#wifi-tracking
)｡この機能により､自宅でWifiを使用している場合､外出時にスマホのWifi受信を自動でOFFに切り替えることができる｡
LineageOSベースのOSだけかもしれないが､
1. Settings->System->System profilesへ進む
2. 使用するprofileを選び(defaultとか)､設定画面に進む｡
3. "Triggers which will activate this profile"をWifi自動OFFに紐付けたいSSIDに設定｡
4. "Wi-Fi"という項目を"Turn off"にする｡
5. その他のアンカーは､好みがなければ､"Leave unchanged"にする｡

MACアドレスのランダム化の機能･設定･アプリがあれば､補助的に使うのはあり｡

## アプリの利用

### アプリのインストール

すべて､F-Droidのみから行う｡(もし､Playstoreのクローズドなアプリを使用したい場合は､Aurora storeを利用すればGoogleアカウントは必要ない｡Shelterというアプリで､プロファイルを別に用意して隔離環境で利用するなど工夫する｡プロプライエタリだとSSLのエラーが出るのか不明｡)

### 通信の管理
- すべての通信を､Tor経由(例:orbot)か､VPN経由(例:RiseupVPN)にする
- 一部アプリはRoot化を前提とするので､必要性を感じるならRoot化する(例:Magisk)｡
    - VPNとフィルタリングをデバイス側で同時使用するためにRoot化している｡VPNならサーバー側にフィルタリングを設定してもいいし､モバイルルーター側に設定しても良い｡また､NetGuardというアプリで対応できるかも知れないし､Shelter等でプロファイルを分けるとRootは必要ないのかも知れない[(🔗)](https://technicalmarisa.root.sx/blog/non-root-android-hardening-v4/)｡
- Firewall(例:AFWall+)でデフォルトすべてブロックで､必要なアプリ･サービスのみ､TorかVPNで通信許可する
- DNS/Hostフィルタリング(例:AdAway)で､好みのフィルターを入れる｡  
[filterlists.com](https://filterlists.com/)で検索できる｡網羅的なフィルターとしては､energized/ultimateや1Hosts(pro/xtra)など｡
- アプリのインストール直後は､まずアプリ内のプライバシー設定､以下項目のリソースへのアクセス管理設定を済ませる｡その後に､通信が必要なアプリならばファイヤーウォールでアプリの通信を許可する｡

### リソースへのアクセス管理

Permissions
1. Settings-> Apps&notifications->App permissions
2. パーミッションごと､アプリごと等で見ていき､必要なものだけONに許可する｡  
例)Browserにカメラの権限は必要ないと思うならOFFにする｡

Privacy Guard
1. Settings->Security&privacy->Trust->Privacy Guard
2. 全てにチェック(システム含めすべてPrivacy Guardの対象にする)
3. 必要なものだけ"Allowed"にする｡LocationなどSensitiveだと思う情報は"Always ask"､全く使わないと思うなら"Ignored"にする｡

## 電話回線は使用しない

モバイルルーターを使用することで､すべてパケット交換方式での通信するとしたが､PSTNとの電話はどうするかというところ｡PSTNとのブリッジを用意しているSIP(IP電話)に登録し､Linphoneなどに設定する｡
