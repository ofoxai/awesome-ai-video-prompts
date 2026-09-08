# Contributing to awesome-seedance-2.5

This repo is a case/prompt showcase for ByteDance's Seedance 2.5 video model, run
through the [Ofox](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5)
API. Every case links back to
[ofox.ai/seedance-2-5-prompts](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=readme&utm_campaign=awesome-seedance-2-5),
so the bar for a new case is: complete prompt, real output preview, and (for
self-run cases) a real bill. Read this before opening a PR.

## Case format

Copy [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md) as your starting point — it carries
both variants plus per-field instructions. The shape, reproduced here for
reference:

`````markdown
<a id="case-N"></a>
### Case N: <title> (by @author or Ofox Team)

<a href="https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=case&utm_campaign=awesome-seedance-2-5#case-N"><img src="images/caseN/preview.webp" width="<the image's real pixel width — 700 landscape, e.g. 394 vertical>" alt="<title>"></a>

▶ [在 ofox.ai 观看完整视频](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=case&utm_campaign=awesome-seedance-2-5#case-N)

<details>
<summary><strong>Prompt</strong> — <first ~150 characters of the prompt, verbatim>…</summary>

~~~~text
<complete, unedited original prompt text>
~~~~

</details>

**参数**：Seedance 2.5 · <provider> · <t2v/i2v/keyframe/extend/edit> · <N>s · <resolution> · <aspect ratio> · <带音频/无音频>
**费用**：$X.XX（job <the job id that was billed>）
**来源**：<original post link, official doc link, or "Ofox 实测">

<sub>Preview © <year> <a href="<source url>">@author</a> · Prompt by <a href="<source url>">@author</a></sub>

[⬆️ 返回目录](#table-of-contents)
`````

Cases with a visual input — `i2v`, 首尾帧动画, 图生图和修图, 视频延长和编辑 —
use variant 2 in [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md), which puts the source
image and the result side by side in a `| 输入 | 输出 |` table. A reader cannot
judge an image-to-video case without seeing what went in.

Two kinds of text live in a case block. The **data** — prompt, `参数` line,
`来源` and its URLs, the `<sub>` credit, the anchor, the case number and title,
and the `images/caseN/` paths — is byte-identical in all three READMEs. The
**navigation chrome** around it — the "watch the full video" label and the
back-to-top label — is localized like every other piece of chrome on the page.
A Chinese button in the English README is a bug, not consistency.

A note on the `参数` / `费用` / `来源` field labels: they're intentionally
kept in Chinese and identical across all three README variants, the same
way model names, durations, and prices are never translated. A case's own
content is not localized — only the section headers and prose around it
differ between `README.md`, `README.zh-CN.md`, and `README.ja.md`. This
keeps every case machine-parseable the same way regardless of which README
file it lives in, since the same case text is expected to appear (or later
sync to the site page) unchanged in all three. Prompts specifically are never
translated for a harder reason: **a translated prompt does not generate the
same clip.**

### Rules

- **Preview**: a static frame from the clip, saved as **WebP** at **700px on
  the long edge** (340px per cell in the input→output variant), stored under
  `images/caseN/` — see [`images/README.md`](images/README.md) for the full
  convention. Not a GIF: at a usable size a 3-second GIF is 2–5 MB and bands
  badly on exactly the gradients Seedance output is full of. Actual video files
  are never committed here; they live on the site page.
- **`<img width>` is the image's real pixel width, not a blanket 700.** A
  landscape frame is 700×394 and reads `width="700"`; a vertical one is around
  402×700 and reads `width="402"`. Measure, don't assume —
  `file images/caseN/preview.webp` prints the dimensions. Writing 700 on a
  vertical frame makes GitHub upscale it to 700×1219, which is blurry (it is
  stretched from 402 real pixels) and eats the entire viewport.
- **Preview must match the prompt**: play the clip before you grab the frame
  and confirm it is what the prompt actually describes. Compare four things —
  orientation and aspect ratio, setting, subject, and the main action. If any
  of them contradicts the prompt, drop the case; do not publish the prompt
  with a frame it did not produce, and do not "fix" the mismatch by softening
  the prompt. A creator can pair a genuine prompt with an unrelated video:
  one candidate rejected on 2026-09-07 described a vertical 9:16 ink-wash
  swordfight in a night courtyard and shipped a landscape 1080×607 gunfight
  in a modern stairwell.
