# FEATURE-MENU.md — the asks my tracker grew through

> Copy any line into Claude Code inside your tracker's folder. One or two at a time,
> review each change before the next. You don't need most of these — pick what
> answers YOUR morning question.
>
> ⏳ needs a few days of saved history before it shows anything.
> 🌐 pulls extra public data (still only ticker symbols leave your computer).

**Two privacy things worth knowing before you add the 🌐 ones.** The features that
need sector, earnings dates, analyst ratings or headlines require a cookie handshake
with a second host (`fc.yahoo.com`) — the provider returns 401 without one. That host
is contacted once per run and receives **no parameters at all**; the cookie lives in
memory and is never written to disk. Its real cost is that requests within a session
become linkable. `--no-extras` skips the handshake and disables exactly those
features; everything else still works. Second: **the watchlist sends its tickers out
too**, so it reveals what you're *considering*, not only what you own.

Adding a watchlist ticker or an alert means the dashboard writes — to its own JSON
files only, never your holdings file.

## Dashboard

- "Show one big number at the top: what I made or lost today, in dollars, green or
  red, with the percent and my total underneath."
- "Add a panel ranking what's driving today's move by dollar impact — shares times
  today's price change — with a bar showing each holding's share of the move.
  Percent alone misleads: a small position with a big percent barely moves me."
- "Add a today's-movers panel: gainers and losers side by side, by percent."
- "Save my total value once a day to a local file and chart it over time." ⏳
- "Add made-or-lost chips: 1 week, 1 month, 6 months, year to date, 1 year, max."
- "Add three donuts: my money by asset class, by account, and my top holdings."
- "Compare my portfolio against an all-in-one ETF and the S&P 500 over 1, 3, 6 and 12
  months — and be honest in a footnote about how the comparison is computed." 🌐
- "If any holding moves more today than its own typical daily move, show a banner
  with what's typical for it." 🌐

**Be aware of the backtest.** The comparison table and the made/lost chips price
*today's* share counts backwards through history. They assume you held your current
mix the whole time and ignore every trade, deposit, withdrawal and dividend. All the
lines compute the same way, so comparing them is fair — but none of them is your real
past. The net-worth chart is the opposite: real saved values, one point per day.

## List & Cards

- "Add a List tab: one dense sortable row per holding — sparkline, live price, day
  change, shares, average cost, value, percent of portfolio, profit."
- "Let me filter by owner and by type (stocks, ETFs, crypto) with instant chips, and
  a search box. Remember my filters between refreshes."
- "Make each row expandable to show which accounts hold it."
- "Add a Cards tab: the same holdings as visual cards with a big sparkline."
- "Show each holding's analyst rating as a small badge, cached once a day." 🌐
  *Third-party opinions, not findings.*

## Accounts

- "Add an Accounts tab: one collapsible card per account, grouped by owner, with its
  own value, return and holdings table. Expand-all and collapse-all."
- "Let me compare any single account against the others or a benchmark on a chart." ⏳

## Watchlist & Alerts

- "Add a watchlist where I can add any ticker into named groups, saved to a local
  file."
- "Add price alerts: symbol, rises-to or falls-to, target. Show waiting or hit, and
  pop a browser notification when one fires while the page is open."
  *Only while the page is open — this is not a notification service.*

## Catalysts

- "Add a Catalysts tab listing my holdings' upcoming earnings dates for the next two
  months, with a plain note that this is a schedule, not a prediction." 🌐
  *Earnings dates are often estimates that move.*
- "Make the big scheduled economic releases a local file I edit myself, shown in the
  same table and labelled as mine."
  *There's no free reliable feed for these — inventing dates and showing them as
  fact would be worse than leaving them out.*

## Health

- "Add a Health tab that analyses without advising — say so at the top. Include my
  concentration risk (top 1, 3, 5 holdings as a percent), my sheltered versus taxable
  split, my biggest dollar contributors, and my underwater positions."
  *A description of where your money sits. It computes no tax and is not tax advice.*
- "Add an optional savings-target input and show my progress toward it."
  *Pure arithmetic against today's value — no assumed return, no projection.*

## Analytics

- "Add an Analytics tab flagging which holdings deserve a look today — an unusual
  move, earnings coming up, weak analyst consensus — each with a plain-English
  sentence saying why, and a few recent headlines with links." 🌐
  *Unusual-move detection works without the handshake; the rest needs it. Headlines
  are ordinary links out; nothing about your portfolio goes with them.*

## Strategy Lab

- "Add a paper-trading tab: I give it virtual cash, it follows a written rule file I
  can read, rebalances once a day, charts its value, and keeps a trade log. Real
  prices, fake money, and it must say plainly that it can lose." ⏳ 🌐
  *Keep the rule simple enough to check yourself, and give every trade in the log its
  reason.*

## Laggards

- "Add a Laggards tab: everything I'm down on, sorted by the dollars still held in it
  — not by percent lost — with how far each sits below its 52-week high." 🌐

## Goals

- "Add a Goals tab: let me enter my own bear, base and bull annual-return bands and a
  monthly contribution, then show when I'd reach a milestone under each, the
  contribution the base case needs, and my progress against a yearly growth goal.
  Label every figure as my assumption, not a forecast." ⏳

## Anywhere

- "Clicking any symbol opens a chart with ranges from one day to max, and lets me
  overlay any other holding, account or benchmark."
  *Rebase lines to 0% at the window start so shapes compare. Price change only —
  dividends not included.*
- "Show pre-market and after-hours prices behind a toggle, marked clearly."
  *Outside extended hours the provider returns nothing and it falls back to the
  regular close — so the toggle can legitimately look like it did nothing.*
- "Write every empty state as a plain sentence saying what will appear there and
  when."
