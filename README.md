# README

## セットアップ

サイト作成

```shell
hugo new site hugo-hestia-pure
```

レポジトリ初期化

```shell
cd hugo-hestia-pure
git init
echo '*~' >> .gitignore
echo '*.bak' >> .gitignore
echo '*.orig' >> .gitignore
echo '.env' >> .gitignore
echo 'public' >> .gitignore
echo 'resources' >> .gitignore
```

テーマ設定

```shell
git submodule add https://github.com/diwao/hestia-pure.git themes/hestia-pure
```

(参考)submoduleの削除

```shell
git submodule deinit -f themes/hestia-pure
git rm -f themes/hestia-pure
rm -fr .git/modules
```

サイト設定

```shell
cp themes/hestia-pure/archetypes/default.md archetypes
```

config.toml

```toml
baseURL = "https://higebobo.github.io/hugo-hestia-pure/"
languageCode = "en-us"
defaultContentLanguage = "ja"
title = "Hugo Hestia Pure"
theme = "hestia-pure"
```

## パーマリンクおよびフロントマタ➖

以下の場合

config.toml

```toml
[permalinks]
  post = "/:year/:month/:title/"
```

postコンテンツは http://<baseURL>/<year>/<month>/<title>/ のURLを生成する

たたしFront Matterのurlが優先される

```toml
author = "higebobo"
title = "Hello"
date = 2020-06-09T12:46:49+09:00
categories = ["sports", "baseball"]
draft = false
url = "/kokoni/okitain/dayo.html"
```

> github pagesやnetlifyで使う場合はbaseURLのプロトコルはhttpsにすること

起動確認(http://localhost:1313)

```shell
cp /path/to/someplace/Makefile .
make run
```

Githubレポジトリ作成後

```shell
cp -pr /path/to/someplace/.github .
git remote add origin git@github.com:higebobo/hugo-hestia-pure.git
git add .
git commit -m 'init'
git push -u origin master
```

## Github Actionsの利用

* .github/workflows/gh-pages.yamlを作成
    * ソースはmasterブランチ
    * 出力はpublicフォルダの内容をgh-pagesブランチ

```shell
make deploy
```

* Github>Settings>Gighub Pages>Source>gh-pages branchに設定する
* しばらく時間がかかる

## 既存のレポジトリからクローンする場合

```shell
git clone git@github.com:higebobo/hugo-hestia-pure.git higebobo-hestia-pure
cd higebobo-hestia-pure
git submodule update --init --recursive
```

## 使い方

### 投稿

新規投稿

```shell
hugo new post/hello.md
content/post/hello.md created
```

編集

```shell
vi content/posts/hello.md
```

## Link

* [Hestia Pure \| Hugo Themes](https://themes.gohugo.io/hestia-pure/)
* [Hugo用テーマHestia Pureが公式サイトに追加されました \- diwao日記](https://diwao.com/2018/03/hestia-pure.html)
