# `images/` convention

This directory holds only the small preview assets that a case entry embeds
inline in the README. It never holds the actual generated video files.

## Layout

```
images/
  banner.png       # repo banner, ~1280x400, linked from all three READMEs
  case1/
    preview.webp   # required — the output still, 700px on the long edge
    input.webp     # only for input->output cases (i2v, 首尾帧, 图生图, 延长和编辑)
  case2/
    preview.webp
  ...
```

One directory per case, named `caseN` to match the case's number in the
README (e.g. `### Case 12: ...` → `images/case12/`).

## Rules

- **Preview format: WebP, not GIF.** A static frame from the clip, saved as
  `.webp`. This is the convention across comparable video-prompt repos, and it
  is a quality decision, not just a size one: a 3-second GIF at a usable size
  lands at 2–5 MB and bands badly on gradients and skin tones, which is exactly
  what Seedance output looks like. A WebP still at the same size is ~300 KB and
  keeps the detail.
- **Preview size: 700px on the long edge** for a single-output case, **340px on
  the long edge** for each cell of an input→output case. 700px is the width at
  which motion in a still is legible; below that a video frame reads as a
  thumbnail. It is the *long edge* that is capped, so a landscape frame is
  700×394 while a vertical one is around 402×700 — a 9:16 clip scaled to 700
  *wide* would be 1244px tall and swamp the page.
- **The `<img width>` in the README is the file's real pixel width.** Not a
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
- **Input image** (`input.webp`): the actual source image fed to the model, for
  any case whose mode is `i2v`, `keyframe`, `edit`, or `extend`. Same size cap.
  When a case has **more than one** input — a first-last-frame case has two —
  composite them side by side into the single `input.webp` at the cell's display
  width, first input on the left. Do not add extra table columns; the two-cell
  input→output shape is fixed.
- **Reference assets are not inputs.** A case that merely cites a logo or one of
  several style references uses the single-preview variant. The input cell is
  for the image the reader needs in order to judge the result — showing one
  reference out of seven is more misleading than showing none.
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
block. Nine `input.webp` files exist: `case42/` plus the eight i2v self-run
cases (`case1005`-`case1008`, `case1010`, `case1012`-`case1014`). There is no
`bill.png` anywhere, by design — see the billing rule above.

The banner is generated from the repo's own case previews — a darkened mosaic of
real Seedance 2.5 output with the title over it — so it cannot drift from what
the repo actually contains.

It picks tiles **by case number**, which makes it a downstream consumer of the
numbering: renumbering the cases silently repoints the banner at different
images, and it will happily crop a vertical or square preview into an unreadable
sliver. Regenerate and look at it after any renumber. Adding cases at the end is
harmless.
