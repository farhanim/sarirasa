# Sari Rasa Control Room: Style Guide & UI Kit

Version 4.0 · 19 Nov 2026 · source of truth: [index.html](index.html) (CSS tokens at the top of the file)

v4 follows the WareHub reference more closely:
- **Navigation:** four line tabs on one page (icon + label, icons hidden under 440px; no container; 1px `line-2` rule under the bar, active tab in `accent-ink` with a 2px `accent` underline).
- **Fit:** every tab fits one desktop screen.
- **Color:** neutral icon tiles, with blue charts in the reference style.
- **Patterns:** striped progress bars and segmented bars.
- **Sari:** an insight panel with a dot-grid pattern.
- **Copy:** English throughout.

---

## 1. Principles

The user is Pak Hendra, 52, who checks his phone at 06:30 and needs three answers in 30 seconds: *is the business OK, what needs me, is my money safe.*

1. **One screen, no hunting.** On desktop every tab fits the viewport (tested at 1440×900 and 1366×768). Long lists scroll inside their card, never the page.
2. **Quiet chrome, meaningful color.**
   - Icons sit on neutral gray tiles.
   - Color is reserved for status (green / orange / red / purple) and for data: each data series gets its own hue (blue `#2463EB`, teal `#14B8A6`, violet `#8B5CF6`, amber `#F5A524`, slate `#CBD5E1` for "others"). CV Maju Jaya is always light blue (`#8EC2FF`); production lines are always Line 1 blue, Line 2 teal, Line 3 violet. Receivables aging uses blue → amber → orange → red by lateness.
   - The primary action is the only Azure button.
3. **One component pattern.** Every card is *neutral icon tile + title + one control on the right* (info, filter or action).
4. **Monitoring density.** More data per card, shown with small type and visual patterns (segmented bars, striped bars, stacked charts) rather than big text.
5. **Focus moments in a modal.** Alert details and Sari's answers open as a modal on desktop and a bottom sheet on mobile.

---

## 2. Color

### 2.1 Brand & neutrals

| Name | Token | Hex | Use |
|---|---|---|---|
| Midnight Velvet | `ink` | `#01040C` | Text, target line and label, toast |
| Ivory Lace | `card` | `#FFFFFF` | Cards, dialogs |
| Moonlit Gray | `bg` | `#F5F5F5` | Page |
| — | `tile` | `#F4F5F7` | **Icon tile background** (neutral) |
| — | `raised` | `#F7F8FA` | Table header, hover, impact boxes |
| — | `line` / `line-2` | `#ECECEE` / `#E1E2E6` | Borders / control outlines |
| — | `text-2` / `text-3` | `#4F5562` / `#626875` | Secondary / meta text |
| Azure Dream | `accent-2` → `accent` | `#609FFF` → `#2463EB` | Primary button gradient, send button, user chat bubble, Sari's AI sparkles, Fugodash Surya logo arch (`#609FFF` → `#1A4FC9`) and sun (`#2463EB`) |
| — | `accent-soft` / `accent-line` | `#EEF4FF` / `#D7E5FF` | Sari's surfaces, segmented-control selection, "From Sari" filter chip |

### 2.2 Chart categories: one hue, four steps (reference style)

| Token | Hex | Use |
|---|---|---|
| `c1` | `#1E4FD8` | Main series (other distributors, Line 1, 30+ days late) |
| `c2` | `#4F8BFF` | Second series (Line 2, 16–30 days) |
| `c3` | `#A9CBFF` | Third series / the series to watch (CV Maju Jaya, Line 3, 1–15 days) |
| `c4` | `#DCE8FF` | Remainder ("Others", not yet due) |

Bars are stacked dark at the bottom to light at the top, with a 3px gap and rounded corners on every segment. The target line is Midnight, dashed 6/4, with a black pill label.

### 2.3 Status (meaning only)

| Status | mark | soft | ink |
|---|---|---|---|
| On track | `#2FB86E` | `#EAF8F0` | `#15803D` |
| Watch | `#F07B3F` | `#FEF1E9` | `#B4471A` |
| Critical | `#EF4444` | `#FDEDED` | `#B42318` |
| In progress | `#7C5CFC` | `#F2EFFF` | `#5B3FD9` |

