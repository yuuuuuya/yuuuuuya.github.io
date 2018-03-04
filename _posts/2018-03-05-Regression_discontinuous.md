---
layout: post
cover: 'assets/images/cover/tree.jpg'
title: 回帰問題（不連続）
date: 2018-03-05 05:05:55
tags: Regression Bernoulli Likelihood
author: yuuuuuya
---

<script type="text/javascript" src="https://yuuuuuya.github.io/js/MathJax/MathJax.js?config=TeX-MML-AM_HTMLorMML"></script>

<h1>回帰問題（不連続:ベルヌーイ)</h1>

<p>回帰問題：出力値と入力値のペアがある。そのペアを教師データとして入力値から出力値を予測する確率モデルを作成する。</p>
<p>出力値\\(t(scalor)\\)と入力値\\(\textbf{x}(\textbf{x}=[x_1,…,x_N])\\)のペアがある。それぞれのペア同士、独立とする。</p>
<p>各データ点\\(\textbf{x}\\)における予測値\\(y(\textbf{x},\textbf{w})\\)を、パラメータ\\(\textbf{w}(\textbf{w}=[w_0,…,w_N])\\)を用いて次のように表す。</p>

<p>\\(y(\textbf{x},\textbf{w})=w_0x_0+w_1x_1+⋯+w_Nx_N=\textbf{w}^T\textbf{x}\\)</p>

<p>\\(t= y(\textbf{x},\textbf{w})+a  (aは誤差)\\)</p>


\begin{align}
\zeta(s) &= \sum_{n=1}^{\infty} \frac{1}{n^s} \\
&= \prod_p \frac{1}{1-p^{-s}}
\end{align}



<p>\\(\textbf{x}\\)を見た時に、特定の\\(t\\)を見る、確率モデル\\(p(t|y(\textbf{x}.\textbf{w}))\\)を作っていく。</p>
<p>目標は、この確率モデル\\(p(t|\textbf{x},\textbf{w})\\)の高さを高くすることである。つまり、次の尤度関数を高くするような、パラメータ\\(w\\)を求めたい。</p>

\begin{align}
\prod_n \frac{p(t|\textbf{x},\textbf{w})}
\end{align}

<p>\\(\prod_n \frac{p(t|\textbf{x},\textbf{w})}\\)</p>

<p>\\(
\begin{align}
\prod_n \frac{p(t|\textbf{x},\textbf{w})}}
\end{align}\\)</p>

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
