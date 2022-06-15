# Leveraging Type Descriptions for Zero-shot Named Entity Recognition and Classification
- Paper: https://aclanthology.org/2021.acl-long.120/
- Code: none
- Organization: Computer Laboratory, University of Cambridge, UK

## どんなもの?
- 対象となるエンティティのクラスが学習データに含まれないという課題がある
- zero-shot learninig はこの課題に対する解決策の１つである
- 本論文は, 初めて, zero-shot learning を NERC(Named Entity Recongnition and Classification) に適応した

## 先行研究と比べてどこがすごい?
- none

## 技術や手法の肝は?
- 文とクラスディスクリプションをcross-attentionで結合しているところ
- 学習時にnegativeなtokenが, test時に何かしらのpositiveクラスを持っている場合があり, この状況に対応するためにnegative classをモデリングしている

## どうやって有効だと検証した?
- OnteNotesとMedMentionsという２つデータセットで macro f1 score を比較する実証実験を行った

## 結果は?
- 提案した方法がOntoNotesで0.45, MedMentionsで0.38を達成した
- これはMRC(Machine Reading Comprehension), zero-shot text classificationで適用されている手法よりも圧倒的に優れている

## 議論はある?
- none

## 次に読むべき論文は?
- none

## 不明な単語
- MRC, machine reading comprehension
  - 質問応答において, 答えのない質問に対して答えがないことを識別するタスク
  - https://anlp.jp/proceedings/annual_meeting/2018/pdf_dir/P7-22.pdf
- ner subtask
  - entity linking
  - named entity typing
- cross-attention
  - When attention is performed on queries, keys and values generated from same embedding is called self attention.
  - When attention is performed on queries generated from one embedding and keys and values generated from another embeddings is called cross attention

## 感想
- 問題設定が難しいし, 実際macro f1はよくても0.45しかない. やはり, 学習データに含まれないクラスをtest時に識別するのは難しいね.
- テストデータのクラスディスクリプションを入力に想定しているが, そもそも学習データで想定していないクラスは未知である場合が多いのでは? この論文では, 学習データに含まれないが, テストデータには出現することがわかっているクラスがあること, を想定している.
- クラスディスクリプションを定義するのも面倒くさそう
  - クラスディスクリプションの定義の質で精度も変わってきそう
- クラス定義をミーシーにするための方法があると面白そう
  - entityっぽいものをひたすら抽出して提示するみたいな
