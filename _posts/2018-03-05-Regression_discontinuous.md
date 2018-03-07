---
layout: post
cover: 'assets/images/cover/tree.jpg'
title: 回帰問題（不連続:ベルヌーイ）
date: 2018-03-05 05:05:55
tags: Regression Likelihood
author: yuuuuuya
---

<script type="text/javascript" src="https://yuuuuuya.github.io/js/MathJax/MathJax.js?config=TeX-MML-AM_HTMLorMML"></script>

<h1>回帰問題（不連続：ベルヌーイ）</h1>

<p>回帰問題：出力値と入力値のペアがある。そのペアを教師データとして入力値から出力値を予測する確率モデルを作成する。</p>
出力値\\(t(=0 or 1)\\)と入力値\\(\textbf{x}(\textbf{x}=[x_1,…,x_N])\\)のペアがある。それぞれのペア同士、独立でベルヌーイ分布に従うとする。  
各データ点\\(\textbf{x}\\)における予測値\\(y(\textbf{x},\textbf{w})\\)を、パラメータ\\(\textbf{w}(\textbf{w}=[w_0,…,w_N]),a\\)を用いて次のように表す。

<p>\\(y(\textbf{x},\textbf{w})=w_0x_0+w_1x_1+⋯+w_Nx_N=\textbf{w}^T\textbf{x}\tag{1}\\)</p>

<p>\\(t= y(\textbf{x},\textbf{w})+a  (aは誤差)\tag{2}\\)</p>

\\(\textbf{x}\\)を見た時に、特定の\\(t\\)を見る、確率モデル\\(p(t|\textbf{x})\\)を作っていく。  
目標は、この確率モデル\\(p(t|\textbf{x})\\)の高さを高くすることである。  
※確率モデルは高さを高くする（分散が小さくする）ほど、予測値の確率が高くなり、予測が外れにくくなる。

つまり、データは独立であるので、次の尤度関数を高くすればいい。

\begin{align}
\prod_{n=1}^N p(t|\textbf{x}_n)\tag{3}
\end{align}

ここで、(1)、(2)から、予測値はパラメータ\\(\textbf{w}\\)の関数で表すことができ、誤差も考えると、(3)の尤度関数は、パラメータ\\(\textbf{w}\\)と\\(a\\)の関数であることがわかる。
そのため、次のように書き換えることができる。

\begin{align}
\prod_{n=1}^N p(t|\textbf{x}_n,\textbf{w},a)\tag{4}
\end{align}


尤度関数(4)を最大にするパラメータ\\(\textbf{w}\\)と\\(a\\)を求める。そのため、尤度関数(3)に、対数をとった対数尤度関数で求めていく。  
対数尤度関数で考えられる理由は、対数関数は増加関数であり、尤度関数(4)に対数をとっても、尤度関数(4)を最大にするパラメータ\\(\textbf{w}\\),\\(a\\)は不変であるからである。


\begin{align}
\log\prod_{n=1}^Np(t|\textbf{x}_n,\textbf{w},a)\tag{5}
\end{align}

対数の性質から、(4)は次のように変形できる。

\begin{align}
\sum_{n=1}^N \log p(t|\textbf{x}_n,\textbf{w},a)\tag{6}
\end{align}

しかし、ここで問題がある。
\\(y(\textbf{x},\textbf{w})+a\\)は、パラメータ\\(w\\)と\\(a\\)に制限がないので、無限の値をとりうる。そのため、確率の領域で各データモデルとして扱うためには、次の(7)と(8)を満たす必要がある。

\begin{align}
0 \le y(\textbf{x},\textbf{w})+a \le 1\tag{7}
\end{align}

\begin{align}
p(t=1|\textbf{x}_n,\textbf{w},a)+p(t=0|\textbf{x}_n,\textbf{w},a)=1\tag{8}
\end{align}

<p>そこで、シグモイド関数の \\((-∞,∞)→(0,1)\\)の単調増加関数である性質を用いて\\(p(t|\textbf{x}_n,\textbf{w},a)\\)を次の形で定義する。</p>

\begin{align}
p(t=1|\textbf{x}_n,\textbf{w},a)=\frac{1}{1+\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}\tag{9}
\end{align}

\begin{align}
p(t=0|\textbf{x}_n,\textbf{w},a)=\frac{\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}{1+\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}\tag{10}
\end{align}

<p>(9),(10)は、(7),(8)を満たす。(6)を確率モデルとして扱えるように改めて次のように書き換える。</p>

\begin{align}
\sum_{n=1}^N \log (\frac{1}{1+\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}+\frac{\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}{1+\mathrm{e}^{y(\textbf{x},\textbf{w})+a}})\tag{11}
\end{align}

(9)を最大にするパラメータ\\(\textbf{w}\\),\\(a\\)を勾配法で求める。
