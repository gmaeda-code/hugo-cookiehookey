---
title: "メディア: 音楽"
date: 2024-01-21
categories: [Tech]
tags: [media]
description: ""
draft: false
---

ストリーミングで音楽を聴くと､ネットワークやサーバー側の影響を受け､安定して再生できない｡
例えば､長時間の再生であったり､しばらく放置してから再開するとき｡
やはり､ローカルにあるデータを再生する方が安定する｡

## soundcloud
[scdl](https://github.com/flyingrub/scdl)で､soundcloudから入手できる｡

30秒などの短い音楽を除外するには､入手後にfindで削除してもいい｡
```bash
find . -type f  -size -700k -delete
```
