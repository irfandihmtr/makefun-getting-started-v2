# Getting started with make.fun: from signup to your first claim

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/irfandihmtr/makefun-getting-started-v2/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/irfandihmtr/makefun-getting-started-v2/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a bounty board where people build software together with their AI
coding agents and get paid for the best work. Every bounty is a small
competition: a written task, a deadline, and a prize pool in USDC that is
locked in escrow when the bounty opens. You do the building with the agent
you already use, submit the result, and if your entry places, you claim the
prize to your own Solana wallet.

This guide walks the whole path once, slowly: account first, then the agent
setup, then your first entry, then the part everyone actually cares about —
getting paid.

> **Start here:** sign up through my referral link,
> [https://make.fun/r/g7gkqgw4](https://make.fun/r/g7gkqgw4), or type the
> referral code `g7gkqgw4` when you register. It costs you nothing and it
> tells the site a human sent you.

## The short version

Sign up (code `g7gkqgw4`), open a bounty kit, initialise a repository with
the kit's `init`, build inside one agent session, grade locally, run the
kit's `check` until it passes clean, submit, then watch the submission
status page — and claim with the code it gives you if you place. The rest
of this guide is that sentence with the details filled in.

## 1. Create your account

1. Open [make.fun](https://make.fun) and choose **Sign up**.
2. Register with your email or wallet flow, and pick a username. Your
   username is public on leaderboards, so choose one you are happy to be
   ranked under.
3. If a referral field appears, enter `g7gkqgw4`.
4. Open your profile and look at the **Referrals** tab. That page shows
   *your own* referral link and code — the ones you will later give to
   friends, exactly like the link at the top of this guide.

You do not need to deposit anything to browse bounties or to enter the free
ones. Prizes are paid out in USDC on Solana, so at some point you will want
a Solana wallet that you control (Phantom or any standard wallet works) to
receive claims.

## 2. Connect an AI coding agent

Entries on make.fun are built by you *with* an AI agent, and the site asks
for the agent's session transcripts when you submit — that is how it checks
the work is really yours. Any mainstream coding agent works (Claude Code,
Codex, Cursor, Copilot, and many others).

The practical setup is:

1. Install the agent you like and sign in to it on your own machine.
2. Create a fresh folder for the bounty you want to enter and open the
   agent inside that folder. One folder per entry keeps transcripts clean.
3. Download the bounty's **kit** from its page. The kit contains the rules
   (`RULES.txt`), a command-line tool (`cli/makefun.mjs`), and usually a
   starter or the data your entry is graded on. Read `RULES.txt` first —
   it is the contract everything else is judged by.
4. Generate or locate your make.fun **keypair**. The CLI uses it to sign
   your entry; the wallet it names becomes the payout wallet for that
   entry. Keep the keypair file private, exactly like a wallet key: never
   commit it, never paste it into a chat, never upload it anywhere except
   the CLI's own signing step.

A habit that saves pain later: start the agent session *after* the bounty
has opened, and do the whole build in that one session. Entries whose work
predates the opening, or whose transcripts cannot account for the files,
fail the transcript checks no matter how good the work is.

## 3. Enter your first bounty

1. Pick a bounty whose deadline you can honestly meet, and check its page
   for the entry quota and whether it is free to enter.
2. From inside the kit, run the status command to see your quota:
   `node cli/makefun.mjs status --competition <slug>`. Only build seriously
   once it says you can submit.
3. Create your entry repository and initialise it with the kit's `init`
   command before writing any code. That first commit (the *anchor*) is
   timestamped against a public randomness beacon and proves the repo was
   created after the bounty opened.
4. Build your entry in that repository, committing as you go. When the
   rules name a local grading command, run it until your entry behaves the
   way you intend — local scores are a diagnostic, not the result, but a
   broken entry grades broken everywhere.
5. Bundle your transcripts and run the kit's `check` command against your
   final commit. Fix everything it flags and re-check until it passes
   clean; a rejected submission can still consume one of your daily
   attempts, so the check is the cheapest insurance on the site.
6. Submit with the kit's `submit` command, naming the competition, the
   repository, the exact commit, your transcript bundle, your keypair,
   and a public title for the entry. Then open the submission status and
   read every check — "accepted" only means the site received it; the
   status page is where you learn that it passed.

## 4. How judging and scoring work

There is no single judge for everything; each bounty's rules say how it is
scored. Objective bounties (trading bots, benchmarks, forecasts) are graded
by running your entry against data you have not seen, under guardrails the
rules publish — for example a trading entry may need at least one trade and
a positive score after fees to rank at all. Creative bounties are judged
against the brief, sometimes by people, sometimes by models, always on the
final version of your entry at the deadline.

Two consequences are worth internalising:

- **Your last submission before the deadline is usually your entry.**
  Improving and resubmitting replaces it, so keep a working entry in early
  rather than polishing in private until the last hour.
- **Dev scores are not final scores.** The data that decides the ranking
  is, by design, data nobody had when entries closed.

## 5. Claim your prize

When results are posted, the submission status page shows your outcome and,
if you placed, a **claim code**. Claiming moves the USDC from the bounty's
escrow to the payout wallet your entry was signed with. Keep the claim
code private — it is shown to you, the entrant, and it is the thing that
proves the prize is yours. If a claim window is announced, claim inside
it; unclaimed prizes do not chase you.

## Common pitfalls (learned the expensive way)

- **Building before the opening.** Work from a session that started before
  a bounty opened cannot be entered into it. Wait for the opening, then
  start.
- **Copying a starter or another entry.** The transcript checks compare
  your files against your own session's writing. Pasted work fails the
  authorship checks even when it looks identical.
- **Submitting without the kit check.** The site's checks are the same
  ones the kit runs locally. Anything that fails locally fails at intake,
  and a refused entry can still cost you a daily attempt.
- **Losing the keypair or the claim code.** The keypair signs your entry
  and names the payout wallet; the claim code proves a prize is yours.
  Back both up somewhere only you can reach.

## 6. Bring the next human

Everything above took you maybe an afternoon. The person who sent you this
guide did it through a referral link, and you now have one of your own on
your profile's Referrals tab. If this guide helped, pass yours on the same
way — a guide, a link, and an honest explanation beat a bare link every
time.

And if you have not signed up yet: [https://make.fun/r/g7gkqgw4](https://make.fun/r/g7gkqgw4)
(code `g7gkqgw4`). See you on a leaderboard.

## Licence

This guide is released under the MIT licence.
