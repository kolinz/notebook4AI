# notebook4AI

## Qwen3 0.6B を使ったファインチューニング
Unslothを使っています。Unslothが、2025年12月時点で配布しているノードブック [Qwen3_(4B)-Instruct.ipynb](https://github.com/unslothai/notebooks/blob/main/nb/Qwen3_(4B)-Instruct.ipynb) をもとに、日本語データセットを用意し、Qwen3 0.6Bでファインチューニングを行うためにカスタマイズしたノートブックが[Qwen3(0_6B)_ja_dataset_FT.ipynb](https://github.com/kolinz/notebook4AI/blob/main/Qwen3(0_6B)_ja_dataset_FT.ipynb)になります。

- 手法：ファインチューニング
- 使用したモデル：unsloth/Qwen3-0.6B
- モデルに対して、必要な日本語データセットのボリューム；だいたい100件以上が目安。120件で確認しています。
- 日本語データセットは、GoogleドライブにCSV形式でアップロードしたファイルを読み込むようにしています。ファイル名は、faq-dataset.csv です。ファイル名は変更する場合は、ノートブックの「日本語データセットの読み込みを実施」のセルのコードも変更してください。

日本語データセットは、次のような構造のCSVファイルを作成してください。文字コードはUTF-8(BOM付き)です。文字コードがUTF-8(BOM付き)であることで、CSVファイルをMicrosoft Excelで開いた際に文字化けすることはありません。
列は、`conversations`のみです。

| conversations |
| :---- |
| "[[{""role"":""user"",""content"":""キルチェーン（Cyber Kill Chain）とは何ですか？""},{""role"":""assistant"",""content"":""キルチェーンとは、攻撃の一連の段階（偵察・侵入・実行など）を整理したモデルです。各段階で対策を講じることで攻撃を阻止できます。""}]]" |
| "[[{""role"":""user"",""content"":""メールセキュリティでSPFとは何ですか？""},{""role"":""assistant"",""content"":""SPFは送信元メールサーバの正当性を検証する仕組みで、なりすましメール対策に利用されます。""}]]" |

サンプルとして、[faq-dataset.csv](https://github.com/kolinz/notebook4AI/blob/main/dataset-sample/faq-dataset.csv)を用意しましたので、ご自由にお使いください。

## IBM Granite 4.0を使ったファインチューニング
Unslothを使っています。Unslothが、2025年12月時点で配布しているノードブック [Granite4.0_350M.ipynb](https://github.com/unslothai/notebooks/blob/main/nb/Granite4.0_350M.ipynb) を使って、日本語データセットを用意しファインチューニングを試みたところ、エラーが出たため、配布しているノートブックをもとに改修したものが、[Granite4_0_ja_dataset_FT.ipynb](https://github.com/kolinz/notebook4AI/blob/main/Granite4_0_ja_dataset_FT.ipynb)になります。

- 手法：ファインチューニング
- 使用したモデル：unsloth/granite-4.0-350m-bnb-4bit
- モデルに対して、必要な日本語データセットのボリューム；だいたい100件以上が目安。50件ではトレーニングロスが、nan になりましたので、100件を超えたあたりで安定してファインチューニングのためのトレーニングできるようになりました。
- 日本語データセットは、GoogleドライブにCSV形式でアップロードしたファイルを読み込むようにしています。ファイル名は、finetune_support_ja_100_rich.csv です。ファイル名は変更する場合は、ノートブックの「日本語データセットの読み込みを実施」のセルのコードも変更してください。
- トレーニング後のモデルは、granite-4.0-350m-FT-ja.Q8_0.gguf というモデル名でダウンロードすることができます。
