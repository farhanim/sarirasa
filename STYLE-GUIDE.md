# Sari Rasa Control Room: Style Guide & UI Kit

Version 3.0 · 19 Nov 2026 · source of truth: [index.html](index.html) (CSS tokens at the top of the file)

v3 follows the WareHub reference:
- **Look:** calm Moonlit Gray page, white bordered cards, a soft blue icon tile on every card, and the Azure blue accent.
- **Type:** Inter Tight on a strict 6-size scale.
- **Density:** less information per card.

---

## 1. Principles

The user is Pak Hendra, 52, a factory owner who checks his phone at 06.30. He needs three answers in 30 seconds: *is the business OK, what needs me, is my money safe.*

1. **Calm first, color for meaning.** Neutral surfaces. Color appears only as status (green / orange / red), the blue primary action, and the mascot.
2. **One component pattern everywhere.** Every card starts with *icon tile + title*. If you learn one card, you can read all of them.
3. **Less per card.** A KPI tile shows a label, a number, one change and one bar. An alert shows a title, the Rupiah impact and the PIC. Everything else is one tap deeper.
4. **One page, no navigation to learn.** Beranda → tap anything → Laporan (3 tabs at most).
5. **Focus moments in a modal.** Alert details and assistant answers open in a modal on desktop and a bottom sheet on mobile.
6. **The assistant is a character.** Sari speaks first, in short bubbles.

---

## 2. Color

### 2.1 Brand (from the reference)

| Name | Token | Hex | Use |
|---|---|---|---|
| Midnight Velvet | `ink` / `text` | `#01040C` | Primary text, logo tile, toast, tooltip |
| Ivory Lace | `card` | `#FFFFFF` | Cards, modals, sheets |
| Moonlit Gray | `bg` | `#F5F5F5` | Page background |
| Azure Dream (light) | `accent-2` | `#609FFF` | Gradient start, mascot headset highlight, typing dots |
| Azure Dream | `accent` | `#2463EB` | Primary button, send, selected tab, chart bars on target |

### 2.2 Support neutrals & accent steps

| Token | Hex | Use |
|---|---|---|
| `raised` | `#F7F8FA` | Hover rows, impact boxes, progress track |
| `line` | `#ECECEE` | Card border, dividers |
| `line-2` | `#E1E2E6` | Control outlines (buttons, inputs, chips) |
| `text-2` | `#4F5562` | Secondary text |
| `text-3` | `#626875` | Meta: timestamps, axis labels |
| `accent-ink` | `#1A4FC9` | Accent text on `accent-soft` |
| `accent-soft` | `#EEF4FF` | Icon tiles, selected tab, assistant stage, source chips |
| `accent-line` | `#D7E5FF` | Icon tile and selected tab outline |

**Gradient:** only Azure on Azure, `#3573F0 → #2463EB` top to bottom, on primary buttons, the send button and the user's chat bubble. It's never used on surfaces or text.

### 2.3 Status: a traffic light that explains itself

| Status | mark (bars, dots) | soft (backgrounds) | ink (text) | Means |
|---|---|---|---|---|
| Aman | `#2FB86E` | `#EAF8F0` | `#15803D` | On target, running, more than 7 days of stock |
| Waspada | `#F07B3F` | `#FEF1E9` | `#B4471A` | 85–95% of target, 3–7 days of stock, overdue, stale data |
| Kritis | `#EF4444` | `#FDEDED` | `#B42318` | Line stopped, under 3 days of stock, 2 or more critical alerts |
| Ditangani | `#7C5CFC` | `#F2EFFF` | `#5B3FD9` | Assigned to a PIC or acknowledged |

The orange and purple come from the reference's category colors. In this app they always carry the same meaning. Status is always color + icon + word, never color alone.

### 2.4 Measured contrast (WCAG 2.2, 4.5:1 for text)

| Pair | Ratio |
|---|---|
| `text` on `bg` | 18.81 |
| `text-2` on `bg` | 6.86 |
| `text-3` on `card` / `bg` | 5.59 / 5.13 |
| White on `accent` | 5.17 |
| `accent-ink` on `accent-soft` | 6.33 |
| Waspada ink on soft | 4.92 |
| Aman ink on soft | 4.58 |
| Kritis ink on soft | 5.80 |
| Ditangani ink on soft | 5.88 |

---

## 3. Typography

