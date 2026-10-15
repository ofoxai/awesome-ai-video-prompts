[← 返回模型总览](../../README.zh-CN.md) · [English](README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

# Seedance 2.5

92 条字节跳动 Seedance 2.5 案例，每条都有完整提示词、参数和可播放的成片 —— 官方 24 条、社区 53 条、我们自跑 15 条（附账单）。通过 [Ofox](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) 调用和整理。

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

这张表用于**跑之前**估算。下面各分类文件里自跑案例的 `费用` 一行不是按表算出来的估价，而是那次任务的实际账单金额，并在同一行标出被计费的 job id，每个数字都能追回到具体那一次 API 调用 —— 参见 [`CASE_TEMPLATE.md`](../../CASE_TEMPLATE.md)。

<a id="table-of-contents"></a>
<a id="table-of-contents"></a>

## 目录

| | 分类 | 案例数 |
|:---:|---|---:|
| <a href="cases/short-drama.zh-CN.md"><img src="../../images/seedance-2.5/case1/preview.webp" width="160" alt="短剧 Short Drama"></a> | [短剧 Short Drama](cases/short-drama.zh-CN.md) | 15 |
| <a href="cases/anime-drama.zh-CN.md"><img src="../../images/seedance-2.5/case9/preview.webp" width="160" alt="漫剧 Anime Drama"></a> | [漫剧 Anime Drama](cases/anime-drama.zh-CN.md) | 11 |
| <a href="cases/ad-creative.zh-CN.md"><img src="../../images/seedance-2.5/case12/preview.webp" width="160" alt="创意广告 Ad Creative"></a> | [创意广告 Ad Creative](cases/ad-creative.zh-CN.md) | 7 |
| <a href="cases/product-video.zh-CN.md"><img src="../../images/seedance-2.5/case18/preview.webp" width="160" alt="电商产品视频 Product Video"></a> | [电商产品视频 Product Video](cases/product-video.zh-CN.md) | 7 |
| <a href="cases/talking-head.zh-CN.md"><img src="../../images/seedance-2.5/case21/preview.webp" width="160" alt="口播和数字人 Talking Head"></a> | [口播和数字人 Talking Head](cases/talking-head.zh-CN.md) | 3 |
| <a href="cases/ugc-ads.zh-CN.md"><img src="../../images/seedance-2.5/case24/preview.webp" width="160" alt="UGC风格广告 UGC Ads"></a> | [UGC风格广告 UGC Ads](cases/ugc-ads.zh-CN.md) | 6 |
| <a href="cases/shorts-reels.zh-CN.md"><img src="../../images/seedance-2.5/case28/preview.webp" width="160" alt="社媒短视频 Shorts & Reels"></a> | [社媒短视频 Shorts & Reels](cases/shorts-reels.zh-CN.md) | 14 |
| <a href="cases/product-demo.zh-CN.md"><img src="../../images/seedance-2.5/case37/preview.webp" width="160" alt="产品演示 Product Demo"></a> | [产品演示 Product Demo](cases/product-demo.zh-CN.md) | 5 |
| <a href="cases/keyframe-animation.zh-CN.md"><img src="../../images/seedance-2.5/case42/preview.webp" width="160" alt="首尾帧动画 Keyframe Animation"></a> | [首尾帧动画 Keyframe Animation](cases/keyframe-animation.zh-CN.md) | 3 |
| <a href="cases/video-extend-edit.zh-CN.md"><img src="../../images/seedance-2.5/case45/preview.webp" width="160" alt="视频延长和编辑 Video Extend & Edit"></a> | [视频延长和编辑 Video Extend & Edit](cases/video-extend-edit.zh-CN.md) | 11 |
| <a href="cases/image-edit.zh-CN.md"><img src="../../images/seedance-2.5/case55/preview.webp" width="160" alt="图生图和修图 Image Edit"></a> | [图生图和修图 Image Edit](cases/image-edit.zh-CN.md) | 2 |
|  | [电商主图和海报 Product Image](cases/product-image.zh-CN.md) | 0 |
| <a href="cases/music-video.zh-CN.md"><img src="../../images/seedance-2.5/case57/preview.webp" width="160" alt="音乐可视化和MV Music Video"></a> | [音乐可视化和MV Music Video](cases/music-video.zh-CN.md) | 5 |
| <a href="cases/explainer.zh-CN.md"><img src="../../images/seedance-2.5/case62/preview.webp" width="160" alt="教学解说视频 Explainer"></a> | [教学解说视频 Explainer](cases/explainer.zh-CN.md) | 3 |
