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

<p>\\(y(\textbf{x},\textbf{w})=w_0x_0+w_1x_1+⋯+w_Nx_N=\textbf{w}^T\textbf{x}\tag{1}\\)</p>

<p>\\(t= y(\textbf{x},\textbf{w})+a  (aは誤差)\tag{2}\\)</p>

<p>\\(\textbf{x}\\)を見た時に、特定の\\(t\\)を見る、確率モデル\\(p(t|y(\textbf{x}.\textbf{w}))\\)を作っていく。</p>
<p>目標は、この確率モデル\\(p(t|\textbf{x},\textbf{w})\\)の高さを高くすることである。つまり、次の尤度関数を高くするような、パラメータ\\(w\\)を求めたい。</p>

\begin{align}
\prod_{n=1}^N p(t|\textbf{x}_n,\textbf{w})\tag{3}
\end{align}

<p>ここでは、出力値が0 or 1であるベルヌーイ分布で考えていく。</p>
<p>尤度関数(3)を最大にするパラメータ\\(w\\)を求めたかった。
この尤度関数に、対数をとった対数尤度関数を考える。その理由は、対数関数は増加関数であるため、尤度関数（３）に対数をとっても、尤度関数（３）を最大にするパラメータ\\(w\\)は不変であるからである。</p>

\begin{align}
\log \prod_{n=1}^N p(t|\textbf{x}_n,\textbf{w})=
\sum_{n=1}^N \log p(t|\textbf{x}_n,\textbf{w})\tag{4}
\end{align}

<p>但し、</p>
<p>しかし、ここで問題がある。
\\(t= y(\textbf{x},\textbf{w})+a\\)は、無限の値をとりうる。各データモデルとして扱うためには、(5)と(6)を満たす必要がある。</p>

\begin{align}
0 \le y(\textbf{x},\textbf{w})+a \le 1\tag{5}
\end{align}

\begin{align}
p(t=1|\textbf{x}_n,\textbf{w})+p(t=0|\textbf{x}_n,\textbf{w})=1\tag{6}
\end{align}

<p>そこで、シグモイド関数の \\((-∞,∞)→(0,1)\\)の単調増加関数である性質を用いて、\\(p(t|\textbf{x}_n,\textbf{w})\\)を次の形で定義する。</p>

\begin{align}
p(t=1|\textbf{x}_n,\textbf{w})=\frac{1}{1+\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}\tag{7}
\end{align}

\begin{align}
p(t=0|\textbf{x}_n,\textbf{w})=\frac{\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}{1+\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}\tag{8}
\end{align}

<p>(7),(8)は、(6)を満たす。(3)を確率モデルとして扱えるように改めて次のように書き換える。</p>

\begin{align}
\sum_{n=1}^N \log (\frac{1}{1+\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}+\frac{\mathrm{e}^{y(\textbf{x},\textbf{w})+a}}{1+\mathrm{e}^{y(\textbf{x},\textbf{w})+a}})\tag{9}
\end{align}

<p>(9)を最大にするパラメータ\\(w\\)とパラメータ\\(a\\)を勾配法で求める。</p>
