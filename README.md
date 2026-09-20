<p align="center">
  <a href="https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=banner&utm_campaign=awesome-seedance-2-5">
    <img src="images/banner.png" alt="Seedance 2.5 — Awesome Prompts &amp; Cases, on Ofox" width="100%">
  </a>
</p>

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-CC0--1.0-lightgrey.svg" alt="License: CC0-1.0"></a>
  <a href="#table-of-contents"><img src="https://img.shields.io/badge/cases-84-blue.svg" alt="Case count: 84"></a>
  <a href="https://app.ofox.ai/playground?utm_source=github&utm_medium=badge&utm_campaign=awesome-seedance-2-5"><img src="https://img.shields.io/badge/Try-Seedance%202.5%20on%20Ofox-orange.svg" alt="Try Seedance 2.5 on Ofox"></a>
  <a href="https://app.ofox.ai?utm_source=github&utm_medium=badge&utm_campaign=awesome-seedance-2-5"><img src="https://img.shields.io/badge/Get-API%20Key-brightgreen.svg" alt="Get API Key"></a>
</p>

<p align="center">
  <a href="README.md">English</a> ·
  <a href="README.zh-CN.md">简体中文</a> ·
  <a href="README.ja.md">日本語</a>
</p>

# Awesome Seedance 2.5

A curated collection of prompts, parameters, and real output for
ByteDance's Seedance 2.5 video model — every case with a complete prompt,
a preview, and (for self-run cases) the exact bill. Curated and run
through [Ofox](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5).

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
[`CASE_TEMPLATE.md`](CASE_TEMPLATE.md).

## Table of Contents

| | Category | Cases |
|:---:|---|---:|
| <a href="models/seedance-2.5/cases/short-drama.md"><img src="images/seedance-2.5/case1/preview.webp" width="160" alt="Short Drama (短剧)"></a> | [Short Drama (短剧)](models/seedance-2.5/cases/short-drama.md) | 13 |
| <a href="models/seedance-2.5/cases/anime-drama.md"><img src="images/seedance-2.5/case9/preview.webp" width="160" alt="Anime Drama (漫剧)"></a> | [Anime Drama (漫剧)](models/seedance-2.5/cases/anime-drama.md) | 11 |
| <a href="models/seedance-2.5/cases/ad-creative.md"><img src="images/seedance-2.5/case12/preview.webp" width="160" alt="Ad Creative (创意广告)"></a> | [Ad Creative (创意广告)](models/seedance-2.5/cases/ad-creative.md) | 7 |
| <a href="models/seedance-2.5/cases/product-video.md"><img src="images/seedance-2.5/case18/preview.webp" width="160" alt="Product Video (电商产品视频)"></a> | [Product Video (电商产品视频)](models/seedance-2.5/cases/product-video.md) | 7 |
| <a href="models/seedance-2.5/cases/talking-head.md"><img src="images/seedance-2.5/case21/preview.webp" width="160" alt="Talking Head (口播和数字人)"></a> | [Talking Head (口播和数字人)](models/seedance-2.5/cases/talking-head.md) | 3 |
| <a href="models/seedance-2.5/cases/ugc-ads.md"><img src="images/seedance-2.5/case24/preview.webp" width="160" alt="UGC Ads (UGC风格广告)"></a> | [UGC Ads (UGC风格广告)](models/seedance-2.5/cases/ugc-ads.md) | 5 |
| <a href="models/seedance-2.5/cases/shorts-reels.md"><img src="images/seedance-2.5/case28/preview.webp" width="160" alt="Shorts & Reels (社媒短视频)"></a> | [Shorts & Reels (社媒短视频)](models/seedance-2.5/cases/shorts-reels.md) | 11 |
| <a href="models/seedance-2.5/cases/product-demo.md"><img src="images/seedance-2.5/case37/preview.webp" width="160" alt="Product Demo (产品演示)"></a> | [Product Demo (产品演示)](models/seedance-2.5/cases/product-demo.md) | 5 |
| <a href="models/seedance-2.5/cases/keyframe-animation.md"><img src="images/seedance-2.5/case42/preview.webp" width="160" alt="Keyframe Animation (首尾帧动画)"></a> | [Keyframe Animation (首尾帧动画)](models/seedance-2.5/cases/keyframe-animation.md) | 3 |
| <a href="models/seedance-2.5/cases/video-extend-edit.md"><img src="images/seedance-2.5/case45/preview.webp" width="160" alt="Video Extend & Edit (视频延长和编辑)"></a> | [Video Extend & Edit (视频延长和编辑)](models/seedance-2.5/cases/video-extend-edit.md) | 11 |
| <a href="models/seedance-2.5/cases/image-edit.md"><img src="images/seedance-2.5/case55/preview.webp" width="160" alt="Image Edit (图生图和修图)"></a> | [Image Edit (图生图和修图)](models/seedance-2.5/cases/image-edit.md) | 2 |
|  | [Product Image (电商主图和海报)](models/seedance-2.5/cases/product-image.md) | 0 |
| <a href="models/seedance-2.5/cases/music-video.md"><img src="images/seedance-2.5/case57/preview.webp" width="160" alt="Music Video (音乐可视化和MV)"></a> | [Music Video (音乐可视化和MV)](models/seedance-2.5/cases/music-video.md) | 5 |
| <a href="models/seedance-2.5/cases/explainer.md"><img src="images/seedance-2.5/case62/preview.webp" width="160" alt="Explainer (教学解说视频)"></a> | [Explainer (教学解说视频)](models/seedance-2.5/cases/explainer.md) | 2 |

