---
layout: post
cover: 'assets/images/cover/tree.jpg'
title: 勾配法
date: 2018-03-07 05:05:55
tags: gradient method
author: yuuuuuya
---
<script type="text/javascript" src="https://yuuuuuya.github.io/js/MathJax/MathJax.js?config=TeX-MML-AM_HTMLorMML"></script>

<h1>勾配法</h1>

<p>勾配法は、関数を最大値（最小値）となる解を見つけるアルゴリズム。  
最大値（最小値）付近で収束するような更新ができる。  
ちょうど、下記図のような更新になり、関数を最大にする解を見つけることができる。</p>
<img src="../assets/images/gradient_method/gradient.png" width="70%">

---------------------------------------------------------------------

<p>\\(w\in\mathbb{R}^n\\),\\(F\\)：\\(w\\)に関する関数,\\(\epsilon(学習率)>0\\)において、最大値（最小値）付近で収束する更新アルゴリズム。 </p>

\begin{eqnarray}
最大値付近で収束する更新：w^{N} = w^{N-1} + \epsilon {∇}_w F(w^{N-1})
\end{eqnarray}

\begin{align}
最小値付近で収束する更新：w^{N} = w^{N-1} - \epsilon {∇}_w F(w^{N-1})
\end{align}

----------------------------------------------------------------------

<h3>常に上がり続ける更新ができる理由</h3>

<p>\\(x\\)をベクトル。\\(f\\)は\\(x\\)に関する関数とする。</p>
<p>更新後の新しい\\(x\\)の値を\\(x_{new}\\)。更新前の古い\\(x\\)の値を\\(x_{old}\\)とする。</p>


テイラーの定理から、
\begin{align}
f(x_{new}) - f(x_{old}) \approx (x_{new} - x_{old})^T ∇ f(x_{old})
\end{align}

と近似することができる。  

上がり続ける更新をするためには、\\(f(x_{new}) - f(x_{old})\\)を大きくすれば良いから、\\((x_{new} - x_{old})^T ∇f(x_{old})\\)（右辺の勾配を）を最大にするような\\((x_{new}-x_{old})^T\\)を持ってこればいい。  
つまり、\\(x_{new} - x_{old} = ∇f(x_{old})\\)であれば、勾配が正の方向に最大の更新となる。

\begin{align}
x_{new} = x_{old} + ∇f(x_{old}) (勾配が正方向に最大となる更新)
\end{align}

逆に、常に下がり続ける更新は、\\((x_{new} - x_{old})^T ∇ f(x_{old})\\)（右辺の勾配を）を最小にするような\\((x_{new} - x_{old})^T\\)を持ってこればいい。
つまり、\\(x_{new} - x_{old} = -∇ f(x_{old})\\)であれば、勾配が負の方向に最大の更新となる。

\begin{align}
x_{new} = x_{old} - ∇f(x_{old}) (勾配が負方向に最大となる更新)
\end{align}

ここで、重要になるのが学習率\\(\epsilon\\)。
※学習率\\(\epsilon\\)が大きすぎると、最大値（最小値）を超えてしまう。そのため、例えば、数のようになってしまう。そのため、学習率\\(\epsilon\\)は慎重に決めなければいけません。

<img src="../assets/images/gradient_method/mistake.png" width="70%">

----------------------------------------------------------------------------
<h4>【テイラーの定理のおまけ】</h4>
<p>\\(x\\)をベクトル。\\(f\\)は\\(x\\)に関する関数とする。  
\\(x_{new}\\)と\\(x_{old}\\)が限りなく近い時、次の等式が成り立つ。</p>

\begin{align}
f(x_{new}) - f(x_{old}) = (x_{new} - x_{old})^T ∇ f(x')
\end{align}

\begin{align}
ただし、x' = a x_{new} + (1-a) x_{old}
\end{align}
