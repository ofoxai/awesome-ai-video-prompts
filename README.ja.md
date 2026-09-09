<p align="center">
  <a href="https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=banner&utm_campaign=awesome-seedance-2-5">
    <img src="images/banner.png" alt="Seedance 2.5 プロンプト＆事例集 · Ofox" width="100%">
  </a>
</p>

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-CC0--1.0-lightgrey.svg" alt="License: CC0-1.0"></a>
  <a href="#table-of-contents"><img src="https://img.shields.io/badge/cases-84-blue.svg" alt="事例数: 84"></a>
  <a href="https://app.ofox.ai/playground?utm_source=github&utm_medium=badge&utm_campaign=awesome-seedance-2-5"><img src="https://img.shields.io/badge/Try-Seedance%202.5%20on%20Ofox-orange.svg" alt="Ofox で Seedance 2.5 を試す"></a>
  <a href="https://app.ofox.ai?utm_source=github&utm_medium=badge&utm_campaign=awesome-seedance-2-5"><img src="https://img.shields.io/badge/Get-API%20Key-brightgreen.svg" alt="APIキーを取得"></a>
</p>

<p align="center">
  <a href="README.md">English</a> ·
  <a href="README.zh-CN.md">简体中文</a> ·
  <a href="README.ja.md">日本語</a>
</p>

# Awesome Seedance 2.5

ByteDance の動画生成モデル Seedance 2.5 のプロンプト・実行事例集 —— すべての事例に完全なプロンプトと実際の出力プレビューを掲載し、自分で実行した事例には請求額のスクリーンショットも添付。事例は [Ofox](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) 経由で実行・整理しています。

## Seedance 2.5 とは

