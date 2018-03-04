---
layout: post
cover: 'assets/images/cover/karasawa.jpg'
title: 回帰問題（不連続）
date: 2018-03-05 05:05:55
tags: Regression, Bernoulli, Likelihood
author: yuuuuuya
---

<script type="text/javascript" src="https://leico.github.io/TechnicalNote/js/MathJax/MathJax.js?config=TeX-MML-AM_HTMLorMML"></script>

<h1>回帰問題（不連続)</h1>

<p>回帰問題：出力値と入力値のペアがある。そのペアを教師データとして入力値から出力値を予測する確率モデルを作成する。</p>

<p>出力値$t(scalor)$</p>

```math
\begin{eqnarray}
4a &=& ((a+a)+a)+a \\
&=& (a+a)+(a+a)
\end{eqnarray}
```

<p>入力値$x_N$</p>

<p>のペアがある。これらのペアは、それぞれ独立。</p>

<p>各データ点xにおける予測値y(x,w)を、パラメータw(w=[w_0,…,w_N])を用いて次のように表す。</p>

(y(x,w)=w_0 x_0+w_1 x_1+⋯+w_N x_N=w^T x#(1) )
(t= y(x,w)+a  (aは誤差))

<p>目標は、この確率モデルp(t|x)の高さを高くすることである。つまり、次の尤度関数を高くするような、パラメータwを求めたい。</p>

<p>ここでは、出力値が0 or 1であるベルヌーイ分布で考えていく。</p>
<p>尤度関数(2)を最大にするパラメータwを求めたかった。
この尤度関数に、対数をとっても、求めたいパラメータwは不変であるので、対数をとった形で考える。</p>

<p>但し、</p>

<p>しかし、ここで問題がある。
y(x,w)+aは、無限の値をとりうる。各データモデルとして扱うためには、(5)と(6)を満たす必要がある。</p>

<p>そこで、シグモイド関数の (-∞,∞)→(0,1) の単調増加関数である性質を用いて、p(t_n│x_n )を次の形で定義する。</p>
<p>(7),(8)は、(6)を満たす。(3)を確率モデルとして扱えるように改めて次のように書き換える。</p>


<p>を最大にするパラメータwとパラメータaを勾配法で求める。</p>
<p></p>
<p></p>
<p></p>
<p></p>
