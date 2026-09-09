# Case template

Copy the block for your case type below, fill in the placeholders, and append it
to the right category file — `cases/<category>.md`, and, since a case's own
content is never localized, the same spot in `cases/<category>.zh-CN.md` and
`cases/<category>.ja.md` too — only the navigation chrome differs between the
three files. The READMEs hold only the index: add the case's title to the mini
table of contents at the top of each category file, and bump the count on the
category's row in all three READMEs. See `CONTRIBUTING.md` for the full rules
this format encodes.

Replace `N` with the next case number everywhere it appears — the anchor, the
heading, the `#case-N` link fragment, and the `../images/caseN/` paths must all
carry the same number. Image paths start with `../` because the block lives one
directory down from `images/`.

---

## Variant 1 — output only (t2v, and any case with no visual input)

```markdown
<a id="case-N"></a>
### Case N: <title> (by @author or Ofox Team)

<a href="https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=case&utm_campaign=awesome-seedance-2-5#case-N"><img src="../images/caseN/preview.webp" width="<the image's real pixel width — 700 landscape, e.g. 394 vertical>" alt="<title>"></a>

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
```

## Variant 2 — input → output (i2v, 首尾帧, 图生图)

Use this when the input is the output's **frame-for-frame counterpart** — an
i2v source image, or a first/last frame. The reader compares the two directly,
so they sit side by side at the same size. For a case whose inputs are
*reference material* (r2v reference images/videos, a keyframe set, a storyboard,
a white model, or the source clip of an edit/extend), use variant 3 instead.

```markdown
<a id="case-N"></a>
### Case N: <title> (by @author or Ofox Team)

| 输入 | 输出 |
|:---:|:---:|
| <img src="../images/caseN/input.webp" width="<real pixel width, ≤340>" alt="input"> | <a href="https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=case&utm_campaign=awesome-seedance-2-5#case-N"><img src="../images/caseN/preview.webp" width="<real pixel width, ≤340>" alt="<title>"></a> |

▶ [在 ofox.ai 观看完整视频](https://ofox.ai/seedance-2-5-prompts?utm_source=github&utm_medium=case&utm_campaign=awesome-seedance-2-5#case-N)

<details>
<summary><strong>Prompt</strong> — <first ~150 characters of the prompt, verbatim>…</summary>

~~~~text
<complete, unedited original prompt text>
~~~~

</details>

**参数**：Seedance 2.5 · <provider> · <i2v/keyframe/extend/edit> · <N>s · <resolution> · <aspect ratio> · <带音频/无音频>
**费用**：$X.XX（job <the job id that was billed>）
**来源**：<original post link, official doc link, or "Ofox 实测">

<sub>Input & preview © <year> <a href="<source url>">@author</a> · Prompt by <a href="<source url>">@author</a></sub>

[⬆️ 返回目录](#table-of-contents)
```

## Variant 3 — input-asset strip (r2v, edit, extend, 白模, 首尾帧以外的多素材)

Use this when the case was fed **reference material** rather than a single
counterpart frame: r2v reference images or videos, an ordered keyframe set, a
storyboard grid, a white-model (白模) clip, or the source video of an edit or
extend. There can be one such asset or thirty, so the shape has to scale —
variant 2's single cell cannot hold case 12's seven assets or case 43's ten.

The output preview stays exactly as in variant 1 (700px on the long edge,
linked to ofox.ai). The strip goes **immediately after the ▶ watch line**, so
the inputs read as the evidence behind the output without pushing the output —
the page's click target — below the fold.

```markdown
**输入素材**（<what the assets are, e.g. 4 张官方参考图 / 1 段官方原视频，只取首帧>）

| | | | |
|:---:|:---:|:---:|:---:|
| <img src="../images/caseN/input1.webp" width="<real pixel width, ≤200>" alt="<label>"><br><sub><label></sub> | <img src="../images/caseN/input2.webp" width="<real pixel width, ≤200>" alt="<label>"><br><sub><label></sub> | … | … |
```

Rules specific to the strip:

- **Up to 4 cells per row**, capped at **200px on the long edge** per cell.
  Beyond four, add body rows to the *same* table and pad the last row with empty
  cells — do not emit a second table. GitHub wraps each cell image in a link to
  the full-size file, so the small size costs the reader nothing.