- **Prompt**: the complete, unedited original text. Fold it in `<details>`
  with the first ~150 characters copied verbatim into the `<summary>` as a
  teaser **only when the prompt exceeds ~200 characters** — below that the
  teaser is the whole prompt and the fold shows it twice, so put it inline
  under a plain `**Prompt**` heading. No partial or paraphrased prompts — if you don't have the full prompt,
  don't submit the case. Use `~~~~text` fences, not triple backticks, so a
  prompt that itself contains a code fence (JSON-structured prompts are common
  here) can't break the block.
- **Numbering**: `N` is the same in the `<a id="case-N">` anchor, the heading,
  the `#case-N` link fragment, and the `images/caseN/` directory. Cases are
  numbered in reading order — the order you scroll past them, not the order
  they were added.
- **Title**: `Case N: <English title> (<中文标题>) — by <author>`. Attribution
  uses an em-dash, not a second parenthetical.
- **`参数`**: state the **provider** as well as the model. fal and Replicate cap
  Seedance 2.5 at 720p while ByteDance native and Ofox reach 1080p, so the same
  prompt produces different output depending on where it ran. If a value was
  never published, write `未标注` — do not infer duration or resolution from the
  video file. Official demo reels in particular are often presentation cuts that
  run longer than the prompt requested.
- **Cost line (`费用`)**: only on self-run cases, written
  `**费用**：$3.30（job <id>）` — the amount actually billed
  (`usage.video_cost` from the completed job) followed by the job id it was
  billed under. The job id is the credential; there is no `bill.png` in this
  repo, because a screenshot of a billing page cannot be tied to a single clip
  and rounds the figure it shows. Community and official cases omit the line
  entirely rather than estimating a number.
- **Attribution (`来源`)**: community cases must credit and link the
  original author (an X/Twitter post, a 即梦 profile/work URL, or a bilibili
  video/space URL). Official cases cite the first-party source (ByteDance
  Seed blog, 火山方舟 / BytePlus docs) — not a blog that reposted it. Ofox's
  own runs use `Ofox 实测`.
- **`<sub>` credit line**: required on every community and official case.
  Delete it on `Ofox 实测` cases.
- **Category**: pick the closest scenario category already in the README's
  table of contents. If none fits, say so in the PR description rather than
  inventing a new category — categories change from a repo-wide decision,
  not a single PR.

## Rights and takedown

By submitting a case you confirm you have the right to share the prompt text and
the preview frame, and that the attribution you provide is accurate.

If you are the author of a prompt or a clip featured here and want it removed,
open an issue titled `Takedown: case-N`. The media will be hidden while the
claim is reviewed, and the case removed if the claim holds. No justification is
required beyond identifying yourself as the rights holder.

Preview frames from community and official cases are mirrored into
`images/caseN/` rather than hotlinked, and every one carries a `<sub>` credit
line naming the source. Contributors are credited in `## Acknowledgements`.

## Case sourcing mix

Once real cases start landing, the target mix is:

- **Self-run** — ≥50% of the total. Run through the Ofox API, record the
  prompt, the exact parameters, the job id, and the `usage.video_cost` it was
  billed. Target 5 per scenario category to start.
- **Official** — examples from the ByteDance Seed blog or the 火山方舟 /
  BytePlus ModelArk Seedance 2.5 docs, labeled as such in the `来源` field.
  Take them from the first-party page, not from a blog that republished them:
  reposts routinely normalize whitespace, which breaks the "complete, unedited"
  requirement.
- **Community** — sourced from X posts tagged "seedance 2.5", 即梦社区,
  bilibili uploads whose description carries the full prompt, or Reddit
  r/aivideo. Only accepted if the full prompt is publicly available;
  screenshots of a result with no prompt text don't qualify. Aggregated prompt
  libraries count as a lead, not a source — verify against the author's own
  post, and apply the "Preview must match the prompt" rule above before
  taking a frame.

## Submitting without a PR

If you'd rather not open a pull request, use the
[case submission form](../../issues/new?template=add_case.yml). It asks for the
same things this document requires — complete prompt, category, mode, provider,
parameters, source, and the rights confirmation — and a maintainer turns it into
a case. The form is also the better route when you have the video but not a
preview frame: we extract the frame.

## Opening a PR

1. Add your case under the right category section using
   [`CASE_TEMPLATE.md`](CASE_TEMPLATE.md), in all three README files
   (`README.md`, `README.zh-CN.md`, `README.ja.md`) — the case content is
   identical across all three, only the surrounding language differs.
2. Add the preview (and `input.webp` for an input→output case) under
   `images/caseN/`, following [`images/README.md`](images/README.md).
3. Bump the case-count badge in each README if you're keeping it in sync.
4. Open a PR. A maintainer reviews for: complete prompt, working preview,
   correct category, accurate `参数`, and (for community and official cases)
   proper attribution.