Status always comes as a dot or bar **plus** a word.

### 2.4 Contrast (measured, WCAG 2.2)

| Pair | Ratio |
|---|---|
| `text` on `bg` | 18.81 |
| `text-2` on `bg` | 6.86 |
| `text-3` on `card` | 5.59 |
| `text-3` on `bg` | 5.13 |
| White on `accent` | 5.17 |
| Watch ink on soft | 4.92 |
| On-track ink on soft | 4.58 |
| Critical ink on soft | 5.80 |
| In-progress ink on soft | 5.88 |

---

## 3. Typography

**Inter Tight** (Google Fonts, OFL), weights 400/500/600, tabular figures. **Six sizes only:**

| Token | Desktop | Mobile | Use |
|---|---|---|---|
| `fig` | 26/32 · 500 | 22/28 | KPI number |
| `h` | 20/28 · 500 | 18/26 | Greeting, dialog title, impact figures |
| `title` | 15/22 · 500–600 | 15/22 | Card title, status word, answer headline, mini-stat value |
| `body` | 14/20 · 400–500 | 14/20 (inputs 16) | Default, alert title, table emphasis, buttons |
| `sm` | 13/18 | 13/18 | Sub-text, table cells, deltas, chips |
| `cap` | 12/16 · 400–600 | 12/16 | Legends, axis, meta, tags, stripe captions |

**English number format:** `29,670 pcs` · `95.7%` · `Rp 6.58B` · `Rp 486M` · `Rp 370K/min` · `06:12`. Deltas always name what they compare to ("8% vs target", "Rp 74M vs last week").

---

## 4. Layout & spacing

- **Spacing (4 grid):** 4 · 8 · 12 · 16 · 20 · 24 · 32. Card padding 16, gap between cards 12, page margin 32 (16 on mobile).
- **Radius:** 6 for tags, 8 for small controls, 9 / 11 for icon tiles, 10 for buttons, 12 for alert items / inputs, 14 for the insight panel, 16 for cards, 20 for dialogs.
- **Shadows:** cards `0 1px 2px` + `0 6px 16px` at 3.5–4%, always with a 1px border. Floating layers use `sh-3`.

**Desktop shell (≥ 1024 wide, ≥ 700 tall):** `100dvh` with no page scroll.

```
Top bar ............ logo · Fugodash Surya / for PT Sari Rasa Nusantara | [greeting · date · freshness] · refresh · bell(count)
Tab bar ............ [Overview | Production | Stock | Finance] ...... filters for this tab
View (fills rest) .. tab content; cards stretch, lists scroll inside
```

| Tab | Rows |
|---|---|
| Overview | Status strip · 4 KPI cards · *Revenue chart* (1.3fr) + *Needs attention* (1fr) + *Sari* (0.95fr) |
| Production | 3 product-line cards · *Output vs target* (stacked) + *Reject rate* (lines + limit) |
| Stock | 4 mini stats · *Materials & packaging* table + (*Finished goods* / *Reorder plan*) |
| Finance | 4 mini stats · *Daily revenue* chart + *Distributors* table · *Receivables* (full height) |

**Mobile:** normal scroll. The tab bar is sticky with 4 equal tabs, and filters scroll horizontally under it. KPI cards drop their legends. Sari becomes the floating button.

---

## 5. Icons

**Lucide** (ISC), stroke 1.6, sizes 18 / 16 / 14.

**Icon tile:** 32×32 (28 small, 40 large), radius 9, `tile` gray background, 1px `line` inset, icon in `text-2`. Status is carried by dots, bars and tags next to them.

**Highlight tile (`itile(name,'hl')`):** card headers, KPI cards and summary tiles show a custom colored duotone icon (22px) on its own, with no tile, border or shadow (`DUO` map in `index.html`). **Icon color:** duotone icons are blue by default on every tab. Only critical data is highlighted (`itile(name,'hl','crit')` → red): Materials at risk on Overview, the revenue drop tile on Finance. Stock's Critical / Watch tiles use their own red / orange icons because the tile *is* the state. Products, finance and headers otherwise stay blue. Summary tiles on every tab use the same frameless icon; status tiles (Critical / Watch on Stock) color it red / orange instead of blue. Status icons in lists stay neutral; the one exception is the "Business today" icon, which is tinted by state (green / orange / red) with a ping ring and a state motion: gentle bob (On track), sway (Watch), quick shake + faster ping (Critical). The sparkle icon is reserved for Sari / AI surfaces only; data cards (e.g. Reorder plan) use a data icon even when Sari produced the numbers. Sari's titles (side card, phone sheet, chat window) use the peanut avatar, whose face follows the current insight and which plays the idle loop. The AI sparkle (`aiBubble()`) marks Sari's content: the insight box and each chat answer, pulsing while Sari is working. The floating button keeps the peanut.

