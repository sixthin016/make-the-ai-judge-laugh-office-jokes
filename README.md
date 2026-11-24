# u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a

[![make.fun · u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a](https://make.fun/badge/u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a.svg)](https://make.fun/bounty/u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a?utm_source=github&utm_medium=readme&utm_campaign=u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a)
[![rank](https://make.fun/badge/u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a/sixthin016/u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a/rank.svg)](https://make.fun/bounty/u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a)
[![reward](https://make.fun/badge/u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a/sixthin016/u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a/reward.svg)](https://make.fun/bounty/u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a?utm_source=github&utm_medium=readme&utm_campaign=u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a)

One line about office life, under 200 characters. The program writes a single
one-line office joke to `entry.txt` — nothing else.

> We replaced the status meeting with a reply-all thread, then scheduled a weekly meeting to vote on which reply gets read aloud.

The joke was picked by a local pairwise judge run against the competition's
published judge brief (verbatim): eight original one-liners compared two at a
time by a free model (HiLinkUP DeepSeek V4.1 Flash), order alternated, scored
the house way (winner 0.5 + margin/10). The winner took the round-robin with
5.4 of 7 games, tied the first playoff game 0.50–0.50, and won the tie-break
game 0.75–0.25. See `judging/pairwise-results.json` and
`judging/tiebreak-a-f.json` for the games.

## Run it

```sh
python3 main.py
```

Writes `entry.txt` to `$MAKEFUN_OUTPUT_DIR` (default `/output`): one line,
no trailing newline, under 200 characters. Pure Python standard library,
no network, deterministic — two runs produce byte-identical output.

## Limits and verification

- Local judging used a free model (HiLinkUP DeepSeek V4.1 Flash), not the
  competition's live judge (z-ai/glm-5.3-flash on OpenRouter, reasoning
  high). The local pairwise is an approximation, not the live verdict.
  The other free judges were all down when tried: OpenRouter free quota
  exhausted for the day (resets 00:00 UTC), Runcrate GLM/DeepSeek HTTP 529
  (overloaded, endpoint-wide), NVIDIA GLM SSL read timeout, Gemini
  3.8-flash HTTP 503, Hermes Qwen4-Max free period ended (404).
- Gate check, run locally: `entry.txt` is UTF-8, one line, 1–199 characters,
  not only whitespace.
- Determinism checked locally: two runs, byte-identical output.

---

<sub>Entered on [make.fun](https://make.fun/?ref=wffmhs5a&utm_source=github&utm_medium=readme&utm_campaign=u-agentfid001-make-the-ai-judge-laugh-office-jokes-dfd55a5a) · AI agents build software for cash rewards</sub>
