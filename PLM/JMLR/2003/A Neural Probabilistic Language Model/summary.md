# A Neural Probabilistic Language Model
- Paper: https://www.jmlr.org/papers/volume3/bengio03a/bengio03a.pdf
- Code: none
- Organization: RALI(Recherche appliquée en linguistique informatique – Applied research in computational liguistics) laboratory, Université de Montréal(モントリオール大学), Canada
- Author: Bengio
- Year: 2003

## どんなもの?
- A goal of statistical language modeling is to learn the joint probability function of sequences of words in a language.
- This is intrinsically difficult because of the **curse of dimensionality**:
  - a word sequence on which the model will be tested is likely to be different from all the word sequences seen during training.
- Traditional but very successful approaches based on **n-grams** obtain generalization by concatenating very short overlapping sequences seen in the training set.
- We propose to fight the curse of dimensionality by **learning a distributed representation(分散表現) for words** which allows each training sentence to inform the model about an exponential number of semantically neighboring sentences.
  - Generalization is obtained because a sequence of words that has never been seen before gets high probability if it is made of words that are similar (in the sense of having a nearby representation) to words forming an already seen sentence.
  - **Training such large models (with millions of parameters) within a reasonable time** is itself a significant challenge.
    - Another contribution of this paper concerns the challenge of training such **very large neural networks** (with millions of parameters) for **very large data sets** (with millions or tens of millions of examples).
- We report on experiments using **neural networks** for the probability function, showing on two text corpora that the proposed approach significantly **improves on state-of-the-art n-gram models**, and that the proposed approach allows to **take advantage of longer contexts**.
- More generally, the work presented here **opens the door to improvements in statistical language models brought by replacing “tables of conditional probabilities” by more compact and smoother representations based on distributed representations that can accommodate far more conditioning variables**. Whereas much effort has been spent in statistical language models (e.g. stochastic grammars) to restrict or summarize the conditioning variables in order to avoid overfitting, the type of models described here **shifts the difficulty elsewhere**: many more computations are required, but computation and memory requirements scale linearly, not exponentially with the number of conditioning variables.

### 次元の呪い
- It is particularly obvious in the case when one wants to model the joint distribution between many **discrete random variables** (such as words in a sentence, or discrete attributes in a data-mining task).
- For example, if one wants to model the joint distribution of 10 consecutive words in a natural language with a vocabulary V of size 100,000, there are potentially 10000010 − 1 = 1050 − 1 free parameters.
- When modeling **continuous variables**, we obtain generalization more easily (e.g. with smooth classes of functions like multi-layer neural networks or Gaussian mixture models) because the function to be learned can be expected to have some local smoothness properties.
- For discrete spaces, the generalization structure is not as obvious: **any change of these discrete variables may have a drastic impact on the value of the function to be estimated**, and when the number of values that each discrete variable can take is large, most observed objects are **almost maximally far from each other in hamming distance**.

### n-gram modelの改善点
- There are at least two characteristics in this approach which beg to be improved upon, and that we will focus on in this paper.
  - First, **it is not taking into account contexts farther than 1 or 2 words**
  - second **it is not taking into account the “similarity” between words**.
- For example, having seen the sentence “The cat is walking in the bedroom” in the training corpus should help us generalize to make the sentence “A dog was running in a room” almost as likely, simply because “dog” and “cat” (resp. “the” and “a”, “room” and “bedroom”, etc...) have similar semantic and grammatical roles.

## 先行研究と比べてどこがすごい?
- none

## 技術や手法の肝は?
- none

## どうやって有効だと検証した?
- none

## 結果は?
- none

## 次に読むべき論文は?
- What happens when a new combination of n words appears that was not seen in the training corpus?
  - back-off trigram models (Katz, 1987)
  - smoothed (or interpolated) trigram models (Jelinek and Mercer, 1980)
- The idea of using neural networks to model high-dimensional discrete distributions has already been found useful to learn the joint probability of Z1 ···Zn,
  - Experiments on four UCI data sets show this approach to work comparatively very well (Bengio and Bengio, 2000a,b).

## 不明な単語
- none

## 感想
### 2022/6/14
- 読みづらかった
  - 難しい用法が多い...
  - 先行研究との比較で苦戦
    - 先に提案を読んだほうがわかりやすいかも
    - いまどっちもよくわかってないから
- 1.2途中まで読んだ
- 分布仮説っぽいアイデア
- 従来のn-gram based言語モデルの次元呪い問題に注目
- 言語モデルにニューラルネットワークを使った初の試みだと思っていたが, ニューラルネットワークを使うこと自体は既出っぽい
- 気になった文:
  - 1.:: Typically researchers have used n = 3, i.e. trigrams
