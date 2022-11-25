---
title: "ProtonVPNのUTMパラメーター"
date: 2022-03-06
categories: [Tech]
tags: [Privacy]
description: ""
draft: false
---
## ProtonVPN

ProtonVPNと言えば､ProtonMail系列のVPNサービス｡
触れ込みによると､プライバシーを売りしているようだ｡

> ### Why use VPN
> Keep your browsing history private. As a Swiss VPN provider, we do not log user activity or share data with third parties. Our anonymous VPN service enables Internet without surveillance.

## メールにはUTM

ProtonVPNのアカウントを削除した際に､削除完了を知らせるメールが送られてきた｡
[ProtonVPNのサイト](https://protonvpn.com/)は､サードパーティーのアナリティクスはないし､メールにもビーコンはない｡クリーンな印象ではあるが､メール内のリンクにUTMが使われていた｡

![protonvpn-utm](/img/protonvpn-utm.png)

UTMというと､Urchin Tracking Moduleのことでマーケティングの効果測定のために､URLに"?utm_source="といったパラメーターをつけることでトラッキングできる｡現在は､Google Analyticsの一部機能｡

最近では､ブラウザのデフォルト設定でも､広告ブロックであったり､サードパーティークッキーのブロックができるので､こうしたURLを用いたサーバーサイドでのアナリティクスの方が正確な分析ができるのかもしれない｡

プライバシーを売りにしていても､やはり企業としては分析しなきゃいけないようだ｡
