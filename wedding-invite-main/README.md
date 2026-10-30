# Disha & Prakhar — Wedding Invitation

Single-page site. No build step, no dependencies to install.
Open `index.html` in a browser and it runs.

## Files

```
index.html          everything — markup, styles, scripts
assets/
  engagement.jpg    Chapter 01
  haldi.jpg         Chapter 02
  sangeet.jpg       Chapter 03
  wedding.jpg       Chapter 04
  vidai.jpg         Chapter 05
```

Keep `index.html` and `assets/` together. The image paths are relative,
so separating them breaks the chapter panels.

## Putting it online

Drag this whole folder onto **Netlify Drop** (app.netlify.com/drop) or
**Cloudflare Pages**. Both are free and give you a URL in seconds.
Vercel and GitHub Pages work the same way. Nothing here needs a server.

## Things you may want to change

**RSVP destination** — search `ENDPOINT` in `index.html`. Currently posts to
Formspree form `xqerjvjg`. Replace the URL to send replies elsewhere.
Note: the free Formspree tier caps at 50 submissions per month.

**Countdown target** — search `TARGET`. Set to 19 Jan 2027, 8:00 PM IST.

**Chapter layout** — below 900px the copy is overlaid on the photograph, with
a warm scrim weighted to the lower half for legibility and the chapter numeral
moved to the top corner. At 900px and above it reverts to the two-column split
with dark ink on cream. Search `Phones: the words sit on the photograph`.
The scrim strength is the `rgba(44,32,14,…)` gradient stops.

**Image crops** — each chapter panel carries a `--pos` value, e.g.
`--pos:72% center`. These portraits have the couple off to one side, so
the crop is tuned per image. Adjust the percentage if one looks off.

**Venues** — now three cards, each with a side badge on the map:

| Venue | Badge | Layout |
|---|---|---|
| Atithi Inn | Groom's Side | Engagement, Haldi, Mehendi & Sangeet |
| Aaradhya | Bride's Side | Haldi, Mehendi & Sangeet |
| Viviana Greens Lawn | Both Families | Wedding, Vidai - full-width row below |

All three addresses were verified against Google Places and each map is
centred on exact coordinates rather than a name search, so the pins can't
drift onto a similarly-named place. The wedding venue spans the full row on
purpose — two family venues above, the shared one below.

Aaradhya's pin shows no name label because the record is a premise rather
than a registered business; the location itself is correct.

**Event locations** — Haldi and Mehendi & Sangeet each list both venues with a
`<span class="who">` side label. Engagement is Atithi Inn only; Wedding and
Vidai are both Viviana Greens.

**Weekday labels are wrong.** The chapters read Friday 17th, Saturday 18th,
Sunday 19th, Wednesday 20th January. Those weekdays belong to **2025**. For
2027 the correct days are Sunday 17th, Monday 18th, Tuesday 19th and
Wednesday 20th — so four of the five are off. Fix before sharing the link.

**Music** — `assets/music.mp3`, 28.6s, 128 kbps. A round toggle sits
bottom-right. Behaviour:

- The speaker reads **on** from the moment the page loads, and the icon tracks
  the visitor's *intent* rather than momentary playback. To start muted
  instead, set `wants=false` at the top of the script.
- It cannot actually make sound until the visitor's first tap, scroll, or
  keypress; browsers refuse autoplay with audio and there is no way round it.
  So the icon says on, and the music arrives the instant they touch anything.
- Tapping the speaker before the music has started counts as opting out, and
  later taps elsewhere on the page will not override that.
- Fades in to 35% volume rather than starting at full blast. Tune `VOL` at the
  top of the script.
- The track is short and ends mid-phrase, so it does **not** use the native
  `loop` attribute — a hard loop clicked audibly every 29 seconds. Two audio
  elements leapfrog each other with a 2.2s crossfade instead, set by `XF`.
- Pauses when the visitor leaves the tab, resumes where it left off.
- Works whether the visitor's first interaction is the button itself or
  anywhere else on the page. Both routes are tested.
- If the file is missing or unplayable the button removes itself and the page
  behaves as though the feature were never there.
- Swapping the track: replace `assets/music.mp3`. Nothing else needs editing —
  the crossfade reads the duration at runtime.
- To remove entirely: delete the `<audio>` element, the `.bgm-btn` button, and
  the final `<script>` block.

**Weekdays** — the event weekdays currently read Saturday 18th and
Sunday 19th. In January 2027 the 18th is a Monday and the 19th a Tuesday;
those labels match January 2025. Worth correcting before you send the link.

**Ganesha artwork** — the watermark behind the bride and groom names is a
lotus mandala drawn in SVG, standing in for the Ganesha illustration on the
original. Search `class="wm"` to swap in your own file.

**Removing the RSVP** — delete the `<section class="rsvp">` block and the
RSVP script block at the bottom. Nothing else depends on them.
