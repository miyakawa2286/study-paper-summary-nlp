# Title
- Paper: Don’t Stop Pretraining: Adapt Language Models to Domains and Tasks
- Code: https://github.com/allenai/dont-stop-pretraining
- Organization: Allen Institute for AI

## どんなもの?
- NLPの世界では, 事前学習済みの言語モデルが幅広い分野で多くの成功をもたらしている
- 本研究では, 対象タスクの領域で事前学習を継続して行うことがモデルのパフォーマンスにどう影響するかを調査した

## 先行研究と比べてどこがすごい?
- none

## 技術や手法の肝は?
- none

## どうやって有効だと検証した?
- 以下の4つの異なるドメインのデータセットを用いて分類問題を解く実証実験を行った
  - biomedical
  - computer science
  - newstext
  - anmazon reviwes
- また以下の通り, 継続的事前学習の設定を３つ設けた
  - Domain Adaptive Pre-Training, DAPT
  - Task Adaptive Pre-Training, TAPT
  - Augmenting Training Data for Task Adaptive Pretraining

## 結果は?
- DAPT, TAPTそれぞれにおいて, すべてのデータセットで分類精度が向上した
- DAPTとTAPTそれぞれ単体で使用するよりも組み合わせることで精度がより上昇することが示されており, とくにCSのACL-ARCデータセットにおいては, baselineの精度63.0%から75.6%と大きく上回った.
- TAPTにおいて, データ拡張を取り入れることで精度が上昇することが示された.

## 議論はある?
- none

## 次に読むべき論文は?
- none

## 不明な単語
- none

## 感想
- DAPTとTAPTの違いがよくわからなかった. 教師あり情報が付与されたデータでLMを学習するのがTAPT? Table.9でcomputational recuirementsの議論があり,　必要なstrorageが示されているがDPATのstorageがでかすぎる. 学習するパラメータは同じではないのかな?
- 両者の違いはわからなかったが, とりあえず, pre-trainingを下流タスクで継続することは有効らしいということはわかった.
- モデルはRoBERTaってやつを使っている
- 事前学習やってみたい