- **Assets are numbered `input1.webp` … `inputN.webp` in the order the prompt
  references them.** The numbering is the only thing tying a cell to a `@图片1`
  or `<3pic>` token in the prompt.
- **The `<sub>` label quotes the prompt's own token for that asset** —
  `@图像1 · 草莓味`, `<video1> 白模首帧`, `@图片 2 · 深色衣服`. That is what makes the
  strip readable next to the prompt. Escape `<` and `>` as `&lt;` / `&gt;`:
  a bare `<2pic>` is an unknown HTML tag and GitHub's sanitizer deletes it.
- **A video input contributes its first frame only, and the label must say so**
  (`@视频1 首帧`, `原视频首帧`). The repo never commits video, so a reader who is
  not told would take a still for a reference *image*.
- The strip's text is case data: **byte-identical in all three language files**, labels
  in Chinese like `参数` / `费用` / `来源`.

## Every non-t2v case must account for its input

The rule is **not** "show the input if you have it" — it is that a case whose
`参数` mode is anything other than `t2v` carries an `**输入素材**` line either
way. Either it shows the assets (variant 2 or 3), or it states in one line that
they were never published:

```markdown
**输入素材**：未公开 —— 原作者只发布了成片，未提供输入素材
**输入素材**：未公开 —— ByteDance Seed 博客只发布了成片，未随文发布输入素材
```

Without that line a reader cannot tell "the input does not exist publicly" from
"the contributor did not finish the block" — and in a repo whose entire claim is
verbatim, checkable evidence, that difference is the product. 22 of the 84 cases
are in this position: 16 community cases whose authors posted only the finished
clip, and 6 official cases sourced from the ByteDance Seed blog, which publishes
output videos and no input assets (verified: both the zh and en pages carry 10
video URLs and a single footer banner image, nothing else).

Pick the wording that is true for the case. Do not use the community wording on
an official case, and never leave the line off to imply the input might exist.

---

## Filling the fields

### `<summary>` teaser

The first ~150 characters of the prompt, copied verbatim, then `…`. Do not
write a description of the prompt — collapsed `<details>` content is invisible
to the browser's Ctrl-F, and the teaser is what makes a case findable on the
page.

### What is byte-identical vs localized inside a case

Discovered while landing the first cases: a case block is not uniformly
"unlocalized". Two kinds of text live in it.

**Byte-identical in all three language files** (`cases/<category>.md` / `.zh-CN.md` /
`.ja.md`) — this is the case *data*:

- the prompt, inside the `~~~~text` fence, and the `<summary>` teaser quoted from it
- the `参数` line, labels and values both
- the `输入素材` line, and the whole variant-3 strip table under it
- the `来源` line and every URL in it
- the `<sub>` credit line
- the `<a id="case-N">` anchor, the case number, and the title after `Case N:`
- the preview `<img>` / `<a>` markup and the `../images/caseN/` paths

**Localized per file** — this is navigation chrome, and every other piece of
chrome in these files is already localized:

- the "watch the full video" call-to-action label
- the back-to-top label (`Back to top` / `回到目录` / `目次に戻る`) — it jumps to the
  `<a id="table-of-contents">` at the top of the category file, so the fragment
  stays `#table-of-contents` in every file

A Chinese button in the English file is a bug, not consistency. The rule that
a case "is not localized" is about the evidence, not the furniture around it.

### Title and attribution

`### Case N: <English title> (<中文标题>) — by <author>`

The title is bilingual, matching the category headings. Attribution follows an
**em-dash**, not a second parenthetical — `(title (中文)) (by X)` nests badly.
Official cases are `— by ByteDance`; our own runs are `— by Ofox Team`.

### When to fold the prompt

Fold in `<details>` only when the prompt is **longer than ~200 characters**.
Below that the `<summary>` teaser is the whole prompt, so the fold prints the
same text twice and charges the reader a click for nothing — show it inline
under a plain `**Prompt**` heading instead. Roughly a third of the official
Seedance prompts are one-liners.

### `参数`

Fixed order, ` · ` separated:

