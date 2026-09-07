# START HERE

You are going to build a **personal portfolio dashboard** that runs on your own
computer. The finished tracker needs no accounts and no signup, and the only data it
ever sends out is ticker symbols. You will not write the code yourself: you will
describe what you want, answer some questions, and check the result.

One thing to know up front: Claude Code is an online service, and while it builds it
reads what is in this folder and what you type. That is why the kit ships a **fake
portfolio** — everything in here is invented, so there is nothing sensitive to read,
and everyone in the room ends up looking at the same numbers.

---

## What you need

| | |
|---|---|
| **Python 3.10 or newer** | Check with `python --version`. The reference build uses only what ships with Python — if Claude asks to `pip install` something, tell it to stick to the standard library. |
| **Claude Code** | The tool that will write the code from your instructions. Needs a Claude account on a paid plan (not the free tier). |
| **About 20–30 minutes** | Longer if you add the optional features. |

---

## The four steps

### 1. Put these files in a folder of their own

Copy everything from this kit into an empty folder, and open a terminal there. Keep
`demo-holdings-2026-08-10_ALEX.csv` with them — that is the fake portfolio the tracker
will read.

### 2. Start Claude Code in that folder and paste this

```
Read START-PROMPT.txt and build it. Follow TRACKER-DESIGN.md exactly for the look.
Then read FEATURE-MENU.md and build all of it.
```

That last sentence matters. Without it you get the basic version — about half the
tabs. `FEATURE-MENU.md` is where Cards, Catalysts, Health, Analytics and the Strategy
Lab come from.

### 3. Answer the interview

It will stop and ask you questions before writing any code — which currency, which
benchmark, what the big number at the top should be. **Answer them for the demo data:**

| Question | Answer to give |
|---|---|
| Watchlist only, or holdings file? | Holdings file — it is already in the folder |
| Which broker? | Wealthsimple-style export (already provided) |
| Reporting currency and FX? | CAD totals, live FX rate |
| Joint accounts? | Split the joint RESP 50/50 between the two owners |
| Anything without a ticker? | No — the CSV is everything |
| The one question each morning? | What did I make or lose today |
| Tracking to a target? | Just watching performance |
| Benchmark? | S&P 500 via VFV.TO |
| Alerts? | All of them |
| Screen sharing / demo mode? | No |
| Refresh rate? | Every 60 seconds |
| One file or a package? | Single file |

Give different answers if you like — the dashboard will be different, and that is
fine. But if you want your screen to match the person next to you, use these.

### 4. Run it and check your work

```bash
python tracker.py
```

Your browser opens at `http://127.0.0.1:8787`.

---

## Did it work? Check these

### Must match, for everyone

These come straight from the CSV. If any of them is wrong, something is wrong:

| | |
|---|---|
| **Total cost** | **$42,215.00** |
| **Positions** | **9**, across **5** accounts |
| **Owners** | **ALEX** and one co-owner (the RESP is joint) |
| **Accounts** | TFSA, RRSP, Crypto, Non-Registered, Family RESP |
| **Underwater** | TSLA is below what it cost |

### Should match, if you run it offline

```bash
python tracker.py --offline
```

Offline uses the prices stored in the CSV instead of fetching live ones, so it gives
the same answer on every machine, every day:

| | |
|---|---|
| **Total value** | **$46,703.00** |
| **Total profit** | **+$4,488.00 (+10.63%)** |
| **FX rate** | **1.3800**, labelled `csv-implied` |
| **Today's move** | not shown — offline has no "yesterday" to compare to |

If your live numbers differ from your neighbour's, that is **correct**. Live prices
move every few seconds. Compare offline numbers, not live ones.

### Three things that are supposed to look empty

Do not treat these as bugs:

1. **Net worth over time** — nearly empty. It saves one dot per day you run it, so on
   day one there is one dot. It cannot show a past it never watched.
2. **"Made since first run"** — says it needs two days. Same reason.
3. **An amber badge saying "Holdings as of 2026-08-10 · N days ago"** — that is the
   point, not a flaw. See below.

---

## The bit that actually matters

Two lessons are built into this thing on purpose.

**It does not auto-sync.** The CSV is a snapshot from a date in the past. If you bought
or sold since, the tracker has no idea — it will confidently show you the old
holdings at today's prices. That amber badge exists to keep reminding you. This is the
most common way a tool like this misleads someone.

**Know exactly what goes out.** Not "it's private" — the actual list. Open the 🔒
**Limits** tab once it is running, and read the *Network calls* section of
`TRACKER.md`. Both spell out every outbound request, what parameters go with it, and
what a price provider can still infer from it. Then judge it yourself.

Read section 1 of `START-PROMPT.txt`. Those rules are the real assignment:

- Outbound calls are restricted to price lookups, carrying ticker symbols only.
- All network calls live in exactly **two** functions, so the whole outbound surface
  can be checked by reading two pieces of code.
- The server binds to `127.0.0.1`, so nobody else on the wifi can reach it.
- The page loads no fonts, no scripts, no images from anywhere.
- `--offline` makes zero network calls at all.

Check it yourself once it is running:

```bash
netstat -ano | findstr 8787
```

You should see `127.0.0.1:8787` and never `0.0.0.0`. Then try opening it from your
phone on the same wifi — it will fail, and that is the correct answer.

**Open the 🔒 Limits tab and read it.** It is the honest list of what these numbers are
and are not — not advice, not tax software, prices delayed, your broker is the real
record.

---

## If you get stuck

| Problem | Try |
|---|---|
| `python: command not found` | Try `py` instead, or install Python 3.10+. |
| Port already in use | `python tracker.py --port 8788` |
| Prices all show "CSV price" or "stale" | The free price source is unofficial and does break. Use `--offline` — everything still works. |
| Sector / earnings / analyst badges missing | Those need an extra handshake with the price provider and are the most fragile part. `--no-extras` turns them off deliberately. |
| Numbers do not match the table above | Compare **offline** numbers. Live prices always differ. |
| It asks to put your real portfolio in | Don't. Use the demo CSV for class. |

---

## Using your own portfolio afterwards

You can, and the tracker is built for it — but **read `SHARING.md` first**. The moment
you drop in a real export, this folder stops being safe to share, and you need to
delete every `!` line in `.gitignore`. Never email the file to yourself or paste it
into a chat window.

---

## What is in this kit

| File | What it is |
|---|---|
| `START-HERE.md` | This page. |
| `START-PROMPT.txt` | The brief. Claude Code reads this — it is the assignment. |
| `TRACKER-DESIGN.md` | Exactly how it should look: colours, layout, tab order. |
| `FEATURE-MENU.md` | The optional features, in plain English. |
| `demo-holdings-2026-08-10_ALEX.csv` | The fake portfolio. Fictional people, `DEMO-` account numbers. |
| `TRACKER.md` | What the finished tracker does, and precisely what leaves your machine. |
| `SHARING.md` | What reproduces, what doesn't, and how to pass this on. |
| `.gitignore` | Keeps real financial data out of git, if you ever use it. |
| `reference/` | A finished version, plus a note on the one rule it deliberately breaks. **Try not to open it until yours works.** |
