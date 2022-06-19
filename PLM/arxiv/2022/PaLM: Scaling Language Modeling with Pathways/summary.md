# PaLM: Scaling Language Modeling with Pathways
- Paper: https://arxiv.org/abs/2204.02311
- Code: 
- Organization: Google Rereach
- Author: Chowdhery et el
- Year: Apr, 2022

## どんなもの?
- Large language models have been shown to achieve remarkable performance across a variety of natural language tasks using **few-shot learning**, which drastically reduces the number of task-specific training examples needed to adapt the model to a particular application.
- To further our understanding of the **impact of scale on few-shot learning**, we trained a **540-billion parameter**, densely activated, Transformer language model, which we call **Pathways Language Model (PaLM)**.
  - a 540B parameter dense Transformer language model trained on 780B tokens of high-quality, diverse text
- We trained PaLM on **6144 TPU v4 chips using Pathways**, a new ML system which **enables highly efficient training across multiple TPU Pods**
- On a number of these tasks, PaLM 540B achieves breakthrough performance, **outperforming the finetuned stateof-the-art on a suite of multi-step reasoning tasks**, and **outperforming average human performance** on the recently released **BIG-bench** benchmark.
  - BIG-bench containing **150+** challenging new language tasks
  - **PaLM 5-shot** achieves higher performance than the average performance score of humans who were asked to complete the same tasks.
- A significant number of BIG-bench tasks showed **discontinuous improvements** from model scale, meaning that performance steeply increased as we scaled to our largest model.
- PaLM also has strong capabilities in **multilingual tasks** and **source code generation**, which we demonstrate on a wide array of benchmarks.
### モデルの性能はまだ頭打ちになっていない可能性がある. つまり, よりモデルをスケーリングすれば性能はもっとよくなるかもしれない.
- We additionally provide a comprehensive analysis on **bias and toxicity**, and study the extent of **training data memorization** with respect to model scale.
- From these results, we can draw a number of conclusions.
  - First, the results presented here suggest that the improvements from scale for few-shot language understanding have not yet **plateaued**.
#### モデルの予測性能にモデル自身が出力した根拠?が大きく寄与している? 推論プロセスが見直されてタスク依存のモデルのフレームワークも変わってくるかも!
  - Second, the breakthrough performance on reasoning tasks (Section 6.3) has critical implications.
    - It is obvious that **a model being able to generate natural language to explain its predictions is beneficial** to the end user of a system, in order to better understand why a model made a certain prediction.
    - However, these results go far beyond that, demonstrating that **prompting the model to generate explicit inference chains can drastically increase the quality of the predictions themselves**.
    - In other words, **the model’s generation (rather than just understanding) capabilities can be immensely beneficial even for tasks that are modeled as categorical prediction or regression**, which typically do not require significant language generation.
### 今回はとりあえずwell-estabilishdなアーキテクチャを選択したが, 今後はアーキテクチャを探索してPathwaysと組み合わせたい
- Finally, although we achieved our goal of pushing the boundaries of scale for few-shot language modeling, there are still many open questions about the ideal network architecture and training scheme for future generations of models.
  - PaLM is only the first step in our vision towards establishing **Pathways as the future of ML scaling at Google and beyond**.
  - To that end, we chose to demonstrate this scaling capability on a **well-established recipe: a dense, decoder-only, full-attention Transformer model, which is trained to perform autoregressive language modeling**.
  - However, our wider goal is to explore a diverse array of novel architectural choices and training schemes, and combine the most promising systems with the scaling capabilities of Pathways.

### PLM -> fine-tuningの問題点.
- the downside is that **they require a significant number of task-specific training examples** to finetune the model.

### GPT-3 variants
- The improvements in these models have primarily come from one or more of the following approaches:
  - (1) scaling the size of the models in both depth and width;
  - (2) increasing the number of tokens that the model was trained on;
  - (3) training on cleaner datasets from more diverse sources; and
  - (4) increasing model capacity without increasing the computational cost through sparsely activated modules.
- In this work, **we continue the scaling line of language modeling improvements** and train a 540 billion parameter, densely activated, autoregressive Transformer on 780 billion tokens of high-quality text.
- This was achieved through the use of **Pathways** (Barham et al., 2022),

## 先行研究と比べてどこがすごい?
### Efficient scaling
- We demonstrate the first large-scale use of Pathways (Barham et al., 2022) – a new ML system **which enables training a single model across thousands or tens of thousands of accelerator chips in a highly efficient manner**. With Pathways, we trained a 540B parameter language model on 6144 TPU v4 chips at efficiency levels that could not be reached before for models of this scale.
- **Most previous large language models were either trained on a single TPU system** (Du et al., 2021; Thoppilanet al., 2022) or **used pipeline parallelism** (Huang et al., 2019) to scale across GPU clusters (Smith et al.,1) or **multiple TPU v3 pods** (Rae et al., 2021a), with a maximum scale of 4096 TPU v3 chips.
- In Section 4, we describe how we were able to scale pipeline-free training of PaLM 540B to **6144 chips across two TPU v4 Pods** while achieving very high efficiency of 46.2% in model FLOPs utilization (observed throughput relative to theoretical max throughput) and 57.8% in hardware FLOPs utilization.

## 技術や手法の肝は?


## どうやって有効だと検証した?
- none

## 結果は?
- none

## 次に読むべき論文は?
- The most powerful of these post-GPT-3 models are
  - GLaM (Du et al., 2021),
  - Gopher (Rae et al., 2021a),
  - Chinchilla (Hoffmann et al., 2022),
  - Megatron–Turing NLG (Smith et al., 2022), and
  - LaMDA (Thoppilan et al., 2022),
- Pathways (Barham et al., 2022)
  - a new ML system which enables highly efficient training of very large neural networks across thousands of accelerator chips, including those spanning multiple Tensor Processing Units (TPU) v4 Pods.
- chain-of-thought prompting (Wei et al., 2022b),

## 不明な単語
- BIG-bench
- toxicity

## 感想
### 2022/6/19
- まあまあ集中して読めたと思う
- 1章まで読んだ
- 図表がきれい.
- 1:: "The key takeaways from this work are as follows"にはいろいろとすごいことが書いてあるので, あとで見直すのがいい.
