# Including Signed Languages in Natural Language Processing
- Paper: https://aclanthology.org/2021.acl-long.570.pdf
- Code: none
- Organization: カーネギー・メロン大学(アメリカ)

## どんなもの?
- 手話は多くの聴覚障害者の主要なコミュニケーション手段であるものの, 口語が大多数の日常世界において読唇術やテキストベースのコミュニケーションが中心となっており, 手話によってコミュニケーションがとれる場面は少なく, 聴覚障害者のコミュニケーション手段が制限されてしまっている.
- 手話は自然言語の基本的な言語特性をすべて備えているため, そのモデル化には自然言語処理（NLP）のツールや理論が必要不可欠であるが, NLPを手話言語処理(SLP)に拡張しようとする研究はほとんどなされていない.
- 本研究ではまず, 手話をモデル化する際に考慮すべき手話の言語的特性, 現在のSLPモデルの限界を検討し、NLPを手話に拡張するための未解決の課題を明らかにした.

## 先行研究と比べてどこがすごい?
- 手話言語に対する言語モデリングの課題, NLPコミュニティが取り組むべき未解決問題のロードマップを提供しているところ.
  - NLPが関与することの重要性を主張するものはあったものの, 手話の言語的構成を探り, 活用しようとする試みは今までほとんどなかった

## 技術や手法の肝は?
- none

## どうやって有効だと検証した?
- none

## 結果は?
- none

## 議論はある?
- none

## 次に読むべき論文は?
- 手話表現認識のSummary
  - [Koller, 2020](https://arxiv.org/abs/2008.09918)
  - [Rastgoo et al, 2020]()
  - [Adaloglou et al, 2020](https://arxiv.org/abs/2007.12530)

## 不明な単語
- モダリティ
  - 話している内容や聞き手に対する話し手の態度（attitude）に関する言語表現
  - 例えば、「きっと雨が降るだろう」という文では、「雨が降る」ということに対する話し手の推測が「きっと～だろう」によって表されているので、この部分がモダリティ形式である
  - モダリティには「きっと～だろう」で表されるような事柄に対する対事モダリティと「おいしいね」「おもしろいよ」の「ね」や「よ」のような形式で表される聞き手に対する対人モダリティとがある
- フォノロジー(音韻論)
  - 言語がどんな音から成り立っているのかを調べる研究分野
  - 大きく言語学は、一般的に統語論、意味論、音韻論の３つに分けられる
  - 言葉の意味を成立させる最小単位は音素であり, 音素は文化的に決定されるものである
    - 日本人に、sing（発音記号síŋ）とthing（発音記号θíŋ）の違いを聞き分けることは難しい（物理学的には違う音だが、同じ音に聞こえる）
  - 参考:
    - https://liberal-arts-guide.com/phonology/