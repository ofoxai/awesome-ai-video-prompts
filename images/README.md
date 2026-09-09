# `images/` convention

This directory holds only the small preview assets that a case entry embeds
inline in its category file under `cases/` (and that the README index uses as
category thumbnails). It never holds the actual generated video files.

## Layout

```
images/
  banner.png       # repo banner, ~1280x400, linked from all three READMEs
  case1/
    preview.webp   # required — the output still, 700px on the long edge
    input1.webp    # input-asset strip, one file per asset, 200px long edge
    input2.webp
  case42/
    preview.webp   # 340px — input->output variant
    input.webp     # the output's frame-for-frame counterpart, 340px
  case2/
    preview.webp
  ...
```

One directory per case, named `caseN` to match the case's number in its
category file (e.g. `### Case 12: ...` → `images/case12/`). Case blocks live in
`cases/<category>.md`, one directory down, so they reference the files as
`../images/caseN/…`; the README index, at the root, uses `images/caseN/…`.

## Rules

- **Preview format: WebP, not GIF.** A static frame from the clip, saved as
  `.webp`. This is the convention across comparable video-prompt repos, and it
  is a quality decision, not just a size one: a 3-second GIF at a usable size
  lands at 2–5 MB and bands badly on gradients and skin tones, which is exactly
  what Seedance output looks like. A WebP still at the same size is ~300 KB and
  keeps the detail.
- **Preview size: 700px on the long edge** for a single-output case, **340px on
  the long edge** for each cell of an input→output case, and **200px on the long
  edge** for each cell of an input-asset strip. 700px is the width at
  which motion in a still is legible; below that a video frame reads as a
  thumbnail. It is the *long edge* that is capped, so a landscape frame is
  700×394 while a vertical one is around 402×700 — a 9:16 clip scaled to 700
  *wide* would be 1244px tall and swamp the page.
- **The `<img width>` in the case block is the file's real pixel width.** Not a
  blanket 700. GitHub renders an `<img>` from `width` plus the file's intrinsic
  aspect ratio, so `width="700"` on a 402×700 vertical frame upscales it to
  700×1219 — visibly blurry, since it is stretched from 402 real pixels, and
  tall enough to fill the viewport. Measure the file instead of assuming:

  ```bash
  file images/caseN/preview.webp    # → ... 402x700 ...  so width="402"
  ```

  Landscape frames do read `width="700"`, but only because that is their real
  width. To audit every case at once:

  ```bash
  for f in images/case*/*.webp; do file "$f" | grep -oE '[0-9]+x[0-9]+' | head -1 | \
    awk -F x -v f="$f" '$2>$1 {print f, $0, "-> width=\"" $1 "\""}'; done
  ```
- **Size limit**: `≤2MB` per file — but a correctly-made WebP preview should
  land nowhere near it (~250–350 KB is typical). If you are approaching the cap,
  something is wrong with the export.
- **Two input shapes, chosen by what the input *is*.** Any case whose `参数`
  mode is not `t2v` has to account for its input one of three ways:

  | The input is… | Files | Cell size |
  |---|---|---|
  | the output's frame-for-frame counterpart (i2v source, first/last frame) | `input.webp` | 340px |
  | reference material (r2v refs, keyframe set, storyboard, 白模, edit/extend source) | `input1.webp` … `inputN.webp` | 200px |
  | never published | none — the case carries `**输入素材**：未公开 —— <why>` | — |

  Strip files are numbered **in the order the prompt references them**, because
  that number is the only thing tying a cell to a `@图片1` or `<3pic>` token.

- **A video input contributes its first frame, and the label has to say so.**
  This repo never commits video (see below), so a reference *video* appears in
  the strip as a still — labelled `@视频1 首帧` / `原视频首帧`, never as a plain
  reference image. Of the 51 strip assets in the repo today, 18 come from
  reference videos this way.

- **Retired rule: compositing several inputs into one `input.webp`.** It used to
  say a multi-input case should paste its inputs side by side into a single
  file, and that a case citing "one style reference out of several" should show
  no input at all — the reasoning being that showing one input out of seven
  misleads more than showing none. That diagnosis was right and the fix was
  wrong: show **all** of them in a strip, each labelled. Compositing also
  destroyed the per-asset labels, and case 12 (1 image + 6 videos) and case 43
  (1 白模 clip + 9 keyframes) do not fit one cell at any size.
- **No billing screenshot.** A self-run case's `费用` line carries the job id
  it was billed under (`**费用**：$3.30（job 844c9145-…）`), which is the
  credential — the cost comes from `usage.video_cost` on the completed job, at
  full precision. A screenshot of a billing page cannot be tied to one clip and
  rounds what it shows, so `bill.png` does not exist in this repo and should not
  be added.
- **Mirror, don't hotlink.** For community and official cases, save the frame
  into `images/caseN/` rather than linking someone else's CDN. Hotlinked assets
  break, and several official demo assets sit on doc-platform CDNs with no
  stability guarantee. The `<sub>` credit line in the case block is what carries
  the attribution.
- **No video files.** The actual `.mp4` output is never committed to this
  repo — it lives on the `ofox.ai/seedance-2-5-prompts` page, which the preview
  links to. This keeps the repo small and keeps the site page as the canonical
  place to watch the full clip. (Committing an mp4 would not even work: GitHub
  serves files from `raw.githubusercontent.com` as `application/octet-stream`
  with `nosniff`, so an HTML5 player pointed at one renders but never plays.)

## Current state

`banner.png` (1280×400) plus `case1/` … `case70/` and `case1001/` …
`case1014/` — round 2's official ByteDance cases and the community cases
landed alongside them, then the 14 Ofox self-run cases in the reserved 1000+
block.

Nine `input.webp` files (the 340px counterpart variant): `case42/` plus the
eight i2v self-run cases (`case1005`-`case1008`, `case1010`,
`case1012`-`case1014`).

Fifty-one `inputN.webp` files (the 200px strip) across 15 official cases —
`case1` (4), `case12` (7), `case13` (1), `case23` (8), `case29` (6), `case43`
(10), `case45` (1), `case48` (1), `case49` (3), `case50` (1), `case51` (1),
`case52` (4), `case53` (1), `case54` (2), `case57` (1). All are ByteDance
official doc assets, mirrored from `arkdocs.tos-cn-beijing.volces.com` and
`ark-project.tos-cn-beijing.volces.com`; 202 KB for all 51, largest 9 KB.

The remaining 22 non-t2v cases have no input files and are not supposed to:
their inputs were never published, and each says so on its `**输入素材**` line.

There is no `bill.png` anywhere, by design — see the billing rule above.

The banner is generated from the repo's own case previews — a darkened mosaic of
real Seedance 2.5 output with the title over it — so it cannot drift from what
the repo actually contains.

It picks tiles **by case number**, which makes it a downstream consumer of the
numbering: renumbering the cases silently repoints the banner at different
images, and it will happily crop a vertical or square preview into an unreadable
sliver. Regenerate and look at it after any renumber. Adding cases at the end is
harmless.
