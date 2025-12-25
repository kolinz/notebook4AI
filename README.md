# notebook4AI

## IBM Granite 4.0を使ったファインチューニング
Unslothを使っています。Unslothが、2025年12月時点で配布しているノードブック [Granite4.0_350M.ipynb](https://github.com/unslothai/notebooks/blob/main/nb/Granite4.0_350M.ipynb) を使って、日本語データセットを用意しファインチューニングを試みたところ、エラーが出たため、配布しているノートブックをもとに改修したものが、[Granite4_0_ja_dataset_FT.ipynb](https://github.com/kolinz/notebook4AI/blob/main/Granite4_0_ja_dataset_FT.ipynb)になります。

- 手法：ファインチューニング
- 使用したモデル：unsloth/granite-4.0-350m-bnb-4bit
- モデルに対して、必要な日本語データセットのボリューム；だいたい100件以上が目安。50件ではトレーニングロスが、nan になりましたので、100件を超えたあたりで安定してファインチューニングのためのトレーニングできるようになりました。
- 日本語データセットは、GoogleドライブにCSV形式でアップロードしたファイルを読み込むようにしています。ファイル名は、finetune_support_ja_100_rich.csv です。ファイル名は変更する場合は、ノートブックの「日本語データセットの読み込みを実施」のセルのコードも変更してください。
- トレーニング後のモデルは、granite-4.0-350m-FT-ja.Q8_0.gguf というモデル名でダウンロードすることができます。
