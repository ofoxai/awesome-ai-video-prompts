<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-CC0--1.0-lightgrey.svg" alt="License: CC0-1.0"></a>
  <a href="#table-of-contents"><img src="https://img.shields.io/badge/cases-299-blue.svg" alt="Case count: 299"></a>
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

Prompts, parameters, and real output for the current generation of AI video
models — **299 cases across 3 models**, with complete, unedited prompts,
disclosed request parameters, and preview frames. Playable clips are linked
where collected. Collected, verified, and (where marked) run through
[Ofox](https://ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts),
which serves all three models behind one `POST /v1/videos` endpoint.

```bash
curl -X POST https://api.ofox.ai/v1/videos \
  -H "Authorization: Bearer $OFOX_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"bytedance/seedance-2.5","prompt":"A neon-lit Tokyo alley at night, cinematic dolly-in, rain reflections","duration":10,"resolution":"1080p","aspect_ratio":"16:9"}'
# -> {"id": "..."}; poll GET /v1/videos/{id} until "status" is "completed"
```

Swap `model` for `minimax/hailuo-3` or `alibaba/wan-3.0` — same endpoint, same
request shape. Full parameter reference and error codes:
[Ofox video API docs](https://ofox.ai/docs/api/videos?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts).
Get a key: [app.ofox.ai](https://app.ofox.ai?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts).

<a id="table-of-contents"></a>

## Models

| | Model | Cases | Browse |
|:---:|---|---:|---|
| <a href="models/seedance-2.5/README.md"><img src="images/seedance-2.5/case1/preview.webp" width="160" alt="Seedance 2.5"></a> | **Seedance 2.5** — ByteDance<br><sub>4–30s · up to 1080p · 8 aspect ratios · synced audio</sub> | 92 | [cases](models/seedance-2.5/README.md) · [prompts page](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |
| <a href="models/hailuo-3/README.md"><img src="images/hailuo-3/case1/preview.webp" width="160" alt="MiniMax Hailuo 3"></a> | **MiniMax Hailuo 3** — MiniMax<br><sub>text / image / reference to video · native audio</sub> | 127 | [cases](models/hailuo-3/README.md) · [prompts page](https://ofox.ai/hailuo-3-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |
| <a href="models/wan-3/README.md"><img src="images/wan-3/case1/preview.webp" width="160" alt="Tongyi Wanxiang Wan 3.0"></a> | **Tongyi Wanxiang Wan 3.0** — Alibaba<br><sub>2–30s · up to 1080p · reference / first-last frame / edit / extend</sub> | 80 | [cases](models/wan-3/README.md) · [prompts page](https://ofox.ai/wan-3-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-ai-video-prompts) |

## What a case looks like

Every case, in every model folder, carries the same six things:

- **The prompt, complete and unedited.** Not a paraphrase, not a tidied
  version — including the original's own typos and half-width punctuation
  where the source had them.
- **The parameters** it ran with, as a single line: model · provider · mode ·
  duration · resolution · aspect · audio. Anything the source did not publish
  reads `未标注` rather than a guess.
- **A preview frame** (WebP, 700px on the long edge) linking to the playable
  clip on ofox.ai.
- **The input material** — reference images, reference videos, keyframes, the
  source clip of an edit — where the case used any.
- **A credit line** naming the original author or first-party source, with a
  link back to it.
- **The cost**, on cases we ran ourselves, traceable to the job id it was
  billed under.

## How to Contribute

PRs welcome. Pick the model folder your case belongs to
(`models/<model>/cases/<category>.md`) and follow the format already in that
file. Every case needs: a complete, unedited prompt; a real output preview (a
static WebP frame, 700px on the long edge, `≤2MB`, under
`images/<model>/caseN/`) plus the input material for image/reference cases;
and, for self-run cases, the job id behind the cost line. Community and
official cases must credit and link the original author or first-party source.
Full format and rules: [`CONTRIBUTING.md`](CONTRIBUTING.md); copy
[`CASE_TEMPLATE.md`](CASE_TEMPLATE.md) as your starting point. Not comfortable
opening a PR? Use the
[case submission form](../../issues/new?template=add_case.yml) instead.

⚠️ **The `hailuo-3` and `wan-3` case files are generated** from Ofox's gallery
data and will be overwritten — open your PR against the case content and a
maintainer will land it upstream. The `seedance-2.5` files are the source of
truth and can be edited directly.

## Related

- [ofoxai/skills](https://github.com/ofoxai/skills) — Ofox's agent-skill
  repo. Where this repo shows you the prompt, that repo's scenario skills
  let an AI agent (Claude Code, Codex, OpenCode) run it end to end: write
  the prompt, call this same API, download the video, and report the
  bill.
- **Official material** — where this repo's official cases come from, and the
  right place to check a parameter before you trust ours.
  Seedance 2.5: [ByteDance Seed launch post](https://seed.bytedance.com/en/blog/one-take-creation-flexible-referencing-introducing-seedance-2-5) ·
  [ModelArk tutorial](https://docs.byteplus.com/en/docs/ModelArk/2607688) ·
  [prompt guide](https://docs.byteplus.com/en/docs/ModelArk/2607689).
  Hailuo 3: [MiniMax-H3 model card](https://huggingface.co/MiniMaxAI/MiniMax-H3).
  Wan 3.0: [Wan 3.0 showcase](https://www.aliyun.com/benefit/scene/wan) ·
  [Alibaba Cloud prompt guide](https://help.aliyun.com/zh/model-studio/wan3-video-generation-prompt-guide).
- [jamez-bondos/awesome-gpt4o-images](https://github.com/jamez-bondos/awesome-gpt4o-images) —
  the same idea for image generation, and the format this repo's case layout
  learned from.

## Acknowledgements

Cases come from three kinds of source, credited differently on each one, and
the mix is different per model:

- **Seedance 2.5** (92) — 24 official ByteDance cases from the Seed team's
  posts and the 火山方舟 / BytePlus ModelArk docs; 53 community cases credited
  individually to their X/Twitter or bilibili author and re-verified against
  the original post; 15 our own runs through the Ofox API, marked `Ofox 实测`
  and the only ones carrying a `费用` line.
- **MiniMax Hailuo 3** (127) — 3 official cases from MiniMax's own HuggingFace
  model card (the reproducible request scripts, so prompt, parameters and clip
  match exactly); 124 community cases from public X posts, verbatim prompt,
  mirrored clip, credited and linked.
- **Wan 3.0** (80) — 74 official Alibaba cases: 8 from the Wan 3.0 showcase,
  63 from the Creator Handbook, and 3 from the Wan 3.0 prompt guide;
  6 community cases credited and linked to their original X or Reddit posts.

Preview frames are mirrored under the credit line on each case; every prompt
is reproduced complete and unedited.

Case numbering is per model and has deliberate gaps. `N` is both the heading
here and the `#case-N` anchor on the model's prompts page, so renumbering to
close a gap would silently repoint links that are already published. On
Seedance the numbering jumps from 77 to 1001 because 1000+ is the reserved
block for Ofox's own runs.

If you authored something featured here and want it removed, open an issue
titled `Takedown: <model> case-N`. No justification needed beyond identifying
yourself.
