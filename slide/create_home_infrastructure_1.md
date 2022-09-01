---
marp: true
theme: gaia
size: 16:9
paginate: true
headingDivider: 2
header: 自宅インフラを構築した (1) ネットワークまわりの改造
footer: 'AiTachi, GitHub:[tcbn-ai](https://github.com/tcbn-ai), Twitter: [@tcbn_ai](https://twitter.com/tcbn_ai)'
---

<style>
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
</style>

# 自宅インフラを構築した <br> (1) ネットワークまわりの改造

<!--
_class: lead
_pagenate: false
_header: ""
-->

## 目次
- きっかけと要件
- 初期環境と問題点
- ネットワークまわりの改造

## きっかけ
何故自宅インフラを構築しようと思ったのか？

- ホスト型の仮想環境を使って色々遊んでいたが、PCのスペック (メモリ、SSD) が足りず不便だった
- ネットワークとかサーバまわりをもっと知りたい
- 家のネットワークを整えたい 
- (サブスクは使いたくない。。。)

$\Rightarrow$ 家のインフラを整えれば解決じゃない？？？

---

### 要件
とりあえず、次のようなインフラを目指すことにする。

- **容易に拡張できる**
    - 機器を増やすときにあまり面倒じゃない方がうれしい
$\Rightarrow$ 最初にネットワークの大枠を決めてしまう

- **物理機器は最小限**
    - 引っ越しの手間を考えると物理機器は少なければ少ないほど良い
$\Rightarrow$ 仮想サーバーを使う

## 初期環境
よくある自宅ネットワークの構成 (つまらない)
![center height:450](../fig/ver0/network_configuration_ver0.svg)

---

![center](../fig/ver0/config_ver0.svg)

---

#### 写真

![bg width:550](../fig/ver0/img_2290-fs8.png) ![bg width:550](../fig/ver0/img_2287-fs8.png)

---

#### スペックとか
- 無線LANルーター
    - [ELECOM WRC-300FEBK](https://www.elecom.co.jp/products/WRC-300FEBK.html)
        - 販売終了してる古いやつ。高校生の頃に買った。
- デスクトップPC
    - M1で買った Lenovo のデスクトップを魔改造しながら使ってる
        - core i5 9th Gen, Mem 16GB
        - SSD2枚刺しでデュアルブートしてる
        - 安いグラボを積んだ
        - USB 3.0 のインターフェースカードを入れた 

---

#### 遊び方
- Windows にゲームを入れて遊ぶ
    - 飽きっぽいからすぐ飽きる
- Kali Linux に KVM で仮想マシンを立てて遊ぶ
    - 途中でスペックが足りないことに気付く
    - 攻撃するマシンがホストOSだと色々不便

---

#### 問題点
- PCまわり
    - 環境を作って遊ぶにはPCのスペックが足りない
    - そもそもホスト型にするメリットがあまりない
- ネットワークまわり
    - 使っている無線LANルーターが販売中止しているし変えたい
    - よくある自宅ネットワーク構成はつまらない
    - ネットワークまわりの勉強と改造をしたい

$\Rightarrow$ **サーバー構築** & **ネットワークまわりの改造**


## ネットワークまわりの改造
- 新しい (有線) ルーターを導入する
    - 1Gbps くらいほしい
    - VLAN まわりの操作が楽なのがいい

$\Rightarrow$ [tp-link ER605](https://www.tp-link.com/jp/business-networking/omada-sdn-router/er605/)：Amazon 9,283円 (2022/8/21 購入)

- 無線APを新しくする
    - 安定していて、管理者まわりの操作が容易なのがほしい

$\Rightarrow$ [NEC Aterm WG1900HP2](https://www.aterm.jp/product/atermstation/product/warpstar/wg1900hp2/)：Amazon 7,399円 (2022/8/22 購入)

---

### 構成 (ver 1.0)

![center height:550](../fig/ver1_change_network_config/network_configuration_ver1.svg)

---

![](../fig/ver1_change_network_config/config_ver1.1.svg)

---

#### 写真

![bg width:550](../fig/ver1_change_network_config/img_2295-fs8.png) ![bg height:550](../fig/ver1_change_network_config/img_2294-fs8.png)

---

#### 個人的こだわりポイント
- 仕事用と個人用のネットワークのセグメントを分けた
  - やらかしても会社端末への影響を最小限に抑えるため (VPN使ってるけどね)
- そこそこ良いルーターを使った
  - そもそもの回線があまり良くないから、引っ越しも視野に入れる

## まとめ
- 自宅のネットワークまわりを整えました。
  - ルーターを無線APを新しくした
  - 仕事用と個人用のセグメントを分けた
- 今後の予定
  - サーバー自作
