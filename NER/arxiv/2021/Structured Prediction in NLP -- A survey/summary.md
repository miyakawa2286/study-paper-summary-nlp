# Structured Prediction in NLP -- A survey
- Paper: https://arxiv.org/abs/2110.02057
- Code: 
- Organization: Indian Institute of Technology Kanpur, India

## どんなもの?
- NLPにおけるstructured predictionという分野において, 主要な手法を簡潔にまとめている

## 先行研究と比べてどこがすごい?
- none

## 技術や手法の肝は?
- none

## どうやって有効だと検証した?
- none

## 結果は?

### task例
- POS tagging
- syntactic dependency parsing
- NER
- machine translation
- coreference resolution

### 主に使用されるモデル
- Hidden Markov Model, HMM
  - exposure bias problem?
    - 学習時には常に正解があたえられるが, 推論時には自身が予測した値が次の入力として与えられるという問題[参考, slide no 5](https://www.slideshare.net/DeepLearningJP2016/d-lhacks-0804pdf-78526975)
- Maximum Entropy Markov Model, MEMM
  - label bias
- Conditional Random Field, CRF
  - no label bias
  - 分配関数(規格化定数)の計算が大変?
    - Baum-Welch algorithm, 前向きアルゴリズム
- Structured Perceptron
- Structured SVM
  - no exposure bias problem
  - no label bias
- Structured Prediction Energy Network, SPEN
- これ以降もあるが, とりあえずここまで

## 次に読むべき論文は?
- none

## 不明な単語
- coreference resolution

### 確率過程
- 時間とともに変化する確率変数のこと

### マルコフ性
- 確率過程の持つ特性の一種で, 将来状態の条件付き確率分布が、現在状態のみに依存し、過去のいかなる状態にも依存しない特性
- 状態遷移行列がまさにそのように定義されており, 唯一のモデルパラメータである

### マルコフ過程
- マルコフ性をもつ確率過程のこと
  - 単純マルコフ過程
    - 現在状態のみから将来状態が決定されるマルコフ過程
  - N階(N重)マルコフ過程
    - 連続したN個の状態から将来状態が決定されるマルコフ過程
    - N=1のとき, 単純マルコフ過程
  - 離散/連続時間マルコフ過程
  - 離散/連続マルコフ過程

### マルコフ連鎖
- マルコフ連鎖の１種で, とりうる状態が離散的なもの（離散状態マルコフ過程）をいう
- また特に、時間が離散的なものを指すことが多い

### 隠れマルコフモデル
- 観測されない（隠れた）状態をもつマルコフ過程である
- 状態は観測されないが, 出力は観測されている

### Beam-search
- 系列推論で使用されるアルゴリズム
- 深さ優先探索と幅優先探索のいいところどり
- 幅優先探索をする際にすべてを考慮すると計算が終わらないので、その場の深さで評価値が良い方から順に上位数個の選択肢のみを考慮する
- Exposure biasの対応策?

## 感想
- 隠れマルコフモデルってカルマンフィルタと関係ありそうだね
- 似たような言葉で, マルコフ確率場がある. 確率場という概念がよくわからないが, これは確率的グラフィカルモデルの1種らしい. 条件付き確率場もグラフィカルモデルの１種?
