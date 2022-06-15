# Language Models are Unsupervised Multitask Learners
- Paper: https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf
- Code: 
- Organization: OpenAI
- Author: Radford et el
- Year: 2019

## どんなもの?
- We demonstrate language models can perform down-stream tasks in a **zero-shot** setting – without any parameter or architecture modification.
- GPR-2
  - 1.5GB parameters
- achieves SOTA results on 7 out of 8 tested language modeling datasets in a **zero-shot** setting but still underfits WebText.
- Samples from the model reflect these improvements and contain **coherent paragraphs of text**.
- When a large language model is trained on a **sufficiently large and diverse** dataset it is able to perform well across many domains and datasets.
  - ゼロショット設定においてモデルが実行できるタスクの多様性は, **十分に多様なテキストコーパスの尤度を最大化するように学習**された言語モデルが, **教師情報を必要とせずに驚くほど多くのタスクの実行方法を学習し始める**ことを示唆している.

### Pre-training and supervised fine-tuning apporach history
1. **word vectors** were learned and used as inputs to task-specific architectures (Mikolov et al., 2013) (Collobert et al., 2011)
2. contextual representations of **recurrent networks** were transferred (Dai & Le, 2015) (Peters et al., 2018)
3. task-specific architectures are no longer necessary and transferring many **self-attention blocks** is sufficient (Radford et al., 2018) (Devlin et al., 2018).

### Training Dataset
- 十分に多様性をもったデータセットを構築するために, scraping(Common Crawl)を使用.
- ただしCommon Crawlで得られたデータの品質はいまいち.
- そこでクローラーから得られたデータを人手でチェックした. ただしすべてのデータを人手でチェックするのはめちゃくちゃ時間がかかるので, 以下のように進めた.
  - Redditから少なくとも3karma?を受け取ったすべてのリンクをスクレイピング.
    -  a heuristic indicator for whether other users found the link interesting, educational, or just funny.
  - The resulting dataset, WebText, contains the text subset of these **45 million links**.
  - To extract the text from HTML responses we use a combination of the
    - Dragnet (Peters & Lecocq, 2013)
    - Newspaper content extractors
  - All results presented in this paper use a preliminary version of WebText which
    - does not include links created after Dec 2017
    - de-duplication
    - some heuristic based cleaning
  - contains slightly over **8 million documents** for a total of **40 GB of text**.
  - We removed all Wikipedia documents from WebText
    - since it is a common data source for other datasets
    - could complicate analysis due to overlapping training data with test evaluation tasks

### Input Representation
- Current large scale LMs include pre-processing steps such as
  - lowercasing
  - tokenization
  - out-of-vocabulary tokens 
    - which restrict the space of model-able strings.
- While processing **Unicode strings** as a sequence of UTF-8 bytes elegantly fulfills this requirement as exemplified in work such as Gillick et al. (2015)
- current byte-level LMs are not competitive with word-level LMs on large scale datasets such as the One Billion Word Benchmark (Al-Rfou et al., 2018).
- Byte Pair Encoding, BPE(Sennrich et al., 2015)
  -  practical middle ground between character and word level language modeling which effectively interpolates between
     -  word level inputs for frequent symbol sequences
     -  character level inputs for infrequent symbol sequences
  - Despite its name, reference BPE implementations often **operate on Unicode code points** and **not byte sequences**.

## 先行研究と比べてどこがすごい?
- none

## 技術や手法の肝は?
- タスクの条件付け方法
  - 通常は, 例えばタスクごとに異なるアーキテクチャを使用してp(output|input)をそれぞれでモデリングする.
  - ここでは, タスクを条件付き確率に直接組み込む. つまり, p(output|input, task)をモデリングする.
  - これは言語データが柔軟性を持っており, **データの中でタスクを指定する**ことを可能にする, という特性による.
    - inspired by McCann et al. (2018)
      - (translate to french, english text, french text)
      - (answer the question, document, question, answer)
  - また明示的に教師情報を付け足す必要がない

## どうやって有効だと検証した?
- none

## 結果は?
- none

## 次に読むべき論文は?
- McCann et al. (2018), MQAN

## 不明な単語
- none

## 感想
- 就活のせいで集中できず, あまり読み進められなかった.
- 1章の"This motivates exploring additional setups for performing multitask learning"の部分, よくわからなかった.
- 2.2章のBPEのところまで読んだ.
- GPTと聞くと, 意味的に一貫性のある自然な文を生成することができるモデル, という印象が強いが, GPT-1,2は読んだ感じ, テキスト生成のパフォーマンスをあまりフィーチャーしてない.
  - GPT-1はPretraining->supervised fine-tuningモデル, 転移しやすい枠組み
  - GPT-2はtaskに依存しないzero-shotモデルは, 多様なデータセットと巨大な言語モデルがあれば実現できる.
