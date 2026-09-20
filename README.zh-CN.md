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

当代 AI 视频模型的提示词、参数与真实成片合集 —— **3 个模型、276 个案例**，每条都附完整
未删改的提示词、当时的参数、预览帧和可播放成片。由
[Ofox](https://ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts)
收集、核对，标注为自跑的那些也是通过 Ofox 调用的 —— 三个模型在 Ofox 上共用同一个
`POST /v1/videos` 接口。

```bash
curl -X POST https://api.ofox.ai/v1/videos \
  -H "Authorization: Bearer $OFOX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"bytedance/seedance-2.5","prompt":"A neon-lit Tokyo alley at night, cinematic dolly-in, rain reflections","duration":10,"resolution":"1080p","aspect_ratio":"16:9"}'
# -> {"id": "..."}; 轮询 GET /v1/videos/{id} 直到 "status" 变成 "completed"
```

把 `model` 换成 `minimax/hailuo-3` 或 `alibaba/wan-3.0` 即可 —— 同一个接口、同一套请求体。
完整参数与错误码见
[Ofox 视频 API 文档](https://ofox.ai/docs/api/videos?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts)；
取 key：[app.ofox.ai](https://app.ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts)。

<a id="table-of-contents"></a>

## 模型

| | 模型 | 案例数 | 浏览 |
|:---:|---|---:|---|
| <a href="models/seedance-2.5/README.zh-CN.md"><img src="images/seedance-2.5/case1/preview.webp" width="160" alt="Seedance 2.5"></a> | **Seedance 2.5** — 字节跳动<br><sub>4–30 秒 · 最高 1080p · 8 种宽高比 · 自带同步音频</sub> | 85 | [案例](models/seedance-2.5/README.zh-CN.md) · [案例页](https://ofox.ai/zh/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |
| <a href="models/hailuo-3/README.zh-CN.md"><img src="images/hailuo-3/case1/preview.webp" width="160" alt="MiniMax Hailuo 3"></a> | **MiniMax Hailuo 3** — MiniMax<br><sub>文生 / 图生 / 参考生视频 · 原生音轨</sub> | 120 | [案例](models/hailuo-3/README.zh-CN.md) · [案例页](https://ofox.ai/zh/hailuo-3-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |
| <a href="models/wan-3/README.zh-CN.md"><img src="images/wan-3/case1/preview.webp" width="160" alt="通义万相 Wan 3.0"></a> | **通义万相 Wan 3.0** — 阿里巴巴<br><sub>2–30 秒 · 最高 1080p · 参考生视频 / 首尾帧 / 视频编辑 / 延长</sub> | 71 | [案例](models/wan-3/README.zh-CN.md) · [案例页](https://ofox.ai/zh/wan-3-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |

## 一个案例包含什么

每个模型目录下的每条案例，都带同样六样东西：

- **完整未删改的提示词**。不是转述、不是整理过的版本 —— 原文里的错字和半角标点也照原样保留。
- **当时的参数**，一行写全：模型 · 平台 · 模式 · 时长 · 分辨率 · 宽高比 · 音频。
  来源没公布的一律写 `未标注`，不猜。
- **预览帧**（WebP，长边 700px），点进去是 ofox.ai 上可播放的成片。
- **输入素材** —— 参考图、参考视频、关键帧、被编辑的源视频，用到了就附上。
- **署名行**，写明原作者或一手来源并给出回链。
- **实付费用**，只有我们自己跑的案例有，且能追回到出账的那个 job id。

## 如何贡献

欢迎提 PR。先找到你的案例属于哪个模型
（`models/<模型>/cases/<分类>.md`），照该文件里已有的格式写。每条案例都需要：完整未删改的
提示词；真实成片的预览帧（静态 WebP，长边 700px，`≤2MB`，放在 `images/<模型>/caseN/`），
图生 / 参考生类案例还要附输入素材；自跑案例的费用行要带上出账的 job id。社区与官方案例
必须署名并链接原作者或一手来源。完整格式与规则见 [`CONTRIBUTING.md`](CONTRIBUTING.md)
（英文），模板从 [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md) 复制。不方便提 PR 的话，可以用
[案例投稿表单](../../issues/new?template=add_case.yml)。

⚠️ **`hailuo-3` 和 `wan-3` 的案例文件是生成的**，直接改会被下次导出覆盖 —— 请针对案例
内容提 PR，由维护者同步回上游。`seedance-2.5` 那份是真源，可以直接改。

## 相关链接

- [ofoxai/skills](https://github.com/ofoxai/skills) —— Ofox 的 agent skill 仓库。
  这个仓库给你看提示词，那个仓库的场景 skill 能让 AI agent（Claude Code、Codex、
  OpenCode）端到端跑完：写提示词、调同一个 API、下载视频、报账单。
- **官方素材** —— 本仓库官方案例的出处，也是核对参数时该信的一手来源。
  Seedance 2.5：[ByteDance Seed 发布博客](https://seed.bytedance.com/zh/blog/one-take-creation-flexible-referencing-introducing-seedance-2-5) ·
  [火山方舟 2607688](https://docs.volcengine.com/docs/82379/2607688?lang=zh) ·
  [2607689](https://docs.volcengine.com/docs/82379/2607689?lang=zh)。
  Hailuo 3：[MiniMax-H3 模型卡](https://huggingface.co/MiniMaxAI/MiniMax-H3)。
  Wan 3.0：[Wan 3.0 展示页](https://www.aliyun.com/benefit/scene/wan) ·
  [阿里云提示词指南](https://help.aliyun.com/zh/model-studio/text-to-video-prompt)。
- [jamez-bondos/awesome-gpt4o-images](https://github.com/jamez-bondos/awesome-gpt4o-images) ——
  图像生成领域的同类合集，本仓库的案例排版参考了它。

## 致谢

案例来自三类来源，每条下方分别署名，各模型的构成不同：

- **Seedance 2.5**（85 条）—— 24 条字节跳动官方素材，来自 Seed 团队的发布与
  火山方舟 / BytePlus ModelArk 文档；46 条社区作品，逐条署名到 X/Twitter 或 B 站原作者，
  收录前均核对过原帖；15 条是我们自己通过 Ofox API 跑的，标为 `Ofox 实测`，也是全仓唯一
  带 `费用` 行的案例。
- **MiniMax Hailuo 3**（120 条）—— 3 条官方案例取自 MiniMax 自家 HuggingFace 模型卡里的
  可复现请求脚本（提示词、参数、成片三者精确对应）；117 条社区案例来自 X 公开原帖，
  逐字提示词 + 成片镜像 + 署名回链。
- **Wan 3.0**（71 条）—— 全部是阿里官方一手材料：8 条来自 Wan 3.0 展示页，63 条来自官方
  《Wan3.0 视频创作者手册》。没有社区档 —— 能找到的第三方 Wan 素材达不到收录标准
  （关键词抢注仓库；以及一个拿不到单条作品 permalink、无法署名回链的公开广场）。

预览帧在此镜像保存，每个案例下方均附署名；提示词完整未删改地转载。

案例编号按模型各自计数，且**刻意留有断档**。`N` 既是这里的标题编号，也是该模型案例页上的
`#case-N` 锚点 —— 为填平断档而重排编号，会把已经发出去的外链静默指到别的案例上。
Seedance 的编号从 70 跳到 1001，是因为 1000+ 是留给 Ofox 自跑案例的保留段。

如果你是此处收录内容的作者并希望撤下，请开一个标题为 `Takedown: <模型> case-N` 的 issue。
除表明身份外无需其他理由。