**Bar charts:** wide stacked bars (~78% of the slot), rounded top corners, 4px white gap between segments, no value labels on the bars. Totals, % of target and annotations live in the hover/tap tooltip; hovering a day dims the others.

| Use | Icon |
|---|---|
| Overview | `layout-grid` |
| Production | `factory` |
| Stock | `package` |
| Finance | `wallet` |
| Revenue | `trending-up` |
| Receivables | `receipt` |
| Charts | `chart-column` |
| Rejects | `gauge` |
| Distributors | `store` |
| Purchase orders | `truck` |
| Alerts | `bell` |
| Sari / insight | `sparkles` |
| Info | `info` |
| Export | `download` |
| Demo | `sliders-horizontal` |

---

## 6. Element patterns (from the reference)

| Pattern | Spec | Where |
|---|---|---|
| **Segmented bar** | 10px tall, 3px gaps, radius 4, one segment per category, plus a 2-column legend (swatch · name · value) | KPI cards, receivables aging |
| **Striped progress** | 12px track of 3px stripes / 2px gaps in `#E8E9ED`; the fill uses the same stripes in the status color; optional black limit marker | Needs attention, alert dialog |
| **Stacked bar chart** | Blue steps, rounded segments, dashed light grid, black dashed target with a pill label, red annotation pill for events | Revenue, output |
| **Tooltip card** | White card with a border and `sh-3`: date (600) then rows of swatch · name · value chip (blue / orange / neutral) | All charts, aging bar |
| **Limit band** | Pale red area above a red dashed limit line | Reject rate |
| **Target marker** | 2px black tick on a progress track | Line output, stock cover (3 and 7 days) |
| **Dot grid** | 1px Azure dots on a 12px grid, fading to the right | Sari insight panel only |
| **Segmented control** | White track, selected item in `accent-soft` / `accent-ink` | Tab filters |
| **Select** | 30px "Last 7 days ⌄" outlined | Chart period |
| **Switch** | 30×18, Azure when on | "Needs action only" |

---

## 7. Components

### 7.1 Status strip
- Neutral icon tile, then "Business today" (`cap`), then a dot and status word (`title`, status ink).
- One sentence with the count in bold.
- Three-step scale: On track · Watch · Critical.
- On sync error, an orange inline strip with [Try again].

### 7.2 KPI card
Contents, top to bottom:
1. Icon tile + label + period on the right (orange when stale).
2. Number (`fig`) + delta.
3. Segmented bar.
4. 2-column legend.

The whole card is a button to the matching tab.

| Card | Segments |
|---|---|
| Output | Chips / Peanuts / Macaroni |
| Revenue | Sumber / Maju Jaya / Berkah / Others |
| Overdue receivables | 30+ / 16–30 / 1–15 days |
| Materials at risk | Critical / Watch / OK |

### 7.3 Needs attention
- **Items:** bordered, radius 12. Each has a status dot, title, Rupiah impact on the right, striped bar, and a caption with what the bar means on the left and owner · time on the right.
- **Live alerts** get a red-tinted border.
- **Order:** most costly first.
- **Header:** count + [View all].
- **Footer:** "In progress (n)".
- Tapping an item opens the alert modal: details, then **Assign to …**, then due time, note and **Send task**.

### 7.4 Sari card (Overview, desktop)
- **Header:** AI sparkle, "Sari · AI assistant · reads factory data". No online/status pill: Sari is an AI assistant, not a help desk.
- **Insight panel:** `accent-soft` with the dot-grid pattern. Sari (70px) sits in the left corner, cut off by the bottom edge. Right of her: "✦ Insight for you" + 1/3 pager, then one sentence, then a primary small button. While thinking, three bouncing dots replace the text.
- **"Ask Sari" prompt cards:** a 2×2 grid, each card 48px tall with a neutral icon tile and a short question.
- **Footer:** "Continue: …" row and the input (text · mic · send).
- **Answer modal:** headline, stale warning, mini comparison bars, at most 3 reasons, "Based on" source chips (neutral; orange when stale; each opens its tab), actions, confidence meter, then "Follow up" chips and input.

