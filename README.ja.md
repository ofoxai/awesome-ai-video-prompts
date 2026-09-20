<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-CC0--1.0-lightgrey.svg" alt="License: CC0-1.0"></a>
  <a href="#table-of-contents"><img src="https://img.shields.io/badge/cases-276-blue.svg" alt="Case count: 276"></a>
  <a href="#table-of-contents"><img src="https://img.shields.io/badge/models-3-blue.svg" alt="Models: 3"></a>
  <a href="https://app.ofox.ai/playground?utm_source=github&utm_medium=badge&utm_campaign=awesome-ai-video-prompts"><img src="https://img.shields.io/badge/Try-on%20Ofox-orange.svg" alt="Try on Ofox"></a>
  <a href="https://app.ofox.ai?utm_source=github&utm_medium=badge&utm_campaign=awesome-ai-video-prompts"><img src="https://img.shields.io/badge/Get-API%20Key-brightgreen.svg" alt="Get API Key"></a>
</p>

<p align="center">
  <a href="README.md">English</a> ·
  <a href="README.zh-CN.md">简体中文</a> ·
  <a href="README.ja.md">日本語</a>
</p>

# Awesome AI Video Prompts

現行世代の AI 動画生成モデルのプロンプト・パラメータ・実出力のコレクションです。
**3 モデル・276 事例**、すべてにプロンプト全文（未編集）、実行時のパラメータ、
プレビューフレーム、再生できるクリップが付いています。収集と検証、そして「自社実行」と
明記した事例の実行は
[Ofox](https://ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts)
経由 —— 3 モデルとも同じ `POST /v1/videos` エンドポイントで呼び出せます。

```bash
curl -X POST https://api.ofox.ai/v1/videos \
  -H "Authorization: Bearer $OFOX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"bytedance/seedance-2.5","prompt":"A neon-lit Tokyo alley at night, cinematic dolly-in, rain reflections","duration":10,"resolution":"1080p","aspect_ratio":"16:9"}'
# -> {"id": "..."}; "status" が "completed" になるまで GET /v1/videos/{id} をポーリング
```

`model` を `minimax/hailuo-3` または `alibaba/wan-3.0` に変えるだけです —— 同じ
エンドポイント、同じリクエスト形式。パラメータとエラーコードの詳細は
[Ofox 動画 API ドキュメント](https://ofox.ai/docs/api/videos?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts)、
API キーの取得は
[app.ofox.ai](https://app.ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) から。

<a id="table-of-contents"></a>

## モデル

| | モデル | 事例数 | 一覧 |
|:---:|---|---:|---|
| <a href="models/seedance-2.5/README.ja.md"><img src="images/seedance-2.5/case1/preview.webp" width="160" alt="Seedance 2.5"></a> | **Seedance 2.5** — ByteDance<br><sub>4〜30秒 · 最大 1080p · 8 アスペクト比 · 音声同期</sub> | 85 | [事例](models/seedance-2.5/README.ja.md) · [事例ページ](https://ofox.ai/ja/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |
| <a href="models/hailuo-3/README.ja.md"><img src="images/hailuo-3/case1/preview.webp" width="160" alt="MiniMax Hailuo 3"></a> | **MiniMax Hailuo 3** — MiniMax<br><sub>テキスト / 画像 / 参照から動画 · ネイティブ音声</sub> | 120 | [事例](models/hailuo-3/README.ja.md) · [事例ページ](https://ofox.ai/ja/hailuo-3-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |
| <a href="models/wan-3/README.ja.md"><img src="images/wan-3/case1/preview.webp" width="160" alt="Tongyi Wanxiang Wan 3.0"></a> | **通義万相 Wan 3.0** — Alibaba<br><sub>2〜30秒 · 最大 1080p · 参照生成 / 開始終了フレーム / 編集 / 延長</sub> | 71 | [事例](models/wan-3/README.ja.md) · [事例ページ](https://ofox.ai/ja/wan-3-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |

## 事例に含まれるもの

どのモデルのどの事例にも、次の 6 つが揃っています。

- **プロンプト全文（未編集）**。要約でも整形版でもありません —— 原文にあった誤字や
  半角記号もそのまま残しています。
- **実行時のパラメータ**を 1 行で: モデル · プラットフォーム · モード · 長さ ·
  解像度 · アスペクト比 · 音声。出典が公開していない項目は推測せず `未标注` と記載。
- **プレビューフレーム**（WebP、長辺 700px）。クリックすると ofox.ai で再生できます。
- **入力素材** —— 参照画像、参照動画、キーフレーム、編集元クリップなど、使っていれば添付。
- **クレジット行** —— 原作者または一次ソースを明記し、リンクを張っています。
- **実費用** —— 自社で実行した事例のみ。課金対象の job id まで追跡できます。

## 貢献方法

PR 歓迎です。事例が属するモデルのフォルダ（`models/<モデル>/cases/<カテゴリ>.md`）を選び、
そのファイルの既存フォーマットに合わせてください。各事例には次が必要です: 完全かつ
未編集のプロンプト、実際の出力プレビュー（静止 WebP、長辺 700px、`≤2MB`、
`images/<モデル>/caseN/` 配下）、画像・参照から生成した事例では入力素材、自分で実行した
事例では費用欄に課金対象の job id。コミュニティ事例と公式事例は、必ず元の作者または
一次ソースをクレジット・リンクしてください。詳細は
[`CONTRIBUTING.md`](CONTRIBUTING.md)（英語）、テンプレートは
[`CASE_TEMPLATE.md`](CASE_TEMPLATE.md) を参照。PR に慣れていない方は
[事例投稿フォーム](../../issues/new?template=add_case.yml)もご利用ください。

⚠️ **`hailuo-3` と `wan-3` の事例ファイルは自動生成**されており、直接編集しても次回の
書き出しで上書きされます —— 内容に対して PR を出していただければ、メンテナが上流に
反映します。`seedance-2.5` のファイルは真のソースなので直接編集できます。

## 関連リンク

- [ofoxai/skills](https://github.com/ofoxai/skills) —— Ofox のエージェント向け skill
  リポジトリ。このリポジトリがプロンプトを見せる一方、あちらのシナリオ skill は AI
  エージェント（Claude Code、Codex、OpenCode）にプロンプト作成から同じ API の呼び出し、
  動画のダウンロード、費用の報告までを一気通貫で実行させます。
- **公式資料** —— 本リポジトリの公式事例の出典であり、パラメータを確認する際の一次情報です。
  Seedance 2.5: [ByteDance Seed 発表ブログ](https://seed.bytedance.com/en/blog/one-take-creation-flexible-referencing-introducing-seedance-2-5) ·
  [ModelArk チュートリアル](https://docs.byteplus.com/en/docs/ModelArk/2607688) ·
  [プロンプトガイド](https://docs.byteplus.com/en/docs/ModelArk/2607689)。
  Hailuo 3: [MiniMax-H3 モデルカード](https://huggingface.co/MiniMaxAI/MiniMax-H3)。
  Wan 3.0: [Wan 3.0 ショーケース](https://www.aliyun.com/benefit/scene/wan) ·
  [Alibaba Cloud プロンプトガイド](https://help.aliyun.com/zh/model-studio/text-to-video-prompt)。
- [jamez-bondos/awesome-gpt4o-images](https://github.com/jamez-bondos/awesome-gpt4o-images) ——
  画像生成における同種のコレクション。本リポジトリの事例レイアウトはこれを参考にしています。

## 謝辞

事例は 3 種類のソースから成り、それぞれ個別にクレジットしています。構成はモデルごとに
異なります。

- **Seedance 2.5**（85 件）—— 公式 24 件は Seed チームの発表と 火山方舟 / BytePlus
  ModelArk ドキュメントより。コミュニティ 46 件は X/Twitter・bilibili の原作者を個別に
  クレジットし、収録前に原投稿と照合済み。15 件は Ofox API での自社実行で `Ofox 实测`
  と表示、`费用` 行を持つ唯一の事例群です。
- **MiniMax Hailuo 3**（120 件）—— 公式 3 件は MiniMax 自身の HuggingFace モデルカードに
  ある再現用リクエストスクリプトから（プロンプト・パラメータ・出力が厳密に対応）。
  117 件は X の公開投稿から、プロンプト全文・クリップのミラー・クレジットとリンク付き。
- **Wan 3.0**（71 件）—— すべて Alibaba の一次資料です。8 件は Wan 3.0 ショーケース、
  63 件は公式『Wan3.0 動画クリエイター手引き』より。コミュニティ枠はありません ——
  見つかった第三者の Wan 素材は収録基準を満たしませんでした（キーワードを先取りした
  リポジトリ群、および作品単位のパーマリンクが取得できずクレジットを返せない公開ギャラリー）。

プレビューフレームは各事例のクレジット行の下にミラーしています。プロンプトはすべて
完全かつ未編集で転載しています。

事例番号はモデルごとに独立しており、**意図的に欠番があります**。`N` はここでの見出し番号
であると同時に、そのモデルの事例ページ上の `#case-N` アンカーでもあるため、欠番を詰める
ための再採番は、すでに公開されているリンクを黙って別の事例に向け替えてしまいます。
Seedance で 70 から 1001 に飛ぶのは、1000 番台を Ofox の自社実行用に予約しているためです。

ここに掲載されている作品の作者で削除をご希望の場合は、`Takedown: <モデル> case-N` という
タイトルで issue を立ててください。ご本人であることが分かれば、理由は不要です。
