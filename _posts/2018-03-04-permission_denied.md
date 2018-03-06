---
layout: post
cover: 'assets/images/cover/tree.jpg'
title: Permission denied
date: 2018-03-04 19:05:55
tags: permission error　denied
author: yuuuuuya
---

<h1>Permission denied</h1>
作成した投稿を、Githubのサーバーにcommit&pushする前に、Jekyllのサーバーで確認しようとして、
```terminal
$ bundle exec Jekyll serve
```
を実行しようとした時に、
```terminal
jekyll 3.6.2 | Error:  Permission denied @ rb_sysopen - /hanuman-pages/about/index.html
```
と表示されました。
そのため、permissionを調べました。[『参考URL』](https://teratail.com/questions/16788 )
```terminal
$ find /hanuman-pages/about/index.html | xargs ls -ld
```

実行結果
```terminal
-rwxr--r--  1 root  wheel  62012  3  5 01:04 /hanuman-pages/about/index.html
```
※これは、”アクセス権、リンク数、所有者名、グループ名、サイズ、最終更新日時、名前の詳細”を表している。[『参考URL』](https://do-zan.com/mac-terminal-ls/)

所有者は、root（スーパーユーザー）だったので、所有者として実行の権限を与えるコマンド”sudo”をコードの頭につけることで実行できました。
```terminal
$ sudo bundle exec Jekyll serve
```
----------------------------------------------------
<h4>メモ（アクセス権の見方）</h4>


|1ケタ目|2~4ケタ目|5~7ケタ目|8~10ケタ目|
|:----:|:------:|:------:|:-------:|
|ファイルの種類|所有者|所有グループ|その他|
|-:file|r:読み込み許可 |r:読み込み許可|r:読み込み許可|
|d:directry|w:書き込み許可 |w:書き込み許可|w:書き込み許可|
|l:symbolic link|x:実行許可   |x:実行許可|x:実行許可|
| |-:許可ない|-:許可ない|-:許可ない|

[『permissionの読み方参考URL』](https://do-zan.com/mac-terminal-chmod/)
