# Vocabulary Learning via Optimal Transport for Neural Machine Translation
- Paper: https://aclanthology.org/2021.acl-long.571.pdf  
- Code: https://github.com/Jingjing-NLP/VOLT
- Organization: bytedance(china)

## どんなもの?
- トークンボキャブラリーの選択は、機械翻訳のパフォーマンスに影響を与えます
- 学習の試行錯誤なしに最適なサイズで辞書を構築するVOLTと呼ばれる手法を提案した
- WMT-14 English-German, TED's 52を含む様々な翻訳問題で従来手法よりも優っていることを実験的に示した

## 先行研究と比べてどこがすごい?
- 計算コストが小さいところ
  - 単に学習を試行錯誤し最適なサイズを探索する方法は計算コストが大きい
- 頻度だけではなく, サイズを考慮した辞書構築方法であるところ
  - BPEやSentencePieceのような従来手法には辞書サイズを考慮する枠組みがない
- 実際には便宜上, 30K-40K程度のvocablaryが採用されていることが多い
  - ただし適切なサイズであることは保障されていない

## 技術や手法の肝は?
- 最適な辞書構築問題を最適輸送問題として定式化し, 線形計画法を用いて多項式時間で解いている

## どうやって有効だと検証した?
- 複数の翻訳タスクにおける精度(BLEU)を評価しBPEと比較する実証実験を行った

## 結果は?
- WMT-14 英語-ドイツ語やTED's 52の様々なシナリオで、VOLTは広く使われているボキャブラリーを上回る性能を示した
- 例えば 英語-ドイツ語翻訳において，VOLTはボキャブラリー数を70%削減し，0.5BLEUの向上を達成した
- BPE-Searchと比較すると, 計算コストを384 GPU hoursから30 GPU hoursに短縮した

## 議論はある?
- none

## 次に読むべき論文は?
- word-level vocablary
- byte-lebel approach
- character-lebel approach
- sub-word approach
  - Byte-Pair Encoding
    - variants
      - BPE-dropout
      - SentencePiece
- practical solutions to reduce computational cost and find optimal vocablary size

## 不明な単語
- Byte-Pair Encoding, BPE
  - sub-word approach
  - 広く使われている辞書構築手法
  - ざっくりいうと, もっとも頻度の高いsub-wordをvocablary tokenとして採用する方法
- BLEU
- 最適輸送問題
- 線形計画法
- 多項式時間
- Marginal Utility
  - economics
- パレート最適化
