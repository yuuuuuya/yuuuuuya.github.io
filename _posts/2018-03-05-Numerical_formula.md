---
layout: post
cover: 'assets/images/cover/tree.jpg'
title: ブログで数式を入力できるようにする。
date: 2018-03-05 05:05:55
tags: MathJax, blog, Github, Github-pages jekyll, 数式
author: yuuuuuya
---

<script type="text/javascript" src="https://yuuuuuya.github.io/js/MathJax/MathJax.js?config=TeX-MML-AM_HTMLorMML"></script>

<h1>Github-pages + jekyllのブログで、数式をかけるようにする</h1>



<p>ブログ上で、</p>
\\( 1/x^{2} \\)
<p>このような数式を書くには、"__MathJax__"をインストールしなければいけません。</p>
<p>MathJaxのインストール方法から、ブログ上で数式をかけるようになるまで、簡単に書いておきま す。</p>

<h2>MathJaxのインストール方法</h2>
<p>username.github.ioのレポジトリにcommit&pushしているフォルダーで、cloneを作成。</p>

```terminal
$ git submodule add -b v2.6-latest https://github.com/mathjax/MathJax.git js/MathJax
```

<p>実行すると、".gitmodule" と "js/MathJax" が作られているはず。</p>
<p>".gitmodule" と "js/MathJax" を commit&push する。</p>

<p>これで、準備は完了。</p>

<h2>MathJaxを呼び出す</h2>

<p>記事を書く際に、毎回、MathJaxを呼び出す必要がある。</p>
<p>そのため、ヘッダーにMathJaxを呼び出す次のコードを書く。</p>

```Atom
$ <script type="text/javascript" src="https://username.github.io/js/MathJax/MathJax.js?config=TeX-MML-AM_HTMLorMML"></script>
```

<p>※srcのURLが存在するか要確認。先ほどclone, commit&pushしたフォルダー(js/MathJax/config/)にいくつかの設定プリセットがある。その中の１つを呼び出している。</p>
<p>※"TeX-MML-AM_HTMLorMML.js"を呼び出したいときは、".js"を省いて、config=TeX-MML-AM_HTMLorMMLとする。</p>



<p>以上で数式をかけるようになっていると思いま す！！！。</p>


<p>[参考URL](https://leico.github.io/TechnicalNote/Jekyll/mathjax-install)←わかりやすく書いてあり、とても参考になりました。</p>