```
Seedance 2.5 · <provider> · <mode> · <duration>s · <resolution> · <aspect ratio> · <audio>
```

- **provider** — which service produced the clip: `Ofox` / `火山方舟` / `即梦` /
  `fal` / `Replicate`. This is not decoration: fal and Replicate cap Seedance
  2.5 at **720p**, while ByteDance native and Ofox go to 1080p, so the same
  prompt yields different output depending on where it ran.
- **mode** — `t2v` / `i2v` / `keyframe` / `extend` / `edit`.
- Duration is 4–30 seconds, any integer. Aspect ratio is one of
  `21:9` / `16:9` / `4:3` / `1:1` / `3:4` / `9:16` / `adaptive`.
- **If a value was never published, write `未标注`.** Do not infer it from the
  video file, and do not guess. A demo video's length is not the prompt's
  `duration` — official demo reels are often presentation cuts that run longer
  than the request.

### `费用`

Delete this line entirely unless the case is self-run. Do not leave it blank,
and do not estimate a number from the pricing table. The value is the actual
charge — `usage.video_cost` from the completed job — not a recomputed
estimate.

The line carries the **job id** in parentheses after the amount:

```
**费用**：$3.30（job 844c9145-9b10-4335-9fdc-ec4937793a2f）
```

The job id is the credential, not a screenshot. Self-run cases are produced
through the Ofox API by `ofoxai/skills`, which records `usage.video_cost` per
job to full precision; a screenshot of a billing page cannot be tied to one
clip and rounds what it shows. There is no `bill.png` in this repo and none
should be added.

### `来源`

- Self-run → `Ofox 实测`
- Community → link the author's original post (X/Twitter, 即梦, or bilibili)
- Official → link the first-party page (ByteDance Seed blog, 火山方舟 / BytePlus docs)

### `<sub>` credit line

Required for every community and official case — it is what makes it
unambiguous that the media and prompt are someone else's work. Delete it for
`Ofox 实测` cases, where `来源` already says so.

### Assets

`images/caseN/preview.webp` at 700px on the long edge (340px in variant 2),
plus `input.webp` for variant 2 or `input1.webp` … `inputN.webp` at 200px for
variant 3. See `images/README.md` for the size rules.
Video files are never committed, and neither is a billing screenshot — the
`费用` line carries the job id instead.

Take the frame only after confirming the clip is really the output of this
prompt — orientation, setting, subject, and main action all have to match. A
creator can pair a genuine prompt with an unrelated video; see the "Preview
must match the prompt" rule in `CONTRIBUTING.md`.

Cap the **long edge**, not the width: a 9:16 clip scaled to 700px wide is
1244px tall and swamps the page. A vertical case is 394×700, a landscape one
700×394.

**The `width` attribute carries the image's real pixel width — never a blanket
700.** GitHub sizes an `<img>` from `width` plus the file's intrinsic aspect
ratio, so `width="700"` on a 402×700 vertical frame upscales it to 700×1219:
blurry, because it is stretched from 402 real pixels, and tall enough to fill
the whole viewport. Read the width off the file rather than assuming it:

```bash
file images/caseN/preview.webp    # → ... 402x700 ...  so width="402"
```

Landscape frames are 700 wide, so they do read `width="700"` — but that is the
measurement agreeing with the rule, not the rule itself. Variant 2 caps each
cell at 340 the same way: 340 on the long edge, `width` set to the real width.

Choose the variant by **what the input is**, not by how many there are:

| The input is… | Variant | Files |
|---|---|---|
| the output's frame-for-frame counterpart (i2v source, first/last frame) | 2 | `input.webp`, 340px cells |
| reference material (r2v refs, keyframe set, storyboard, 白模, edit/extend source) | 3 | `input1.webp` … `inputN.webp`, 200px cells |
| never published | — | none; the `**输入素材**：未公开 ——` line instead |

The old rule here said a logo or "one style reference out of several" did not
qualify, because showing one input out of seven is more misleading than showing
none. That reasoning was right about the failure and wrong about the fix: the
answer is to show **all** of them in a strip, labelled, not to show none.
Compositing several inputs into a single `input.webp` is likewise retired — it
destroyed the per-asset labels that tie a cell to its `@图片1` token.
