---
title: "サービスをセルフホストする"
date: 2022-11-28
categories: [Tech]
tags: [Privacy,Finance]
description: ""
draft: true
---
- プライバシーとは､誰がコントロールを持っているかということとトレードオフになる｡
	- コントロールを受け渡すならば､プライバシーは下がる｡

自由とセキュリティとプライバシー
	セキュリティとプライバシーは相反する
	アメリカの国境､カメラでの監視､body scanner
	誰がコントロールを持つか
	自分でコントロールするためには､自分たちでセルフホストしかない


- sshはすごい
	- サービスの公開(Remote forwarding),nginx,tunnel
	- local forwarding,firewall
	- vpn,
	- x11 forwarding,guacamole


- user,governer,ownerの3つ
	- どのものにも当てはまる(住宅とか､vpsとか)
	- プライバシーやautonomyにも通ずるか


- ドメインのsslも管理はできない｡
	- https://gigazine.net/news/20221110-trustcor-systems-with-government-ties/

    - フィッシング詐欺の対策
    - 一般的な対策
    - 正しいURLでも､別のサイトかも
        - DNSキャッシュポイズニングをされたら
        - ドメインが期限切れだったら
            - 過去のVISAの事例

