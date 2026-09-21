---
title: "メールアドレスをネットで公開する時"
date: 2026-09-20
categories: [Tech]
tags: [Tips,Privacy]
description: ""
draft: false
---

インターネット上でメールアドレスを公開する際に､そのままのテキストで公開すると､ボットに収集され､スパムに利用される｡
基本的に､少し手間がかかる程度で､botを完全に防ぐことは難しいが､ボット対策について紹介する｡



## アイデア
ボットにはわかりにくく､一方でユーザーにはわかりやすくできるようすると､以下のような方法があるようだ(4と5は､mailtoが使えるが､それ以外は使えなくなる)｡

1. 画像で表示する
2. 全角文字で表示
3. @を用いない(★や画像で表記)
4. HTMLエンティティ表記で表示
5. JavaScriptの処理後に表示されるようにする


## JavaScriptの処理後に表示されるようにする
以降は､5のJSを用いた方法を紹介する([このサイト](https://blog.nns.ee/contact/)のコードを参考にした)｡


ちなみに､Cloudflareの[メールアドレス難読化機能](https://developers.cloudflare.com/waf/tools/scrape-shield/email-address-obfuscation/)を用いれば､特別準備は必要ない｡
今回は､CFは用いず､自前で､予めアドレスを暗号化しておき､JSで都度復号化することになる｡

### メールアドレスの暗号化
下記JSの内､`emailAddress`と`encryptionKey`の変数を入力してから､実行する(例えばFirefoxでF12を押して､Consoleタブで実行)｡

実行後に､2桁の数字を羅列した配列が出力される｡


```Javascript
// 新規コンソール画面で実行する

function encrypt(text, key) {
  return Array.from(text).map((char, i) => 
    char.charCodeAt(0) ^ key.charCodeAt(i % key.length)
  );
}

const emailAddress = "abc@example.com";
const encryptionKey = "go@away.ee";
const encrypted = encrypt(emailAddress, encryptionKey);

console.log(encrypted);

```


### 出力内容
上記関数にメールアドレスとキーを入力すると､下記配列が出力された｡
```javascript
[6,13,35,33,18,25,24,67,21,9,2,65,35,14,26]
```

### クリックで復号化する関数
下記コードに､暗号化に用いたキーと､出力された配列を入力する｡
このコードをHTML内に貼り付けておけば､onclickで関数がJSで処理され､実際のメールアドレスに書き換えられる｡

```html
<script>
const encryptionKey = "go@away.ee";
function reveal() {
  document.getElementById("email").innerHTML =
    [6,13,35,33,18,25,24,67,21,9,2,65,35,14,26]
    .map((c, i) => String.fromCharCode(
      c ^ encryptionKey.charCodeAt(i % encryptionKey.length)
    )).join('');
};
</script>
<p><span id=email onclick=reveal()><a href=#>クリックでメールアドレスを表示する</a></span>
```

## 参考リンク
- [ホームページでのメールアドレスの公開方法](https://icts.nagoya-u.ac.jp/ja/security/address-open.html)
- [JS暗号化･復号化の別例](https://andrewlock.net/simple-obfuscation-of-email-addresses-using-javascript/)
