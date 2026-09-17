---
title: "kindleでニュースを読む"
date: 2026-09-16
categories: [Tech]
tags: [Tips]
description: ""
draft: false
---

RSSなどのフィードを使って､kindleでニュースなどの記事を読む方法

## 構成､流れ
- サーバーで行う作業
    - ebookの作成: フィードからデータを取得してepubを作成
    - メールの送信: 作成したebookを､kindleライブラリに送信
- kindleライブラリー
    - ebookの保持と配布
- 端末
    - ebookの受取と閲覧


## サーバーで行う作業
フィードの取得･ebookの作成をcalibreで行う｡

### ファイル構成
```bash
# パスの通った場所に実行ファイルと設定ファイル､calibreのレシピも用意する｡
$ ls -l ~/bin
-rw-r--r-- 1 mg mg  223 Jun 16 12:03 conf.txt
-rwxr-xr-x 1 mg mg 1728 Jul 27 09:45 rsstokindle.sh

$ ls -l ~/.config/calibre/custom_recipes
-rw-r--r-- 1 mg mg 2225 Jul 17 09:03 news_1111.recipe
```

### recipeの用意
calibreのGUIから用意しても良い｡
feeds=[]内に同じフォーマットで列挙していけば､複数のフィードを登録できる｡
パラメーターは好みに応じて設定する｡

```bash
$ cat news_1111.recipe
# vim:fileencoding=utf-8
from calibre.web.feeds.news import BasicNewsRecipe

class AdvancedUserRecipe1678082873(BasicNewsRecipe):
    title          = 'news'
    oldest_article = 7
    max_articles_per_feed = 10
    auto_cleanup   = True

    feeds          = [
	('https://cookiehookey.neocities.org/index.xml'),
    ]
```

### conf.txtの中身
KINDLE_ADDRは､send to kindleで使う送信先のアドレス､amazonのページから探す[(参照)](https://www.amazon.co.jp/sendtokindle/email)

```bash
$ cat conf.txt
# mail configuration
KINDLE_ADDR="example@kindle.com" # kindleの送信先アドレス
MAIL_ADDR="user@example.com" # メール送信で使う送信元の自分のアドレス
MAIL_USER="user" # ユーザー名､アドレスの@以前の部分
MAIL_PASSWD="your-strong-mail-password" # メールのパスワード
```

### rsstokindle.shの中身
calibreでRSSフィードの取得､ebookの作成､メールの送信を行う｡
```bash
$ cat rsstokindle.sh
#!/bin/bash
 
##################### configurations #########################################
# load mail configuration
source ~/bin/conf.txt
 
#working_directory
recipe_dir="/home/mg/.config/calibre/custom_recipes/news_1111.recipe"
output_dir="/home/mg/Downloads"
 
# file name. ex. RSSFeeds_201308220730
output_file_b="RSS_`date +'%Y-%m-%d_%H-%M'`.mobi"
output_file="RSS_`date +'%Y-%m-%d_%H-%M'`.epub"
 
# kindle, kindle_dx, kindle_fire, kindle_pw
conv_opts="--output-profile=kindle"
 
##################### run programs #########################################
echo "starting ebook-convert ..."
# mobiで取得してから､epubに変換することで､amazon側でのフォーマットエラーを減らす｡
ebook-convert $recipe_dir $output_dir/$output_file_b $conv_opts
ebook-convert $output_dir/$output_file_b $output_dir/$output_file $conv_opts
 
# send email to kindle library
if [ $? -eq 0 -a -f $output_dir/$output_file ];
then
    echo "starting ebook-smtp ..."
    calibre-smtp -a $output_dir/$output_file \
    --relay disroot.org --port 587 -e TLS \
    -u $MAIL_USER -p $MAIL_PASSWD $MAIL_ADDR $KINDLE_ADDR \
    -s 'RSS Feeds to Kindle' ''
    if [ $? -eq 0 ];
        then
        echo "SUCCESS: send to kindle $output_file"
        # 以下はcronでの実行時にエラーが出た時のdebug用
        #echo "SUCCESS: send to kindle $output_file" >> ~/bin/dbg-msg.txt
        rm -f $output_dir/$output_file_b
        rm -f $output_dir/$output_file
    else
        echo "ERROR: calibre-smtp failed. NAME: $output_file"
        #echo "ERROR: calibre-smtp failed. NAME: $output_file"  >> ~/bin/dbg-msg.txt
    fi
else
    echo "ERROR: ebook-convert failed. NAME: $output_file"
    #echo "ERROR: ebook-convert failed. NAME: $output_file"  >> ~/bin/dbg-msg.txt
fi
```

### プログラムの実行
手動であれば都度実行､自動であればcronで設定｡
```bash
# serverではなく､client側以下のように設定もできる
$ which rss-to-kindle
rss-to-kindle: aliased to ssh {host-name} /home/mg/bin/rsstokindle.sh > /dev/null 2>&1
$ rss-to-kindle
```

```bash
$ crontab -e
# 以下は1日おきに朝6時に実行
00 06 */2 * * /home/mg/bin/rsstokindle.sh > /dev/null 2>&1
```

## まとめ
上記の方法で､フィードを提供しているサイトであれば､newsをkindleで読めるようになる｡

また､応用として､wallabagを用いれば､記事単位で読みたいものだけを追加して､後でkindleで読むということも出来る｡
