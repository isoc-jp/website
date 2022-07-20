
# ISOC-JP Webサイトについて

ISOC-JPの概要や活動について情報公開するためのWebページです。

* トップページ：https://www.isoc.jp/ （作業用ページ：https://isoc-jp.pages.dev/）

ISOC-JP Webページメンテナンスチーム（有志）によってメンテナンスされています。
ご連絡はISOC-JPオフィサー（「ISOC-JPのご紹介」をご参照）まで。Slack ISOC Japan Chapter に入って頂くと連絡を取りやすいです。

* ISOC-JPのご紹介
https://www.isoc.jp/aboutus/
<br><br>

# ファイルの構成

| ページ | ファイル |
| ---- | ---- |
| トップページの内容 | content/pages/home.md |
| 静的なページ置き場 | content/infoPages/ |
| 各委員会のページ置き場 | content/infoPages/committees/ |
| 自動分類のカテゴリー | content/postCategories/ |
| 自動分類されるページ置き場 | content/posts/ |
| 自動分類されるページ例 | content/posts/IETF113Update.md |
| 旧サイトから移行中のコンテンツ | content/content/migration/ |

<br><br>

# 編集とレビューの考え方

| 編集内容 | レビューや反映の考え方 |
| ---- | ---- |
| 軽微な語句の修正 | 各自で反映します。 |
| チームの他の人にレビューしてもらいたい変更 | Pull requestし、レビューして欲しい人を指定します。レビューが終わったら Pull request した人が merge して close します。Webメンテナンスチーム： ([@isoc-jp/team-website-maintainer](https://github.com/orgs/isoc-jp/teams/team-website-maintainer))  |
| 議事録やメンバーの変更 | Pull requestします。Pull requestし、レビューして欲しいオフィサーを指定します。レビューが終わったら Pull request した人が merge して close します。オフィサーのご連絡先： ([@isoc-jp/officer](https://github.com/orgs/isoc-jp/teams/officer)) |

<br><br>

# 編集方法

編集にはGitHubのアカウントが必要です。更にWebメンテナンスチームに入っている必要があります。編集作業をされたい方はISOC-JPオフィサーまでご連絡ください。<br>
編集には3つの方法があります。
<br><br>

## ■GitHubのWebインターフェースを使う方法

ちょっとした修正を行うのに適した方法です。

1. GitHubのISOC-JP Websiteリポジトリにアクセスします。

* isoc-jp/website
https://github.com/isoc-jp/website/

2. 編集したいファイルをクリックして鉛筆マーク「Edit this file」をクリックします。Markdownで記述します。「Preview」をクリックするとWebページとしてどう見えるのかが確認できます。
3. 編集したら変更の趣旨を「Commit changes」の欄に、具体的な変更点をその下の欄に書きます。
4. 「Create a new branch for this commit and start a pull request.」を選択して「Propose changes」をクリックします。
5. GitHub isoc-jp/websiteの「Pull requests」にリストされたら完了です。
 
今回の変更について他の人がレビューするのを待っている状態になります。公開Webページにはまだ反映されていません。
自分でマージできる方はマージします。

WebメンテナンスチームがマージしますのでSlackなどでご連絡ください。一か月に一度程度の頻度で確認はしていますが頻度と内容を含めてすぐに反映されないことがありますことをご了承ください。
Pull requestの中でcloudflareによるエラーが表示されている場合、公開するにはそれを修正する必要があります。エラーメッセージをよく読むと対処方法が分かることがあります。分からない場合にはWebページメンテナンスチームかISOC-JPオフィサーにご連絡ください。
<br><br>

## ■gitを使ってローカルファイルとして編集する方法

いくつものファイルを一度に変更するのに適している方法です。

1.リポジトリの最新ファイルをクローンします。

```{r}
$ git clone git@github.com:isoc-jp/website.git
```

GitHubへのsshを使ったアクセス方法は「github ssh」といった単語を検索すると説明しているページが見つかります。

2.作業用のプランチを作ります。

```{r}
$ cd website.git/
$ git checkout -b <作業用ブランチ名>
```

作業用ブランチ名には、ユーザ名と編集趣旨を2単語くらい繋げた文字列をハイフンでつなげたものが分かりやすいでしょう。

3.ファイルを編集してローカルリポジトリに変更を追加しコミットします。

```{r}
$ emacs <ファイル>
$ git commit -m "<編集の趣旨>"
```

4.自分のリポジトリとして分岐を作成(fork)し、リポジトリにアップロード（push）してからプルリクエストします。

```{r}
$ git fork
$ git push <GitHubのユーザ名> <作業用ブランチ名>
$ git pull-request
```

5. GitHub isoc-jp/websiteの「Pull requests」にリストされたら完了です。Pull requestは他の人がレビューするのを待っている状態で、まだ公開Webページには反映されていません。
6. 自分でマージできる方はマージします。

WebメンテナンスチームがマージしますのでSlackなどでご連絡ください。一か月に一度程度の頻度で確認はしていますが頻度と内容を含めてすぐに反映されないことがありますことをご了承ください。
Pull requestの中でcloudflareによるエラーが表示されている場合、公開するにはそれを修正する必要があります。エラーメッセージをよく読むと対処方法が分かることがあります。分からない場合にはWebページメンテナンスチームかISOC-JPオフィサーにご連絡ください。
<br><br>

## ■ローカルのサーバを準備して閲覧しながら編集する方法

「gitを使ってローカルファイルとして編集する方法」と下記「ローカルのサーバ準備手順 (macOS)」を行います。
<br><br>

## ローカルのサーバ準備手順 (macOS)

1. node.js, yarnを準備する  
例: `brew install nodejs yarn autoconf vips`
2. 必要なモジュールをインストールする  
`yarn`
3. ローカルに開発用サーバを起動する  
`yarn start`
4. http://localhost:8000/ にアクセスする
<br><br>

## コンテンツ編 - 旧コンテンツの移行（migrate/ 内のファイルの編集）

1. content/migration/ の中のファイルを編集用に開きます。
2. 先頭に下記のようなテキストを追加します。
  1. 本文中にあるタイトルをtitle:に記述して本文の方を削除します。
  2. date:を当時の文書公開日等にします。
  3. categoryを https://isoc.jp/activities/ をみながら指定します。
```
---
template: SinglePost
title: 第一回 ISOC-JP 勉強会 / 1st ISOC-JP Workshop
status: Published
date: '2018-03-27'
categories:
  - category: ISOC-JPワークショップ
  - category: 各種活動
---
```
3. ページがどのように見えているのが良いのかを踏まえながらマークダウン形式に直します。
4. pull request します。merge されたら一旦完了です。
5. (分かる方) このあと、ファイルを content/posts/ に移動してActivitiesのページで表示されるようにすると完了です。(分からない方) Webメンテナンスチームがなんとかしますので merge までで結構です。

## トラブルシューティング - ローカルのサーバ準備

開発用サーバを起動する時に、環境によっては下記エラーがでるかもしれない。

```
digital envelope routines::unsupported
```

ひとまず起動するだけなら、
NODE_OPTIONSに `--openssl-legacy-provider` を設定する。

```
export NODE_OPTIONS=--openssl-legacy-provider
```
