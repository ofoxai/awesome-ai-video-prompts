<p align="center">
  <a href="https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=banner&utm_campaign=awesome-seedance-2-5">
    <img src="images/banner.png" alt="Seedance 2.5 提示词与案例合集 · Ofox" width="100%">
  </a>
</p>

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-CC0--1.0-lightgrey.svg" alt="License: CC0-1.0"></a>
  <a href="#table-of-contents"><img src="https://img.shields.io/badge/cases-84-blue.svg" alt="案例数：84"></a>
  <a href="https://app.ofox.ai/playground?utm_source=github&utm_medium=badge&utm_campaign=awesome-seedance-2-5"><img src="https://img.shields.io/badge/Try-Seedance%202.5%20on%20Ofox-orange.svg" alt="在 Ofox 试用 Seedance 2.5"></a>
  <a href="https://app.ofox.ai?utm_source=github&utm_medium=badge&utm_campaign=awesome-seedance-2-5"><img src="https://img.shields.io/badge/Get-API%20Key-brightgreen.svg" alt="获取 API Key"></a>
</p>

<p align="center">
  <a href="README.md">English</a> ·
  <a href="README.zh-CN.md">简体中文</a> ·
  <a href="README.ja.md">日本語</a>
</p>

# Awesome Seedance 2.5

字节跳动 Seedance 2.5 视频模型的提示词与实测案例合集 —— 每个案例都有完整提示词、真实输出预览，自跑案例还附账单截图。案例通过 [Ofox](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) 调用和整理。

## Seedance 2.5 是什么

