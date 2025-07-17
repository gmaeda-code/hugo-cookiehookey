---
title: "メディア: bilibili"
date: 2024-07-10
categories: [Tech]
tags: [media]
description: ""
draft: true
---

bilibiliには､日本のバラエティ動画があったりする｡
ただ､browserで見ると1分くらいで止まるし､anthology(小分けされた動画)だとそれが切り替わる度に発生する｡
ローカルで見れるようにした方が安定する｡

## yutto
[yutto](https://github.com/yutto-dev/yutto)

anthologyの場合
```bash
yutto --batch {video-url}
```

タイトルが長い場合
```bash
yutto -tp {download_date} --batch {video-url}
```
