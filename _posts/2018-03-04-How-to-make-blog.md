---
layout: post
cover: 'assets/images/karasawa.jpg'
title: How to make blog
date: 2018-03-04 18:00:00
tags: blog
author: inagaki
---
<p>first step　『環境構築』
①Jekyllをインストール
Rubyから、Jekyllをインストールします。
そのため、このサイトを参考にインストールしました。[参考サイトURL](https://www.ruby-lang.org/ja/downloads/)
そして、</p>

```terminal
$ gem install jekyll
```

<p>でJekyllをインストールします！！</p>

<p>でも、FilePermissionErrorで、インストールできなかった…
これは、「アクセス権がないよ」というエラー。そのため、先頭に”sudo”をつけて、実行し、パスワードを入れれば、インストールできた！！[error参考URL](https://teratail.com/questions/74708)</p>

```terminal
$ sudo gem install jekyll
```

<p>②GitHubでブログ公開用のレポジトリを作成。
”username.github.io”で作ればOK！！
参考URLの”Create repository”を参照[参考URL](https://pages.github.com)</p>

<p>これで、環境設定は完了！！</p>


<p>second step　『ブログ構築』
Jekyllは、たくさんのテンプレートがあるのが魅力！！！
[Jekyll-themes](http://jekyllthemes.org)から好きなテーマを選べます。</p>
僕は、[Hanuman](http://jekyllthemes.org/themes/hanuman/ )を選びました！！
こんな感じのテーマです。いいですよね〜。</p>

![Hanuman img](../assets/images/hanuman.jpg =200×)

<p>これをForkし、cloneをします！！
Forkしたものを開き、cloneするためのURLを取得。
そして、terminalでブログを作りたい住所まで行き、次のコードを実行すれば、clone完了です。</p>

```terminal
$ git clone (clone URL)
```


<p>cloneした、ディレクトリにいき、３つ行うことがありうます！</p>

```terminal
$ cd hanuman
```

<p>1つ目。次のコードを実行。</p>

```terminal
$ bundle install
```

<p>2つ目、”config.yml”に自分の情報を記述。
僕は、Atomを使っているので、Atomで開きました。</p>

```terminal
$ Atom _config.yml
```

<p>3つめ、次のコードを実行して、</p>
```terminal
bundle exec Jekyll serve
```
