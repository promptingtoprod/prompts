# TRACKER-DESIGN.md — the look of the tracker from the video

> OPTIONAL. Save this next to the starting prompt and Claude follows it. It's the
> LOOK, not the features — build only the tabs you have so far.

## Colours

Define these once as CSS variables on `:root`; never hardcode a hex below that.

| `--bg` | `#0A0D13` | page |
| `--surface` | `#141A23` | cards, panels |
| `--surface-2` | `#1A2029` | row hover |
| `--border` | `#242C38` | card borders |
| `--divider` | `#1B222C` | table rules |
| `--text` | `#E8EDF4` | primary text |
| `--muted` | `#9AA7B5` | secondary |
| `--faint` | `#6E7B8A` | column labels, timestamps |
| `--accent` | `#2F7BF6` | active tab, chips, focus |
| `--pos` | `#3FD07A` | gains |
| `--neg` | `#FF5F56` | losses |
| `--warn` | `#E3B341` | stale-data badges |

Radii 6/10/14px. Shadow `0 1px 2px rgba(0,0,0,.4), 0 4px 16px rgba(0,0,0,.22)`.

## The five rules that matter

1. **System fonts only.** No web fonts ever — the privacy rules forbid the page
   loading anything external, and a Google Fonts link breaks that on every view.
2. **Tabular numerals** (`font-variant-numeric: tabular-nums`). Every figure sits in
   a column with other figures; proportional digits make columns ragged. This one
   line does more for how finished it looks than any colour choice.
3. **Say what the number is, not what finance calls it.** These started as "Total
   value / Total cost / Total profit" — "total cost" reads as *fees* to anyone
   outside finance when it means the book cost of the shares. They became "Worth
   today / What you paid / Profit". If a label needs a sentence of explanation out
   loud, rename it.
4. **Colour only for gains and losses.** Emphasise with weight (600), never hue.
   No gradients, no glows, no stock images. Emoji only as tab icons.
5. **Nothing below 12px, anywhere.**

Labels (table headers, strip captions) are uppercase 12px `--faint`, letter-spacing
.05em. Values carry the weight, not the captions.

## Global chrome (every tab)

Header: title left; status chips right — live/offline toggle, an FX chip if you hold
more than one currency, a `127.0.0.1 only` chip. Under it: "Updated <time> · <file>"
plus an amber badge when the holdings file is stale ("Holdings as of <date> · N days
ago"). Then the totals strip: Worth today · What you paid · Profit ($ and %), plus
per-owner totals. Controls: refresh button, after-hours toggle, quotes refreshing in
place every 60s with no page reload. Last open tab and filters survive a refresh.

## Tab bar — this order, these icons

📊 Dashboard · ☰ List · ▦ Cards · 🏦 Accounts · ★ Watchlist · 🔔 Alerts ·
📅 Catalysts · 🎯 Health · 🔬 Analytics · 🎮 Strategy Lab · ⚠️ Laggards · 🏁 Goals

Active tab: `--text` with an `--accent` underline. Inactive: `--muted`. All twelve
stay on ONE line — a wrapped tab bar reads as a bug.

## Tab layouts, top to bottom

- **Dashboard** — hero stat row (worth today · made since start · today's move ·
  profit · positions) → you-vs-benchmark table (1M/3M/6M/1Y) → net-worth chart →
  made/lost range chips → two panels side by side: today's movers (by %) and what's
  driving today's move (by DOLLAR impact, with share-of-move bars) → three donuts
  (asset class, account, top holdings) → **"What this can't do"**: the honest-limits
  panel the prompt requires, full width at the bottom, two columns, muted text.
- **List** — search + owner chips + type chips → dense sortable table (sparkline,
  price, day %, shares, avg cost, value, % of portfolio, profit) → expandable rows
  showing per-account lots → total footer.
- **Cards** — same filters, one card per holding, big sparkline.
- **Accounts** — collapsible card per account (owner · type · value · return) with
  its own holdings table; expand-all / collapse-all.
- **Watchlist** — add-ticker bar with a group field; collapsible groups; sparkline,
  price, day change, remove.
- **Alerts** — add form (symbol · rises-to/falls-to · target) → rules table with live
  price and waiting/hit status.
- **Catalysts** — one calm line ("a schedule, not a prediction") → events table:
  date · what · detail · typical impact in plain English.
- **Health** — disclaimer header ("analysis and considerations, not directives") →
  concentration risk, sheltered vs taxable, biggest contributors, underwater,
  optional savings-target progress.
- **Analytics** — one attention card per flagged holding: the reason, a plain-English
  remark, a few real headlines. Friendly empty state when nothing is flagged.
- **Strategy Lab** — honesty blurb naming the written rule file → virtual-cash input
  → paper value, chart, positions with reasons, trade log, reset.
- **Laggards** — framing note (sorted by DOLLARS held, a deliberate counter to
  anchoring) → count, value held, combined loss → table with sector and % of
  52-week high.
- **Goals** — milestone projections from your own bear/base/bull return bands plus a
  monthly contribution, the contribution the base case needs, and progress against a
  yearly growth goal. Every figure is your assumption, not a forecast — say so on
  the tab.

## Interactions

Any symbol or sparkline opens a chart modal: range chips (1D…Max), a compare
dropdown (portfolio / accounts / benchmarks / any ticker), multi-series legend,
stats. Tables sort on header click. Filters recompute instantly. Every empty state
is a plain sentence, never a blank box. Footnotes under tables in small muted text,
plain English.
