[← All models](../../README.md) · [English](README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

# Seedance 2.5

92 ByteDance Seedance 2.5 cases with the complete prompt, the parameters, and a playable output — 24 official, 53 community, 15 run by us with the bill attached. Collected and run through [Ofox](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5).

## What is Seedance 2.5?

Seedance 2.5 is ByteDance's text-to-video and image-to-video model:
4–30 second clips, up to 1080p, 8 aspect ratios, with synced audio on by
default. It's available today through the
[Ofox video API](https://ofox.ai/models/bytedance/seedance-2.5?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) —
no Chinese business entity or phone number required to get a key, unlike
going straight to the upstream provider.

```bash
curl -X POST https://api.ofox.ai/v1/videos \
  -H "Authorization: Bearer $OFOX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"bytedance/seedance-2.5","prompt":"A neon-lit Tokyo alley at night, cinematic dolly-in, rain reflections","duration":10,"resolution":"1080p","aspect_ratio":"16:9"}'
# -> {"id": "..."}; poll GET /v1/videos/{id} until "status" is "completed"
```

Full parameter reference and error codes:
[Ofox video API docs](https://ofox.ai/docs/api/videos?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5).
Get a key: [app.ofox.ai](https://app.ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5).

## Pricing

Seedance 2.5 per-second rate on Ofox, as of 2026-08 (source:
[ofox.ai/models/bytedance/seedance-2.5](https://ofox.ai/models/bytedance/seedance-2.5?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5) —
re-verify against the live page before quoting a number you intend to hold
someone to, particularly the "time-limited" 1080p rate):

| Resolution | Text-to-video (t2v) | Video-to-video (v2v) |
|---|---|---|
| 480p | $0.11/s | $0.14/s |
| 720p | $0.24/s | $0.30/s |
| 1080p | $0.48/s (list $0.60/s, time-limited) | $0.568/s (list $0.71/s) |

- Duration: 4–30 seconds, any integer.
- Aspect ratios: 21:9 / 16:9 / 4:3 / 1:1 / 3:4 / 9:16 / adaptive.
- Audio is on by default and already covered by the per-second rate above
  — it's not billed separately.

Use this table to estimate a run **before** you start it. The `费用` (cost)
line on a self-run case (in the category files linked below) is not an
estimate off this table — it is the
amount actually billed for that job, and it carries the job id that was
billed, so every number traces back to one API call. See
[`CASE_TEMPLATE.md`](../../CASE_TEMPLATE.md).

<a id="table-of-contents"></a>

## Table of Contents

| | Category | Cases |
|:---:|---|---:|
| <a href="cases/short-drama.md"><img src="../../images/seedance-2.5/case1/preview.webp" width="160" alt="Short Drama (短剧)"></a> | [Short Drama (短剧)](cases/short-drama.md) | 15 |
| <a href="cases/anime-drama.md"><img src="../../images/seedance-2.5/case9/preview.webp" width="160" alt="Anime Drama (漫剧)"></a> | [Anime Drama (漫剧)](cases/anime-drama.md) | 11 |
| <a href="cases/ad-creative.md"><img src="../../images/seedance-2.5/case12/preview.webp" width="160" alt="Ad Creative (创意广告)"></a> | [Ad Creative (创意广告)](cases/ad-creative.md) | 7 |
| <a href="cases/product-video.md"><img src="../../images/seedance-2.5/case18/preview.webp" width="160" alt="Product Video (电商产品视频)"></a> | [Product Video (电商产品视频)](cases/product-video.md) | 7 |
| <a href="cases/talking-head.md"><img src="../../images/seedance-2.5/case21/preview.webp" width="160" alt="Talking Head (口播和数字人)"></a> | [Talking Head (口播和数字人)](cases/talking-head.md) | 3 |
| <a href="cases/ugc-ads.md"><img src="../../images/seedance-2.5/case24/preview.webp" width="160" alt="UGC Ads (UGC风格广告)"></a> | [UGC Ads (UGC风格广告)](cases/ugc-ads.md) | 6 |
| <a href="cases/shorts-reels.md"><img src="../../images/seedance-2.5/case28/preview.webp" width="160" alt="Shorts & Reels (社媒短视频)"></a> | [Shorts & Reels (社媒短视频)](cases/shorts-reels.md) | 14 |
| <a href="cases/product-demo.md"><img src="../../images/seedance-2.5/case37/preview.webp" width="160" alt="Product Demo (产品演示)"></a> | [Product Demo (产品演示)](cases/product-demo.md) | 5 |
| <a href="cases/keyframe-animation.md"><img src="../../images/seedance-2.5/case42/preview.webp" width="160" alt="Keyframe Animation (首尾帧动画)"></a> | [Keyframe Animation (首尾帧动画)](cases/keyframe-animation.md) | 3 |
| <a href="cases/video-extend-edit.md"><img src="../../images/seedance-2.5/case45/preview.webp" width="160" alt="Video Extend & Edit (视频延长和编辑)"></a> | [Video Extend & Edit (视频延长和编辑)](cases/video-extend-edit.md) | 11 |
| <a href="cases/image-edit.md"><img src="../../images/seedance-2.5/case55/preview.webp" width="160" alt="Image Edit (图生图和修图)"></a> | [Image Edit (图生图和修图)](cases/image-edit.md) | 2 |
|  | [Product Image (电商主图和海报)](cases/product-image.md) | 0 |
| <a href="cases/music-video.md"><img src="../../images/seedance-2.5/case57/preview.webp" width="160" alt="Music Video (音乐可视化和MV)"></a> | [Music Video (音乐可视化和MV)](cases/music-video.md) | 5 |
| <a href="cases/explainer.md"><img src="../../images/seedance-2.5/case62/preview.webp" width="160" alt="Explainer (教学解说视频)"></a> | [Explainer (教学解说视频)](cases/explainer.md) | 3 |
