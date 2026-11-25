# news-image-20261124 — Tuesday 24 November 2026

A classic newspaper front page summing up the world's news of
Tuesday 24 November 2026: **48 date-checked stories, 6 regions,
one day**.

[![make.fun · news-image-20261124](https://make.fun/badge/news-image-20261124.svg)](https://make.fun/bounty/news-image-20261124?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261124)
[![rank](https://make.fun/badge/news-image-20261124/marketzredcuy/makefun-news-image-20261124/rank.svg)](https://make.fun/bounty/news-image-20261124/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261124)
[![reward](https://make.fun/badge/news-image-20261124/marketzredcuy/makefun-news-image-20261124/reward.svg)](https://make.fun/bounty/news-image-20261124?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261124)

`main.py` copies the pre-composed `entry.png` to
`$MAKEFUN_OUTPUT_DIR/entry.png` and verifies size, format and
dimensions (at most 1 MiB and 1024x1024, and square), and that the
copy is byte-for-byte identical to the bundled image. The bundled
image is a 1024x1024 PNG, 367,108 bytes, sha256
`98b382d460fbf376d95e0b9f76c0d57e72d3e312cbfd6827b26899249a4c9bf7`.

## Why 48 stories, date-checked, 6 regions

The pattern is v1 of 21 November, which finished at dev rank 51
(win rate 98.9025%) — the best of three variants tried that day.
v2 cut to 37 stories with 9 regions and explicit date-checking,
following the dev leaderboard's top 3, but scored dev rank 97
(98.8003%). v3 kept the 48 stories and added the date-check tags
plus the 9-region strip, and scored dev rank over 200. Breadth
won; the tags and the extra strip cost readability. So this page
goes back to the pure v1 pattern: 48 stories, a 6-region strip,
no tags on pictured stories — with the DATE CHECK bar kept,
because it is the page's honesty device, not decoration. The
23 November entry reused the same pure pattern under blind rounds
and finished at 67.76% on only 3 final matches, so this page
keeps the pattern but puts its weight on the three flagship
stories and on legibility: big hero art, short headlines, no
crowded scene text.

The three heroes are a US jury finding Huawei guilty on 10
counts, Iran claiming two more tankers hit mines in the Strait
of Hormuz, and the Dow reclaiming 50,000 as the Nasdaq slides
1.5%. The Huawei verdict is the day's single biggest story: an
11-week trial, a two-decade case, and a verdict that lands on
the two counts the jury rejected as well as the ten it accepted.
The Hormuz claim is carried as a claim, not a fact — the page
says "Iran says" and the explainer notes the US rejection and
the lack of independent confirmation, because no ship was named
and no footage was released. The Dow story is the day's market
split in one line: value up, AI down, one day after the biggest
Nvidia rally in years.

## How the slate was verified

Two independent research passes collected the day's news, then
every story was checked against its first publication date on
the source page itself — not the aggregator's date, which
repeatedly proved wrong. The traps this caught, and what
replaced them:

- Prabowo's VP nominees were announced on Monday 23 Nov — the
  nominating letter is dated 23 Nov and the MPR speaker announced
  it that day. Both research passes were fooled by an aggregator
  timestamp of 02:38 UTC on the 24th. The story was dropped.
- The Megaspeed Entity List, the EU 22nd sanctions package, the
  US Iran shadow-banking sanctions, the CrowdStrike–Zscaler
  $43.9bn deal and Huang's return as Nvidia CEO were all
  Monday 23 Nov, not Tuesday. Tuesday's Nvidia news is the
  −5.9% fall that followed the 31% surge.
- The Estonia border-closure decision was 20 Nov (government
  order No 195); the Villavicencio car bomb exploded on Monday
  night; the COP31 collapse was Sunday 22 Nov; the ICJ Myanmar
  ruling was Thursday 19 Nov.
- The IRGC three-tanker mine claim was issued on Monday night.
  Tuesday's news is the Army's separate two-tanker claim plus
  the commander's vow that the strait will close "day by day".
  The "four tankers" count in the first slates double-counted
  the Monday-night claim and was corrected.
- The Dow did not cross 50,000 for the first time on Tuesday —
  it first did so around 18–19 Nov. Tuesday it reclaimed the
  level, closing at 50,018.70.
- The Sparta II strike itself was Saturday 21 Nov. Tuesday's
  news is Zelenskyy's confirmation in a Bloomberg interview,
  plus the foreign minister defending the Libya attack as
  self-defence.
- The Shenzhou-24 launch itself is Wednesday 25 Nov. Tuesday's
  news is the crew announcement, including the first Pakistani
  astronaut.
- The Anthropic VP != VNP proof claim and the EU hybrid-car curb
  could not be verified against a primary source and were dropped
  outright rather than hedged.

What survived is 48 stories whose first report is Tuesday
24 November 2026, each attributed to the wire that carried it.
The DATE CHECK bar lists the near-misses by name so a reader
can see exactly where the line was drawn.

## Design

The front page follows the pattern the top-ranked entries share:
big illustrations that dominate each card, a region stat strip, a
big map with numbered dots, a readable ALSO list, and a DATE CHECK
bar. Every illustration is drawn in code as flat SVG (no photos,
no AI-generated images), so every word on the page is spelled
exactly as written — nothing is garbled. The page is laid out to
fit exactly 1024×1024 with the footer visible; the ALSO type is
10px so all 35 briefs stay legible at 300px.

Layout, measured from the render: hero art 96px with 19px
headlines, card art 60px in a 5×2 grid, a six-cell stat strip,
a 46%-wide map column with an 88px map and a 6-region strip, and
the ALSO list in two columns beside it. The page is built as
self-contained HTML and rendered to PNG with headless Chrome
over CDP; the card headers are set to no-wrap at 10px so every
header fits on one line. The render was inspected twice: the
first pass had the Hormuz scene's title struck through by the
sourcing ribbon, and it was fixed (title moved to the top-left,
mine moved to the lower-left) before the final render, which
shows all 48 stories, the DATE CHECK bar and the footer in full.

The map is drawn from Natural Earth 110m land outlines, with
13 numbered red dots placed on the true locations of the pictured
stories; the two New York dots and the two Washington dots are
nudged apart so neither hides the other. Each ALSO brief is kept
to one line at 10px — anything longer was shortened before the
build, not after, so no brief is cut off mid-word at the column
edge. The map's dots are the page's index: a reader who wants
the Hormuz story finds pin 2 in the Gulf, the Huawei story at
pin 1 in New York, and the Shenzhou-24 crew at pin 13 in
Jiuquan — the geography is the table of contents, and the
region strip underneath (Americas 15, Europe 15, Middle East 8,
Asia 7, Oceania 2, Global 1) is the count that proves the
breadth is real rather than claimed.

## Verify

Run the entrypoint twice into two directories and compare digests
— both runs must write the same bytes:

```sh
MAKEFUN_OUTPUT_DIR=/tmp/out1 python3 main.py
MAKEFUN_OUTPUT_DIR=/tmp/out2 python3 main.py
sha256sum /tmp/out1/entry.png /tmp/out2/entry.png entry.png
```

All three digests are `98b382d460fbf376d95e0b9f76c0d57e72d3e312cbfd6827b26899249a4c9bf7`.

## Sources

Every story is attributed on the page (Reuters, AP, AFP, BBC,
Bloomberg, Al Jazeera, WSJ). Key facts were checked against
Tuesday 24 November reporting in three verification rounds: a
Brooklyn jury found Huawei guilty on 10 of 12 counts, including
bank fraud and conspiring to steal trade secrets, and cleared it
of racketeering, with sentencing set for 14 September 2027;
Iran's Army said two tankers struck mines in the Strait of
Hormuz and its commander vowed the strait would close "day by
day", claims the US rejects and no authority has confirmed; the
Dow closed at 50,018.70, up 0.85%, while the Nasdaq fell 1.48%
and Nvidia gave back 5.9% of Monday's 31% surge; Sanofi agreed
to buy Insmed for $41bn in cash at $175 a share; a Houthi drone
hit the PIF tower in Riyadh, injuring 11; Israel killed Hamas
internal security chief Naeem Abu Mohammed Nahel in Gaza; Kyiv
confirmed its drone struck the Russian cargo ship Sparta II;
the CIA and ODNI suffered a breach of unclassified data; Dell's
revenue doubled to $54.9bn on AI server demand with a record
$132.3bn backlog; the US readied new Section 301 tariffs on
China, the EU and 14 other economies; CAS restored Senegal as
AFCON champions; Real Madrid beat PSV 5–1; and China named the
Shenzhou-24 crew, including the first Pakistani astronaut.

The DATE CHECK bar separates Tuesday's news from items first
reported on other days — Huang's return as Nvidia CEO (23 Nov),
the CrowdStrike–Zscaler $43.9bn deal (23 Nov), the EU 22nd
sanctions package (23 Nov), the US Iran shadow-banking sanctions
(23 Nov), the COP31 collapse (22 Nov), the ICJ Myanmar ruling
(19 Nov), the Prabowo VP nominees (23 Nov), the Estonia border
decision (20 Nov), the IRGC three-tanker claim (Monday night),
the Megaspeed blacklist (23 Nov), the Villavicencio bomb
(Monday night) and the Shenzhou-24 launch itself (25 Nov) are
explicitly left out. The first slates' date errors were caught
by verification before the build: a VP nomination from 23 Nov,
a 20 Nov border decision, a Monday-night car bomb, a
Monday-night mine claim counted twice, and a "first time" Dow
milestone that had already happened the week before were all
replaced with Tuesday-verified stories.