### 7.5 Product-line card (Production)
- **Header:** product name + type · SKU · pack size, then status tag (Running / Stopped N min).
- **4-cell stat strip:** Today so far · Yesterday % · Downtime · Rejects (orange when over the limit).
- **Progress:** yesterday vs target, with a target tick.
- **Footer:** speed and finished-goods cover, or a red stop note with cause and loss.
- **Product filter:** non-selected lines dim to 40%.

### 7.6 Tables (Stock, Finance)
- **Sizing:** 13px cells, 12px sticky header on `raised`.
- **Highlight:** critical rows get a pale red background and a 3px red left bar.
- **Columns:** numbers right-aligned; inline cover tracks with 3- and 7-day ticks; status tags; small Order / Assign buttons.

### 7.7 Buttons
- **Variants:** primary (Azure gradient), secondary (white + outline), ghost, icon button (36).
- **Sizes:** 36 and 30.
- **States:** pressed scales to .96; focus is a 2px Azure ring.

---

## 8. Filters

| Where | Filter |
|---|---|
| Overview · Revenue chart | Select: Last 7 days / This month |
| Production | Product: All · Chips · Peanuts · Macaroni (dims cards, re-stacks the chart, fades lines) + Export |
| Stock | "Needs action only" switch + category: All · Raw materials · Packaging + Export |
| Finance | Period: Last 7 days / This month (stats, chart, table) + "From Sari" chip when opened from an answer + Export |

---

## 9. Illustration: Sari

Unchanged from v3: [assets/sari.svg](assets/sari.svg).

- **Character:** flat two-tone peanut (`#DE9A45` shade, `#F6C67E` base) with Azure AI sparkles by the head (they twinkle while thinking), a waving hand on hover, and 4 moods (idle, think, worry, happy). No headset.
- **Avatar:** head crop (viewBox `14 4 68 54`) in a 32px `accent-soft` square.
- **FAB:** 60px, radius 18, no status dot.

Sari is the only element on the screen with a warm illustration color.

---

## 10. Motion

- **Easing:** `cubic-bezier(.22,1,.36,1)`.
- **Durations:** 150ms for hover and press, 300–350ms for dialogs and sheets, 550–800ms for bars and stripes growing on first draw, a 35ms stagger on tab entry.
- **Re-renders:** the 30-second live refresh does not replay animations.
- **Loops:** only the live dot and Sari's typing dots.
- **Reduced motion:** `prefers-reduced-motion` turns everything off.

---

## 11. Copy

The interface is in English and addresses Pak Hendra as "you". It's short, about money and time, and has no exclamation marks.

| Write | Not |
|---|---|
| Line 2 stopped · 47 min | Downtime event L2 |
| ±Rp 17.3M | 17,300,000 IDR loss |
| Assign to Pak Budi | Create ticket |
| Finance data as of Nov 16, 17:00 · 1 day late | Sync lag detected |

---

## 12. Changes from v3

| v3 | v4 |
|---|---|
| Status icons in blue tiles | Neutral tiles for status icons; highlight tiles only for card-header icons |
| Laporan button opening a separate page | 4 tabs on the same page, filters in the tab bar |
| Desktop could scroll | Every tab fits one screen |
| KPI: number + single bar | Number + delta + segmented bar + 2-column legend |
| Alert list with Assign buttons | Compact items with a striped impact bar; assign inside the modal |
| Sari stage with a speech bubble + chip suggestions | Insight panel with a dot grid + 2×2 prompt cards, or an Online pill / headset (help-desk look) |
| Simple bars | Stacked blue bars by distributor or line, target pill, event annotation, tooltip card |
| Light detail tabs | Production: product, SKU, live output, rejects chart. Stock: supplier, lead time, PO, reorder plan. Finance: distributors, aging, overdue, upcoming |
| Bahasa Indonesia | English |
