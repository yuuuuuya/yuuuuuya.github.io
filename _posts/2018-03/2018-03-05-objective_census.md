---
layout: post
cover: 'assets/images/cover/tree.jpg'
title: 今後の目標”人口調査の推定”
date: 2018-03-05 05:15:55
tags: Census　Data Estimation objective
author: yuuuuuya
---
<script type="text/javascript" src="https://yuuuuuya.github.io/js/MathJax/MathJax.js?config=TeX-MML-AM_HTMLorMML"></script>


<p>[datatraining](../assets/data/census_data/datatraining.txt)\\
[datatest](../assets/data/census_data/datatest.txt)\\
[datatest2](../assets/data/census_data/datatest2.txt)</p>

今後は、この"datatraining"を使って、そこに人がいるかを推定する確率モデルの作成を目標にする。
datatrainingには、"date","Temperatur","Humidity","Light","CO2","HumidityRatio","Occupancy"で１つのデータでが8143個ある。\\
__※これらのデータは、それぞれ独立。__

```python
import pandas as pd
df = pd.read_csv('datatraining.txt', sep = ',' )
df.head()
```
でdatatraing上の方を見ると次のようになっている。
<img src="../assets/images/census_img/datatraining_head.png" width="100%">
__※"Occupancy"における、1は人がいる。0は人はいないことを表している。__

今後は、"Temperature","Humidity","Light","CO2","HumidityRatio"を入力データ。"Occupancy"を出力データとし、
入力データから、出力データ（人がいるかどうか）を推定する確率モデルを作成していく（回帰問題）。

<h3>1.ベルヌーイ分布の回帰問題（準備・考え方）</h3>
データは互いに独立で、人が【いる】or【いない】の２種類の結果を予測したい。そのため、統計量はベルヌーイ分布に従うと考えるべきである。

<h3>2.勾配法（準備・考え方）</h3>
尤度関数を高くするパラメータを求める手法の1つ。

<h3>3.”シグモイド関数”と”シグモイド関数の対数”の微分（勾配法のための準備）</h3>

<h3>4.関数のコードを作成</h3>

<h3>5.データの準備</h3>
