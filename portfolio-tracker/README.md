# Portfolio tracker

Build a portfolio dashboard that runs on your own computer. It reads a CSV export from
your broker and shows what you hold, what it is worth, and what moved today. No linking
your brokerage accounts, no subscription, no data leaving your machine beyond the ticker
symbols it looks prices up for.

You will not write the code. You describe what you want, answer some questions, and check
the result.

**Video:** *link on publish*

## What you need

| | |
|---|---|
| Python 3.10 or newer | Check with `python --version` |
| Claude Code | Or another capable AI coding assistant. Needs a paid Claude plan. |
| 20–30 minutes | Longer if you add the optional features |

## Start

1. Download this folder (green **Code** button at the top of the repository → **Download ZIP**) and put the files in an empty folder of their own.
2. Open **[START-HERE.md](START-HERE.md)** and follow it.

That file has the four steps, the answers to give during the interview, and a table of
numbers to check your build against.

## What is in here

| File | What it is |
|---|---|
| [START-HERE.md](START-HERE.md) | Read first. The four steps and how to check your work. |
| [START-PROMPT.txt](START-PROMPT.txt) | The brief. Claude Code reads this — it is the assignment. |
| [TRACKER-DESIGN.md](TRACKER-DESIGN.md) | How it should look: colours, layout, tab order. Optional. |
| [FEATURE-MENU.md](FEATURE-MENU.md) | The optional features in plain English, one ask at a time. |
| [demo-holdings-2026-08-10_ALEX.csv](demo-holdings-2026-08-10_ALEX.csv) | A fake portfolio to build against. |

## About the demo portfolio

The CSV is invented. The people are made up, every account number starts with `DEMO-`,
and the holdings belong to nobody. Build against it first — everyone following the video
sees the same numbers, which is what makes the check-your-work table work.

When you switch to your own broker export, that folder stops being safe to share. Keep it
off GitHub, out of email, and out of chat windows.

## What this cannot do

It does not connect to your broker and it does not auto-sync. The CSV is a snapshot from
the day you exported it. Buy or sell after that and the tracker will show you the old
holdings at today's prices, confidently and wrongly. It carries a badge reminding you how
old the file is.

Prices are delayed and come from a free, unofficial source that does break. Your broker
remains the record of what you actually own.

## Terms

Free and as-is, no warranty. Not financial, tax, or legal advice. You are responsible for
reviewing what your AI tool builds and for any decisions you make with it.