Seedance 2.5 は ByteDance のテキスト生成動画・画像生成動画モデルです。4〜30秒のクリップを最大 1080p、8種類のアスペクト比で生成でき、音声は既定でオンになっています。今は [Ofox の動画API](https://ofox.ai/models/bytedance/seedance-2.5?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) から直接呼び出せます —— 上流プロバイダーに直接申し込む場合と違い、中国法人や中国の電話番号は不要です。

```bash
curl -X POST https://api.ofox.ai/v1/videos \
  -H "Authorization: Bearer $OFOX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"bytedance/seedance-2.5","prompt":"A neon-lit Tokyo alley at night, cinematic dolly-in, rain reflections","duration":10,"resolution":"1080p","aspect_ratio":"16:9"}'
# -> {"id": "..."}; "status" が "completed" になるまで GET /v1/videos/{id} をポーリング
```

パラメータ・エラーコードの詳細: [Ofox 動画API ドキュメント](https://ofox.ai/docs/api/videos?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5)。APIキーの取得: [app.ofox.ai](https://app.ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5)。

## 料金

Ofox における Seedance 2.5 の秒単価、2026年8月時点（出典: [ofox.ai/models/bytedance/seedance-2.5](https://ofox.ai/models/bytedance/seedance-2.5?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) —— 特に「期間限定」の 1080p 料金は変わる可能性があるため、正確な数字が必要な場合は必ず最新のページを確認してください):

| 解像度 | テキスト生成動画 (t2v) | 動画生成動画 (v2v) |
|---|---|---|
| 480p | $0.11/s | $0.14/s |
| 720p | $0.24/s | $0.30/s |
| 1080p | $0.48/s (通常 $0.60/s、期間限定価格) | $0.568/s (通常 $0.71/s) |

- 長さ: 4〜30秒の任意の整数。
- アスペクト比: 21:9 / 16:9 / 4:3 / 1:1 / 3:4 / 9:16 / adaptive。
- 音声は既定でオンで、上記の秒単価に含まれており別途課金されません。

この表は実行**前**の見積もりに使います。以下の各カテゴリファイルにある自分で実行した事例の「費用」欄は、この表からの見積もりではなく、そのジョブで実際に請求された金額であり、同じ行に課金対象の job id を併記しているため、どの金額も個々の API 呼び出しまで追跡できます —— [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md) を参照してください。

<a id="table-of-contents"></a>
## 目次

| | カテゴリ | 事例数 |
|:---:|---|---:|
| <a href="cases/short-drama.ja.md"><img src="images/case1/preview.webp" width="160" alt="ショートドラマ Short Drama"></a> | [ショートドラマ Short Drama](cases/short-drama.ja.md) | 13 |
| <a href="cases/anime-drama.ja.md"><img src="images/case9/preview.webp" width="160" alt="アニメドラマ Anime Drama"></a> | [アニメドラマ Anime Drama](cases/anime-drama.ja.md) | 11 |
| <a href="cases/ad-creative.ja.md"><img src="images/case12/preview.webp" width="160" alt="クリエイティブ広告 Ad Creative"></a> | [クリエイティブ広告 Ad Creative](cases/ad-creative.ja.md) | 7 |
| <a href="cases/product-video.ja.md"><img src="images/case18/preview.webp" width="160" alt="ECサイト商品動画 Product Video"></a> | [ECサイト商品動画 Product Video](cases/product-video.ja.md) | 7 |
| <a href="cases/talking-head.ja.md"><img src="images/case21/preview.webp" width="160" alt="トーキングヘッド・デジタルヒューマン Talking Head"></a> | [トーキングヘッド・デジタルヒューマン Talking Head](cases/talking-head.ja.md) | 3 |
| <a href="cases/ugc-ads.ja.md"><img src="images/case24/preview.webp" width="160" alt="UGC風広告 UGC Ads"></a> | [UGC風広告 UGC Ads](cases/ugc-ads.ja.md) | 5 |
| <a href="cases/shorts-reels.ja.md"><img src="images/case28/preview.webp" width="160" alt="ショート動画・リール Shorts & Reels"></a> | [ショート動画・リール Shorts & Reels](cases/shorts-reels.ja.md) | 11 |
| <a href="cases/product-demo.ja.md"><img src="images/case37/preview.webp" width="160" alt="製品デモ Product Demo"></a> | [製品デモ Product Demo](cases/product-demo.ja.md) | 5 |
| <a href="cases/keyframe-animation.ja.md"><img src="images/case42/preview.webp" width="160" alt="開始・終了フレームアニメーション Keyframe Animation"></a> | [開始・終了フレームアニメーション Keyframe Animation](cases/keyframe-animation.ja.md) | 3 |
| <a href="cases/video-extend-edit.ja.md"><img src="images/case45/preview.webp" width="160" alt="動画延長・編集 Video Extend & Edit"></a> | [動画延長・編集 Video Extend & Edit](cases/video-extend-edit.ja.md) | 10 |
| <a href="cases/image-edit.ja.md"><img src="images/case55/preview.webp" width="160" alt="画像編集・リタッチ Image Edit"></a> | [画像編集・リタッチ Image Edit](cases/image-edit.ja.md) | 2 |
|  | [商品メイン画像・ポスター Product Image](cases/product-image.ja.md) | 0 |
| <a href="cases/music-video.ja.md"><img src="images/case57/preview.webp" width="160" alt="ミュージックビデオ Music Video"></a> | [ミュージックビデオ Music Video](cases/music-video.ja.md) | 5 |
| <a href="cases/explainer.ja.md"><img src="images/case62/preview.webp" width="160" alt="解説動画 Explainer"></a> | [解説動画 Explainer](cases/explainer.ja.md) | 2 |

## 貢献方法

PR 歓迎です。事例には以下が必要です: 完全かつ未編集のプロンプト、実際の出力プレビュー（700px 幅の静止 WebP フレーム、`≤2MB`、`images/caseN/` 配下に配置）、画像から動画を生成した事例では入力画像も必要です。自分で実行した事例には、費用欄に課金対象の job id を併記してください（金額をその API 呼び出しまで追跡できるようにするためです）。コミュニティ事例および公式事例は、必ず元の作者または一次ソースをクレジット・リンクしてください。詳しいフォーマット・ルール・事例ソース比率は [`CONTRIBUTING.md`](CONTRIBUTING.md)（英語）を、テンプレートは [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md) を参照してください。
PR に慣れていない方は[事例投稿フォーム](../../issues/new?template=add_case.yml)もご利用ください。

## 関連リンク

- [ofoxai/skills](https://github.com/ofoxai/skills) —— Ofox のエージェント向け skill リポジトリ。このリポジトリがプロンプトを見せる一方、あちらのシナリオ skill は AI エージェント（Claude Code、Codex、OpenCode）にプロンプト作成から同じAPIの呼び出し、動画のダウンロード、費用の報告までを一気通貫で実行させます。*（そのリポジトリが公開され次第このリンクは有効になります —— 本稿執筆時点では未公開です。）*

- **Seedance 2.5 の公式資料** —— 本リポジトリの公式事例の出典です。パラメータを
  確認する際は一次情報をご参照ください:
  [ByteDance Seed 発表ブログ](https://seed.bytedance.com/en/blog/one-take-creation-flexible-referencing-introducing-seedance-2-5) ·
  [ModelArk チュートリアル](https://docs.byteplus.com/en/docs/ModelArk/2607688) ·
  [ModelArk プロンプトガイド](https://docs.byteplus.com/en/docs/ModelArk/2607689)
  （中国語原典: [火山方舟 2607688](https://docs.volcengine.com/docs/82379/2607688?lang=zh) ·
  [2607689](https://docs.volcengine.com/docs/82379/2607689?lang=zh)）
- [jamez-bondos/awesome-gpt4o-images](https://github.com/jamez-bondos/awesome-gpt4o-images) ——
  画像生成における同種のコレクション。本リポジトリの事例レイアウトはこれを参考にしています。

## 謝辞

本コレクションは3種類の出典を組み合わせており、各事例ごとに区別してクレジットしています。
24事例は ByteDance の公式資料です —— Seed チームが公開したもの、および火山方舟 /
BytePlus ModelArk のドキュメントに掲載されたプロンプトと実演映像です。46事例はコミュニティ
の作品で、公開プロンプトライブラリ（YouMind、EvoLink）および bilibili のクリエイター本人の
投稿を出典とし、収録前に各作者の元投稿と突き合わせて独立検証したうえで、X/Twitter または
bilibili の作者に個別クレジットしています。残る14事例（Case 1001-1014）は Ofox API で
自分たちが実行したもので、`Ofox 实测` と表記しています —— 本リポジトリで `费用` 欄を持つ
のはこれらだけで、いずれも課金元の job id まで追跡できます。プレビューフレームは各事例の
クレジット表記のもとで本リポジトリにミラーしており、プロンプトは完全かつ未編集のまま
転載しています。

番号が 70 から 1001 へ飛ぶのは意図的です。`N` はここでの見出し番号であると同時に
`ofox.ai/seedance-2-5-prompts` 上の `#case-N` アンカーでもあり、1000 番台は Ofox 自身の
実行分に予約された領域です —— 間を詰めるために番号を振り直すと、すでに公開済みのリンクが
静かに別の事例を指してしまいます。

ここに掲載された内容の作者ご本人で削除をご希望の場合は、`Takedown: case-N` という
タイトルで issue を開いてください。ご本人であることの表明以外に理由は不要です。