**Typeface:** [Inter Tight](https://fonts.google.com/specimen/Inter+Tight) (Google Fonts, OFL). Weights 400 / 500 / 600. All figures use `tabular-nums`.

**Exactly 6 sizes:**

| Token | Desktop | Mobile | Weight | Use |
|---|---|---|---|---|
| `fig` | 28 / 34 | 22 / 28 | 500, −0.02em | KPI number |
| `h` | 20 / 28 | 18 / 26 | 500 (status word 600) | Page greeting, status word, dialog title, report figures |
| `title` | 16 / 24 | 16 / 24 | 500 | Card title, answer headline |
| `body` | 15 / 22 | 15 / 22 (inputs 16) | 400–500 | Default text, alert title, buttons, chat |
| `sm` | 13 / 18 | 13 / 18 | 400–500 | Sub-text, impact line, chips, delta, small buttons |
| `cap` | 12 / 16 | 12 / 16 | 500–600 | Tags, scale labels, chart axes, legends, "Dari data" |

Rules:
- No size outside this table and no inline `font-size`.
- Sentence case. No uppercase labels, no exclamation marks, no periods on labels or buttons.

**Numbers:** `29.670 pcs` · `95,7%` · `Rp 6,58 M` · `Rp 486 jt`. A change always says what it compares to ("8% vs target", "Rp 74 jt vs minggu lalu").

---

## 4. Spacing, radius, elevation, layout

**Spacing (4 grid):** 4 · 8 · 12 · 16 · 20 · 24 · 32. Inside a card the padding is 16 (14 on mobile). Gaps are 8 between items, 16 between cards (12 on mobile), and the page margin is 32 (16 on mobile).

| Radius | Use |
|---|---|
| 6 | Tag, count |
| 8 | Small button, source chip, tab item |
| 9 / 11 | Icon tile 32 / 40 |
| 10 | Button, input inner buttons, icon button |
| 12 | Alert item, input, segmented track, pic card |
| 14 | Assistant stage, speech bubble |
| 16 | Card |
| 20 | Modal, sheet, FAB |
| 999 | Suggestion chips |

| Elevation | Value | Use |
|---|---|---|
| `sh-1` | `0 1px 2px rgba(1,4,12,.04)` | Buttons, inputs |
| `sh-2` | `sh-1` + `0 6px 16px rgba(1,4,12,.04)` | Cards (always with a 1px `line` border) |
| `sh-3` | `0 24px 48px rgba(1,4,12,.14)` | Modal, sheet, FAB, floating bubble, toast, tile hover |

**Layout:**

| | Desktop ≥ 1024 | Mobile < 1024 |
|---|---|---|
| Container | max 1280, margin 32 | margin 16 |
| Beranda | Top bar · Status card · 4 KPI tiles · *Perlu tindakan* (1.7fr) + *Sari* (1fr) | Top bar · Status card · 2×2 tiles · *Perlu tindakan* · Sari FAB |
| Fit | The whole Beranda fits 1440×900 | Status + tiles fit 390×844 |
| Laporan | Sticky top bar: Back · title · 3-tab segmented control | Tabs go full width below the title |

Tap targets are at least 40 on desktop. On mobile the whole alert row is the target.

---

## 5. Icons

**Lucide** ([lucide.dev](https://lucide.dev), ISC). In Figma, use the community plugin "Lucide Icons". Stroke 1.6, round caps. Sizes are 18 by default, 16 in tiles and small buttons, and 14 in deltas and tags.

**Icon tile** (from the reference): 32×32, radius 9, `accent-soft` background, 1px `accent-line` inset, icon in `accent`. Status variants use that status's soft color and ink. The large version is 40×40, radius 11, used for the status card and empty states.

| Meaning | Lucide |
|---|---|
| Produksi | `factory` |
| Omzet | `trending-up` |
| Piutang | `receipt` |
| Stok | `package` |
| Distributor | `store` |
| Chart | `chart-column` |
| Alerts | `bell` |
| Kritis / Waspada / Aman | `octagon-alert` / `triangle-alert` / `circle-check` |
| Change up / down | `arrow-up` / `arrow-down` |
| Assign | `user-check` |
| WhatsApp | `message-circle` |
| Data source | `database` |
| Refresh / Laporan | `refresh-cw` / `clipboard-list` |
| Ask / voice | `send` / `mic` |
| Offline / fresh | `wifi-off` / `clock` |

---

## 6. Illustration: Sari

File: [assets/sari.svg](assets/sari.svg). Full body uses viewBox `10 4 78 92`; the head crop for avatars uses `14 4 68 54`.

**Concept:** a peanut (the company's Kacang Atom) wearing an Azure headset (the universal sign for "here to help"). It's named after the company, so it's easy to say "Sari, kenapa omzet turun?".

**Style:** flat two-tone with no outline stroke. A darker shell (`#DE9A45`) sits behind a lighter shell (`#F6C67E`) offset 1.5px up and left, which gives soft depth without a gradient.

| Part | Spec |
|---|---|
| Shell | 2 circles r24 (shade) + 2 circles r22.5 (base) |
| Texture | 4 short arcs `#E7AD5E` |
| Highlight | White ellipse, 50% opacity, top-left |
| Eyes | Ovals `#1B1206` with a 1.3px white catch-light |
| Cheeks | `#FF8A6B` at 45% |
| Hand | Small two-tone ellipse on the right; waves twice on hover |
| Headset | Band and ear cups `#2463EB`, inner pads `#609FFF`, mic boom to the mouth with an Azure-light tip |

**Moods** (only the eyes and mouth change):

| Mood | When |
|---|---|
| `idle` | Default |
| `think` | Eyes look up, small "o" mouth, while reading data |
| `worry` | Flat mouth, when the tip is about an alert or an error |
| `happy` | Closed-arc eyes, open smile, when there are no alerts |

**Where Sari lives:**

| Surface | Spec |
|---|---|
| Avatar | Head crop in a 32 or 40 `accent-soft` rounded square, used in card headers and chat |
| Stage (desktop card) | `accent-soft` panel, radius 14, soft Azure glow bottom-left; full-body Sari (72) peeks out from the bottom edge, with the speech bubble beside it |
| FAB (mobile and Laporan) | 64 rounded square (radius 20), head crop, green "online" dot top-right |

**Speech bubble:**
- White, radius 14 with a 4px corner toward Sari, a 12px rotated tail and `sh-2`.
- Header line: "**Sari**" in `accent-ink` plus a time in `cap`.
- Body: one sentence in `body`, then one small primary button.
- Paging: "1/3 ›" in the card header steps through tips.
- While Sari is thinking, the bubble shows **three bouncing Azure dots** instead of text.
- The floating bubble (mobile) is the same bubble at `sm` size with ×. It tucks away after 10 seconds.

**Don't:** sparkles, glows behind the character, looping idle animation, or using Sari as decoration where she isn't speaking.

---

## 7. Components

### 7.1 Card (base for everything)
- White, 1px `line` border, radius 16, `sh-2`.
- Header: icon tile 32 + title (`title`) + optional sub (`sm`) + right-hand action (info button 32, count, or chip).
- Body padding 16.

### 7.2 Top bar (Beranda)
- Left: logo tile (Midnight, 40, radius 10) + greeting (`h`) + date (`sm`).
- Right: freshness pill (40 tall, outlined; turns orange-soft when offline or failed) + icon button (refresh) + secondary button (Laporan).
- Mobile: greeting becomes "Pagi, Pak Hendra", the sub line shows freshness, and Laporan is icon-only.

### 7.3 Status card
- Desktop layout: icon tile 40 in status colors + "Kondisi bisnis hari ini" (`sm`) + status word (`h`, 600, status ink) | one sentence with the count in bold | **3-step scale**: Aman · Waspada · Kritis bars, 6px. The current step is filled with its color and its label is bold; the others stay gray.
- Sync error: an orange-soft strip inside the card with [Coba lagi].
- Mobile: everything stacks.

### 7.4 KPI tile
- Row 1: icon tile + label (`body` 500) + chevron.
- Row 2: number (`fig`) + delta (`sm`, status ink, arrow icon, then "vs …" muted).
- Row 3: progress bar, 8 tall, status color. The bar shows % of target, % of total, or days left out of 14.
- Nothing else. The whole tile is a button to the matching Laporan tab.

### 7.5 Alert item
- Bordered item (radius 12) in a list with 8px gaps. A live critical alert gets a red-tinted border and a pulsing dot.
- Contents: status icon tile + title (`body` 500) + "**impact in Rp** · PIC" (`sm`) + [Tugaskan] (small secondary button; a chevron on mobile).
- The card shows at most 3 items. Footer: "Lihat N lainnya" / "Sedang ditangani (N)".

### 7.6 Alert modal → assign
- **Step 1:** tags · title · 2 impact boxes · Penyebab · timeline · PIC card with [WhatsApp] · "Lihat data" link · ghost "Tandai sudah diketahui" · primary **Tugaskan ke [PIC]**.
- **Step 2:** PIC · deadline choices (1 jam / Hari ini 17.00 / Besok) · optional note · primary **Kirim tugas**.
- Sending, success (toast + Batalkan for 5s) and failure (note kept, "Coba kirim lagi") as in v2.

### 7.7 Assistant card and answer modal
- **Card:** avatar header ("Sari · Asisten Bapak" + 1/3 pager) · stage with bubble · "Lanjutkan: …" row · "Bapak bisa tanya" chips (short, pill shaped) · input (Tanya Sari… · mic · send).
- **Answer card:** white with a 1px border and radius 4/14/14/14. In order:
  1. "Sari" (`cap`, accent-ink)
  2. Headline (`title`)
  3. Stale warning
  4. Mini comparison bars
  5. At most 3 reasons
  6. "Dari data" source chips (accent-soft; orange-soft when stale)
  7. Actions
  8. Confidence meter (`cap`)
- The unsure variant has an orange border; the error variant uses Kritis soft.
- **Footer:** "Lanjut tanya" chips + input. The user's own bubble uses the Azure gradient with white text.

### 7.8 Laporan
- Back (secondary button) · title (`h`) · freshness (`sm`) · tabs: a white track with an outline; the selected tab is `accent-soft` with `accent-ink`.
- Rows: name (`body` 500) + one sub line (`sm`) / value + tag. Highlighted rows have a red-soft fade with a 3px red left bar.

### 7.9 Charts
- Bars only, one chart per tab.
- On target (≥ 95%) bars are Azure `#2463EB` with white values; below target they're orange `#F07B3F` with dark values.
- Target: Midnight dashed 1.5px. Grid: `line`. Axis: `cap` `text-3`. The annotation is a red dotted line with a label. The legend is always shown.

### 7.10 Buttons and small parts

| Variant | Style |
|---|---|
| Primary | Azure gradient, white, inner highlight |
| Secondary | White, `line-2` outline, `sh-1` |
| Ghost | Text only, `text-2` |
| Icon button | 40 square, secondary style |

- Sizes are 40 and 32. Pressed scales to .96, focus is a 2px Azure ring, disabled is 55% opacity, loading shows a spinner + verb.
- **Tag:** `cap` 500, radius 6, soft background + ink.
- **Count:** 22px square, radius 6.
- **Delta:** `sm` 500, status ink, 14px arrow.
- **Toast:** Midnight, radius 12, white text, action in Azure-light.
- **Skeleton:** `raised` shimmer.

---

## 8. Motion

One easing curve, `cubic-bezier(.22,1,.36,1)`. Durations: 150ms for hover and press, 300–350ms for the modal and sheet, 600–700ms for bars growing on first draw, 1s per cycle for the typing dots (shown only while thinking). Sari's hand waves only on hover. The only always-on loop is the live dot on a stopped line. `prefers-reduced-motion` turns all of these off.

---

## 9. Copy voice

Polite and short, addressing "Bapak". Talk in money and time.

| Write | Not |
|---|---|
| Lini 2 berhenti 47 menit · ±Rp 17,3 jt | Downtime event L2 |
| Tugaskan | Assign ticket |
| 8% vs target | −8.0% delta |
| Data Finance per 16 Nov 17.00, terlambat 1 hari | Sync lag |

---

## 10. Libraries & Figma setup

| Need | Resource |
|---|---|
| Font | Inter Tight (Google Fonts, OFL) |
| Icons | Lucide (ISC), Figma plugin "Lucide Icons" |
| Mascot | `assets/sari.svg`, original to this project |
| Mobile frame | Apple iOS UI Kit (status bar and home indicator only) |
| Flows | FigJam flow kit |

**Figma variables:**
- `Color/Brand`: ink, bg, card, accent-2, accent
- `Color/Neutral`: raised, line, line-2, text-2, text-3
- `Color/Status`: a collection with modes Aman, Waspada, Kritis and Ditangani, each holding mark, soft and ink. Components then switch status with one mode change.
- `Type`: the 6 styles from §3

**Pages:**
1. Cover
2. Foundations
3. Sari (4 moods, 3 surfaces)
4. Components (§7, all states)
5. Screens (Beranda D/M, modals and sheets, Laporan × 3, States)
6. Flows

---

## 11. Changes from v2

| v2 | v3 | Why |
|---|---|---|
| Full-width colored status band | White status card + 3-step Aman/Waspada/Kritis scale | Calmer; the scale explains what the color means |
| Plus Jakarta Sans, 11 sizes | Inter Tight, exactly 6 sizes | Matches the reference; one consistent rhythm |
| KPI tile: label, figure, comparison, tag, freshness | Label, figure, delta, progress bar | Less to read; the bar shows "how far from target" at a glance |
| Alert row: tag, title, impact, context, PIC line | Title, Rp impact, PIC | Less per item |
| Amber / blue `#2453D6` | Orange `#F07B3F` / Azure `#2463EB`, as in the reference | Follows the reference design system |
| Peanut with outline | Flat two-tone peanut with a waving hand, a "stage" panel, and a typing bubble | More modern and friendlier |