Seedance 2.5 是字节跳动的文生视频 / 图生视频模型：支持 4–30 秒、最高 1080p、8 种宽高比，默认自带同步音频。现在可以通过 [Ofox 的视频 API](https://ofox.ai/models/bytedance/seedance-2.5?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) 直接调用 —— 不需要中国主体或国内手机号即可注册取 key，这点和直连上游供应商不同。

```bash
curl -X POST https://api.ofox.ai/v1/videos \
  -H "Authorization: Bearer $OFOX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"bytedance/seedance-2.5","prompt":"A neon-lit Tokyo alley at night, cinematic dolly-in, rain reflections","duration":10,"resolution":"1080p","aspect_ratio":"16:9"}'
# -> {"id": "..."}；轮询 GET /v1/videos/{id} 直到 "status" 变为 "completed"
```

完整参数说明和错误码：[Ofox 视频 API 文档](https://ofox.ai/docs/api/videos?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5)。取 key：[app.ofox.ai](https://app.ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5)。

## 价格

Ofox 上 Seedance 2.5 的每秒价格，截至 2026-08 月（来源：[ofox.ai/models/bytedance/seedance-2.5](https://ofox.ai/models/bytedance/seedance-2.5?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) —— 如果这个数字对你很重要，尤其是"限时"的 1080p 价格，请以模型页实时数据为准）：

| 分辨率 | 文生视频 (t2v) | 视频生视频 (v2v) |
|---|---|---|
| 480p | $0.11/s | $0.14/s |
| 720p | $0.24/s | $0.30/s |
| 1080p | $0.48/s (原价 $0.60/s，限时价) | $0.568/s (原价 $0.71/s) |

- 时长：4–30 秒，任意整数。
- 宽高比：21:9 / 16:9 / 4:3 / 1:1 / 3:4 / 9:16 / adaptive。
- 音频默认开启，已包含在上面的每秒价格中，不单独计费。

这张表用于**跑之前**估算。下面各分类文件里自跑案例的 `费用` 一行不是按表算出来的估价，而是那次任务的实际账单金额，并在同一行标出被计费的 job id，每个数字都能追回到具体那一次 API 调用 —— 参见 [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md)。

<a id="table-of-contents"></a>
## 目录

| | 分类 | 案例数 |
|:---:|---|---:|
| <a href="cases/short-drama.zh-CN.md"><img src="images/case1/preview.webp" width="160" alt="短剧 Short Drama"></a> | [短剧 Short Drama](cases/short-drama.zh-CN.md) | 13 |
| <a href="cases/anime-drama.zh-CN.md"><img src="images/case9/preview.webp" width="160" alt="漫剧 Anime Drama"></a> | [漫剧 Anime Drama](cases/anime-drama.zh-CN.md) | 11 |
| <a href="cases/ad-creative.zh-CN.md"><img src="images/case12/preview.webp" width="160" alt="创意广告 Ad Creative"></a> | [创意广告 Ad Creative](cases/ad-creative.zh-CN.md) | 7 |
| <a href="cases/product-video.zh-CN.md"><img src="images/case18/preview.webp" width="160" alt="电商产品视频 Product Video"></a> | [电商产品视频 Product Video](cases/product-video.zh-CN.md) | 7 |
| <a href="cases/talking-head.zh-CN.md"><img src="images/case21/preview.webp" width="160" alt="口播和数字人 Talking Head"></a> | [口播和数字人 Talking Head](cases/talking-head.zh-CN.md) | 3 |
| <a href="cases/ugc-ads.zh-CN.md"><img src="images/case24/preview.webp" width="160" alt="UGC风格广告 UGC Ads"></a> | [UGC风格广告 UGC Ads](cases/ugc-ads.zh-CN.md) | 5 |
| <a href="cases/shorts-reels.zh-CN.md"><img src="images/case28/preview.webp" width="160" alt="社媒短视频 Shorts & Reels"></a> | [社媒短视频 Shorts & Reels](cases/shorts-reels.zh-CN.md) | 11 |
| <a href="cases/product-demo.zh-CN.md"><img src="images/case37/preview.webp" width="160" alt="产品演示 Product Demo"></a> | [产品演示 Product Demo](cases/product-demo.zh-CN.md) | 5 |
| <a href="cases/keyframe-animation.zh-CN.md"><img src="images/case42/preview.webp" width="160" alt="首尾帧动画 Keyframe Animation"></a> | [首尾帧动画 Keyframe Animation](cases/keyframe-animation.zh-CN.md) | 3 |
| <a href="cases/video-extend-edit.zh-CN.md"><img src="images/case45/preview.webp" width="160" alt="视频延长和编辑 Video Extend & Edit"></a> | [视频延长和编辑 Video Extend & Edit](cases/video-extend-edit.zh-CN.md) | 10 |
| <a href="cases/image-edit.zh-CN.md"><img src="images/case55/preview.webp" width="160" alt="图生图和修图 Image Edit"></a> | [图生图和修图 Image Edit](cases/image-edit.zh-CN.md) | 2 |
|  | [电商主图和海报 Product Image](cases/product-image.zh-CN.md) | 0 |
| <a href="cases/music-video.zh-CN.md"><img src="images/case57/preview.webp" width="160" alt="音乐可视化和MV Music Video"></a> | [音乐可视化和MV Music Video](cases/music-video.zh-CN.md) | 5 |
| <a href="cases/explainer.zh-CN.md"><img src="images/case62/preview.webp" width="160" alt="教学解说视频 Explainer"></a> | [教学解说视频 Explainer](cases/explainer.zh-CN.md) | 2 |

## 如何贡献

欢迎提 PR。每个案例需要：完整未删改的提示词；真实输出预览（700px 宽的静态 WebP 帧，`≤2MB`，放在 `images/caseN/` 下），图生视频类案例还需附输入原图；自跑案例还需在费用一栏标出被计费的 job id，让金额能追回到那一次 API 调用。社区和官方案例必须注明并链接原作者或第一方来源。完整格式、规则和案例来源比例见 [`CONTRIBUTING.md`](CONTRIBUTING.md)（英文），案例模板见 [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md)。
不习惯提 PR 也可以直接用[案例提交表单](../../issues/new?template=add_case.yml)。

## 相关链接

- [ofoxai/skills](https://github.com/ofoxai/skills) —— Ofox 的 agent skill 仓库。这个仓库给你看提示词，那个仓库里的场景 skill 让 AI agent（Claude Code、Codex、OpenCode）把整条流程跑完：写提示词、调用同一个 API、下载视频、报账单。*（该仓库发布后此链接才生效 —— 撰写本文时尚未公开。）*

- **Seedance 2.5 官方素材** —— 本仓库官方案例的出处，核对参数时请以它们为准：
  [字节 Seed 发布博客](https://seed.bytedance.com/zh/blog/one-take-creation-flexible-referencing-introducing-seedance-2-5) ·
  [火山方舟教程](https://docs.volcengine.com/docs/82379/2607688?lang=zh) ·
  [火山方舟提示词指南](https://docs.volcengine.com/docs/82379/2607689?lang=zh)
  （英文镜像：[ModelArk 2607688](https://docs.byteplus.com/en/docs/ModelArk/2607688) ·
  [2607689](https://docs.byteplus.com/en/docs/ModelArk/2607689)）
- [jamez-bondos/awesome-gpt4o-images](https://github.com/jamez-bondos/awesome-gpt4o-images) ——
  图像生成领域的同类合集，本仓库的案例版式借鉴自它。

## 致谢

本合集混合三类来源，每个案例下方分别署名：24 个案例是字节跳动官方素材 —— 由 Seed
团队发布、以及火山方舟 / BytePlus ModelArk 文档中公开的提示词与演示片段。46 个案例是
社区作品，逐条署名到 X/Twitter 或 B 站原作者，来自公开提示词库（YouMind、EvoLink）以及
B 站创作者本人的投稿，收录前均独立核对过原作者的原帖。剩下 14 个（Case 1001-1014）是我们
自己通过 Ofox API 跑出来的，标为 `Ofox 实测` —— 也是全仓唯一带 `费用` 一行的案例，每条都
能追回到出账的那个 job id。预览帧在此镜像保存，每个案例下方均附署名；提示词完整未删改地
转载。

编号从 70 直接跳到 1001 是刻意的。`N` 既是这里的标题编号，也是
`ofox.ai/seedance-2-5-prompts` 上的 `#case-N` 锚点，而 1000+ 是留给 Ofox 自跑案例的保留
段 —— 为了填平这个断档而重排编号，会把已经发出去的外链静默指到别的案例上。

如果你是此处收录内容的作者并希望撤下，请开一个标题为 `Takedown: case-N` 的 issue。除表明
身份外无需其他理由。
