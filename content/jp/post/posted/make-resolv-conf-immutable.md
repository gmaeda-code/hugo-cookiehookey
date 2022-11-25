---
title: "Nameserverを固定する"
date: 2022-03-25
categories: [Tech]
tags: [DNS]
description: ""
draft: false
---

3rd partyアプリに､自動でnameserverの設定を変更されないようにするために､chattr +iを使用したがエラーが返ってきた｡

```bash
chattr +i /etc/resolv.conf
chattr: Operation not supported while reading flags on /etc/resolv.conf
```

symlinkには使用できないようだが､リンク先の/run/systemd/resolve/resolv.confに当てはめても同じエラーだった｡


```bash
rm /etc/resolv.conf
vim /etc/resolv.conf 
chattr +i /etc/resolv.conf
```

これで､resolv.confはリンクされてない状態になり､仮に3rd partyアプリが変更しても､実際に使用される/run/systemd/resolve/resolv.confには影響がなくなった｡

この他､dhcpcdを用いて､上書きされないようにする方法もあるようだ｡
