# Named Entity Recognition with Small Strongly Labeled and Large Weakly Labeled Data
- Paper: https://aclanthology.org/2021.acl-long.140.pdf
- Code: https://github.com/amzn/amazon-weak-ner-needle
- Organization: google

## どんなもの?
- 固有表現抽出(NER)において, 人間がラベリングを行って作成した強い教師情報はかなりコストがかかるので, 下流のNERタスクのボトルネックになっている.
- 一方でラベリングされていないデータは大量にある場合が多く, これらを機械的に自動でラベリングした弱い教師情報を作成し, この弱い教師情報からモデルを学習する方法が研究されている.
- 本研究では, 弱い教師情報だけでなく, 強い教師情報と弱い教師情報の両者を組み合わせたデータから深層モデルを学習するためのフレームワーク(NEEDLE)を提案した.

## 先行研究と比べてどこがすごい?
- 今まで組み合わせることがなかった強い教師情報と弱い教師情報を, 単に組み合わせて学習すると生じる課題を明らかにし, その課題を解決するためのフレームワークを提案しているところ.

## 技術や手法の肝は?
- 弱い教師情報がもっている2つの課題に対する解決策を考案.
  1. 不完全性(エンティティ見逃し)
     - Weak Label Completion, WLC: 弱い教師情報で学習したモデルを用いて見逃しラベルを補完
  2. ノイジーラベル(ラベルミスマッチ)
     - Noise-Aware Loss, NAL: 損失関数を提案

## どうやって有効だと検証した?
- 以下の2つのNERサブタスクで実証実験を行った.
  - E-commerce query NER
  - Biomedical NER

## 結果は?
- 以下の3つのデータセットにおいて, SOTA(F1-score)を達成した
  - BC5CDR-chem: 93.74
  - BC5CDR-disease: 90.69
  - NCBI-disease: 92.28

## 議論はある?
- none

## 次に読むべき論文は?
- [continually pre-train model on large in-domain unlabeld data](https://aclanthology.org/2020.acl-main.740.pdf)
- [weakly labeled data archive good performance](https://dl.acm.org/doi/10.1145/3394486.3403149)
- [weakly labeled data archive good performance](https://aclanthology.org/D18-1230/)

## 不明な単語
- none

## 感想
- WLC, NALの効果はあるっぽいが, 後段のFine tuningの効果に比べると小さい. 正直, Fine tuningさえすればある程度精度はでるようになるかなって感じ.
  - 実際は, stage:1の事前学習モデルを対象domainでtuningしているのと, stage:3で強い教師情報でのfine tuningの組み合わせが効いているのかな? stage:2のWLCとNALはあんま意味ないかも.
    - 一方で, 事前学習モデルを対象domainでtuningすると, 学習済みのいい感じのembeddingが崩壊する可能性があるので, あんまりしない方がいいと効いたことがある
- ちなみに使っているアーキテクチャはBERT+CRF
