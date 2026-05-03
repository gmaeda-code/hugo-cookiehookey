---
title: "voidlinuxでパッケージをダウングレードする"
date: 2026-04-21
categories: [Tech]
tags: [Tips]
description: ""
draft: true
---

voidlinuxでは､カレンダーにcalcurseを使っている｡
最近versionが4.8.2になると､calcurse-caldavで同期時に作成されるlockfileが､同期完了後に削除されなくなった[^1]｡
そのため､手動で削除しないと新たに同期ができないので､calcurseをダウングレードすることにした｡

## ダウングレード
version4.8.1であれば､問題なかったので､下記を実行する[^2]｡
```bash
# xdowngrade /var/cache/xbps/calcurse-4.8.1_1.x86_64-musl.xbps
# calcurse -v    
calcurse 4.8.1 -- text-based organizer
```

## アップデート時の除外
パッケージ全体のアップデート時に､まとめてアップデートされてしまうので､一旦除外する｡
```bash
# xbps-pkgdb -m hold calcurse
```
下記を実行して､calcurseがholdになっていて､実行してもアップデートされなければ除外できていることが確認できる｡
```bash
sudo xbps-install -Su
```


## パッケージ修正後にアップデート
issueが修正されたら､下記を実行して､アップデート対象に含めるようにする｡

```bash
# xbps-pkgdb -m unhold calcurse
```

\--- 
[^1]: https://github.com/lfos/calcurse/issues/523
[^2]: https://docs.voidlinux.org/xbps/advanced-usage.html
