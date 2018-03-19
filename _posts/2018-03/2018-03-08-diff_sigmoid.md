---
layout: post
cover: 'assets/images/cover/tree.jpg'
title: ”シグモイド関数”・”シグモイド関数の対数”の微分
date: 2018-03-08 1:00:00
tags: sigmoid differential
author: yuuuuuya
---
<script type="text/javascript" src="https://yuuuuuya.github.io/js/MathJax/MathJax.js?config=TeX-MML-AM_HTMLorMML"></script>

<p>変数\\(z\\)に対するシグモイド関数を次のように定義する。</p>
出力値\\(t=0\\)を予測する確率モデルを
\begin{eqnarray}
\sigma(z)=\frac{1}{1+\exp⁡(-z)}\tag{1}
\end{eqnarray}

<p>出力値\\(t=1\\)を予測する確率モデルを
\begin{eqnarray}
\sigma(z)=\frac{\exp(-z)}{1+\exp⁡(-z)}\tag{2}
\end{eqnarray}
とする。</p>
---------------------------------------------------------------------------------------------------------
<h2>”シグモイド関数”の微分</h2>
<h4>__出力値\\(t=0\\)を予測する確率モデル(1)を\\(z\\)に関して微分。__</h4>
\begin{align}
\frac{d\sigma(z)}{dz} &= \frac{1}{dz} \cdot \frac{1}{1+\exp⁡(-z)}\\\
&= \frac{1}{dz} (1+\exp(-z))^{-1}\\\
&= -\exp(-z) \cdot -\bigl(1+\exp(-z)\bigr)^{-2}\\\
&=  \frac{\exp(-z)}{\bigl(1+\exp(-z)\bigr)^{2}}\tag{3}
\end{align}


<h4>__出力値\\(t=1\\)を予測する確率モデル(2)を\\(z\\)に関して微分。__</h4>
\begin{align}
\frac{d\sigma(z)}{dz} &= \frac{\exp(-z)}{1+\exp⁡(-z)}\\\
&= -\exp(-z) \cdot \frac{1}{1+\exp⁡(-z)} + \exp(-z) \cdot \frac{\exp(-z)}{\bigl(1+\exp(-z)\bigr)^{2}} \qquad (3)より\\\
&= \frac{-\exp(-z)-\exp(-z)^2 + \exp(-z)^2}{\bigl(1+\exp(-z)\bigr)^{2}}\\\
&= \frac{-\exp(-z)}{\bigl(1+\exp(-z)\bigr)^{2}}\tag{4}
\end{align}

---------------------------------------------------------------------------------------------------------

<h2>”シグモイド関数の対数”の微分</h2>
<h4>__出力値\\(t=0\\)を予測する確率モデル(1)の対数を\\(z\\)に関して微分。__</h4>
\begin{align}
y=\log {\sigma} \qquad \sigma =\frac{1}{1+\exp⁡(-z)}
\end{align}
と置く。


\begin{align}
\frac{dy}{d\sigma} \cdot \frac{d\sigma}{dz} &= \frac{1}{\sigma} \cdot \frac{\exp(-z)}{\bigl(1+\exp(-z)\bigr)^{2}} \qquad (3)より\\\
&= (1+\exp⁡(-z)) \cdot \frac{\exp(-z)}{\bigl(1+\exp(-z)\bigr)^{2}}\\\
&= \frac{\exp(-z)}{1+\exp(-z)}
\end{align}


<h4>__出力値\\(t=1\\)を予測する確率モデル(2)の対数を\\(z\\)に関して微分。__</h4>
\begin{align}
y=\log {\sigma} \qquad \sigma =\frac{\exp⁡(-z)}{1+\exp⁡(-z)}
\end{align}
と置く。


\begin{align}
\frac{dy}{d\sigma} \cdot \frac{d\sigma}{dz} &= \frac{1}{\sigma} \cdot \frac{-\exp(-z)}{\bigl(1+\exp(-z)\bigr)^{2}} \qquad (4)より\\\
&= \frac{1+\exp⁡(-z)}{\exp⁡(-z)} \cdot \frac{-\exp(-z)}{\bigl(1+\exp(-z)\bigr)^{2}}\\\
&= \frac{-1}{1+\exp(-z)}
\end{align}