## How to Contribute

PRs welcome. Every case needs: a complete, unedited prompt; a real output
preview (a static WebP frame at 700px, `≤2MB`, under `images/caseN/`) plus
the source image for image-to-video cases; and, for self-run cases, the job
id behind the cost line, so the amount traces to the API call that was
billed. Community and official cases must credit and link the original author
or first-party source. Full format,
rules, and the case-sourcing mix: see [`CONTRIBUTING.md`](CONTRIBUTING.md)
and copy [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md) as your starting point.
Not comfortable opening a PR? Use the
[case submission form](../../issues/new?template=add_case.yml) instead.

## Related

- [ofoxai/skills](https://github.com/ofoxai/skills) — Ofox's agent-skill
  repo. Where this repo shows you the prompt, that repo's scenario skills
  let an AI agent (Claude Code, Codex, OpenCode) run it end to end: write
  the prompt, call this same API, download the video, and report the
  bill.

- **Official Seedance 2.5 material** — where this repo's official cases come
  from, and the right place to check a parameter before you trust ours:
  [ByteDance Seed launch post](https://seed.bytedance.com/en/blog/one-take-creation-flexible-referencing-introducing-seedance-2-5) ·
  [ModelArk tutorial](https://docs.byteplus.com/en/docs/ModelArk/2607688) ·
  [ModelArk prompt guide](https://docs.byteplus.com/en/docs/ModelArk/2607689)
  (Chinese originals: [火山方舟 2607688](https://docs.volcengine.com/docs/82379/2607688?lang=zh) ·
  [2607689](https://docs.volcengine.com/docs/82379/2607689?lang=zh))
- [jamez-bondos/awesome-gpt4o-images](https://github.com/jamez-bondos/awesome-gpt4o-images) —
  the same idea for image generation, and the format this repo's case layout
  learned from.

## Acknowledgements

This collection mixes three sources, credited differently on each case: 24
cases are official ByteDance material — prompts and demo footage published by
the Seed team and in the 火山方舟 / BytePlus ModelArk documentation. 46 cases
are community work, individually credited to their X/Twitter or bilibili
author on the case itself, sourced from public prompt libraries (YouMind,
EvoLink) and from bilibili creators' own uploads, and independently
re-verified against each author's original post before being included here.
The remaining 14 (Cases 1001-1014) are our own runs through the Ofox API,
marked `Ofox 实测` — the only ones carrying a `费用` line, each traceable to
the job id it was billed under.
Preview frames are mirrored under the credit line on each case; every prompt
is reproduced complete and unedited.

The numbering jumps from 70 to 1001 on purpose. `N` is the `#case-N` anchor on
`ofox.ai/seedance-2-5-prompts` as well as a heading here, and 1000+ is the
reserved block for Ofox's own runs — renumbering to close the gap would
silently repoint links that are already published.

If you authored something featured here and want it removed, open an issue
titled `Takedown: case-N`. No justification needed beyond identifying yourself.
