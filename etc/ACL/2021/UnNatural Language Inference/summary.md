# UnNatural Language Inference
- Paper: https://aclanthology.org/2021.acl-long.569.pdf
- Code: https://github.com/facebookresearch/UNLU
- Organization: facebook research

## どんなもの?
- 最先端の事前学習済みのTransfoerベースのNLUモデルが, ある程度, 人間と同じように文の構文を理解していることが指摘されている
- 一方で, 含意関係認識(A.k.a Natual Language Inference, NLI)において, 人間が理解できないレベルで語の順番をめちゃめちゃに入れ替えてもモデルの予測が不変であることを明らかにした
  - ![](https://github.com/facebookresearch/UNLU/raw/main/anim_30.gif)
- 本論文では, このモデルの語順不変性について検証し, はたしてモデルが本当に人間のように構文関係を理解しているといえるのかどうかを分析した

## 先行研究と比べてどこがすごい?
- 情報理論の観点から, 順序入れ替えに対してモデルがどうのように反応を示しているか, を考察している
- 順序入れ替えを行うことで, モデルの予測を正しく反転できることを示している
- 問題がTransformerに固有のものではないことを示している
- ドメイン外のデータにも同様に発生することを示している
- モデルが語順の入れ替えをどの程度受け入れるかを測る指標を提案した
- なぜ語順がモデルに受容されないのかを分析している

## 技術や手法の肝は?
- none

## どうやって有効だと検証した?
- none

## 結果は?
- NLIモデル（Transformerベースのモデル、RNN、ConvNets）は、元の構文を破壊するような語順の並べ替えにほとんど影響を受けないことが示された
- 単語の並び替えは、モデルの分類ラベルを反転させる可能性があることが示された

## 議論はある?
- none

## 次に読むべき論文は?
- Large scale pre-trained Transformer-based models have exceeded recurrent neural networks’ performance on many NLU tasks (Wang et al., 2018, 2019).
  - [GLUE: A Multi-Task Benchmark and Analysis Platform for Natural Language Understanding](https://aclanthology.org/W18-5446/)
- Transformers pretrained on a language modeling (LM) objective can capture syntactic information
  - [A Structural Probe for Finding Syntax in Word Representations](https://aclanthology.org/N19-1419/)
  - [What Does BERT Learn about the Structure of Language?](https://aclanthology.org/P19-1356/)


## 不明な単語
- 自然言語理解(Natural Language Understanding, NLU)
- 自然言語推論(Natural Language Infernece, NLI)
- "sentence superiority effect”
  - めちゃめちゃな語順の単語は覚えられない

## 感想
- 全体的に難しかった. 何のためにどんな実験をやっているのかつかめなかった.
- まったくの予想であるが, 含意関係認識タスクで語順入れ替えを行ったときに人間の正解率は下がる(人間は構文をめちゃめちゃに破壊するような語順入れ替えを施した文を理解できない)が, モデルの正解率はそれを上回ったので, モデルは文構造を見ているとは言えない(見ているとすると人間と同じような正解率になるはず), ということを言っていると思う.
