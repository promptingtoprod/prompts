# Part 2: six upgrades, one prompt each

The follow-up prompts from the second portfolio tracker video, full wording. They assume you already
have a tracker built from [START-PROMPT.txt](START-PROMPT.txt) (the first video). Type them into Claude Code
in the project folder, one at a time, and read what it changes before you type the next one.

**Video:** https://youtu.be/cqnQB44GUBA · **Part 1:** https://youtu.be/uKDLMBc0F9M

**One rule for every change:** no buy or sell advice anywhere, report numbers and my own levels only,
keep everything on my computer, no accounts linked.

**Your version will look different from mine**, and each page took a few follow-up prompts after the
first one. These are the asks that started each page, not a recipe for an identical screen.

## The six prompts in the video

### 1. Dashboard: what drove today's move (video at 0:53)

```
Show me which holding moved my money the most today, in dollars.
```

### 2. Charts on every holding, watchlist groups (video at 1:47)

```
Give every holding a small chart in its row, and a full chart when I click it, with a row of buttons from one day up to everything you have. Put the same buttons on the watchlist, and let me split the watchlist into groups.
```

### 3. Alerts as a ladder of my own levels, plus the Dashboard tile (video at 2:09)

```
For each stock, show my own price levels as a ladder: the next ones below today's price, the next ones above, and how far away each is. Keep the levels in a small file next to the holdings, and keep the dates a level was hit. On the Dashboard page, add a tile with the nearest level below and above for every stock, and how far the price is from each, with no buy or sell wording.
```

### 4. Goals page (video at 2:44)

```
Add a goals page. For each target, show how far along I am under three growth guesses: a bad year, a normal one, a good one, using growth rates I type in and my planned monthly contribution. For the biggest target, draw the path it needed to follow from the day I set it, the value I have, and where I land from here at my normal-year guess plus the monthly contribution.
```

### 5. Formulas page (video at 3:39)

```
Run the common formulas investors use to size up a company on each holding, in one table: Graham number, PEG, Magic Formula, Piotroski, Altman Z, a simple discounted cash flow I can adjust, Rule of 40, CAN SLIM. Under the table, add a legend that says who wrote each one, how to read it, and where it misleads. If a figure is missing for a stock, show a blank and say so, never estimate it.
```

### 6. Corrections in plain words, cash by account (video at 4:16)

```
When I buy, sell, or add cash after the last export, let me tell you in plain words instead of exporting again. Keep those corrections in a small file next to the holdings, apply them on top of the export, and show the uninvested cash in each account.
```

## Also added, not shown in the video

### 7. This year's close-up on the Goals page

```
On the goals page, add a chart for the current year only: the goal for this year, what the portfolio has actually done since the day I set it, and the pace it needs from here.
```

### 8. Never lose the history file again

```
Every time you save the history or any data file, write to a temporary file first and then swap it in, keep a backup copy, and if a file turns out corrupt on startup, recover from the backup and tell me.
```

### 9. The adjustable valuation inputs

```
On the formulas page, let me change the discount rate, the growth cap and the terminal growth in the page itself, and recalculate the cash-flow estimate without a reload.
```

### 10. A fairer history chart

```
When comparing my holdings to a benchmark, start both lines on the same day and hold a holding flat at its first known price before it existed, and say on the chart that this is a backtest, not a record of trades.
```

### 11. The AI Money Trail page

Its prompt is long and has its own data file, so it lives in its own repo:
https://github.com/promptingtoprod/ai-money-trail. Answer "a tab in my project" to its first question to get it
as a page inside the tracker.

## Left out on purpose

A market mood gauge, a 0 to 100 stock rating and a buy or sell card exist in my copy. They read as advice,
so they are hidden in the version shown and there is no prompt for them here.

## Please read

Not financial advice. The tracker reports numbers and makes no recommendations. Everything in the video is
sample data: two made-up people, made-up money, live prices. The sample portfolio was picked with hindsight,
and the benchmark line is a backtest on today's holdings, not a record of past trades. I own some of the
tickers shown. Prices come from a free source and can be delayed or wrong; your broker is the system of record.

Free and as-is, with no warranty. These are text instructions, not software: your own AI tool builds the
result on your own computer, and you are responsible for reviewing what it builds and for any decisions you
make with it. Requires Claude Code on a paid Claude plan.
