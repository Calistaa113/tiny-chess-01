# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Calistaa113/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Calistaa113/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4,084-byte chess engine in Python for the
[tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01) — the strongest
chess engine in 4 KB of Python.

`main.py` is the whole engine: an lzma-compressed payload, standard library
only, no network, no model calls, no clock. 0x88 board, negamax with
alpha-beta, iterative deepening on a fixed 150,000-node budget,
Zobrist transposition table, quiescence search (captures, promotions, and
evasions while in check) with SEE pruning and delta pruning, MVV-LVA +
piece-square-gain move ordering, material + piece-square evaluation.

## Practice results (local, kit env server)

Mean practice Elo **1,190** over trials 0–2 (1,191 / 1,099 / 1,279),
above the 1,154 floor for the final. Beats the depth-2 and depth-3 house
rungs; still below the sunfish 4 KB baseline, so this entry is a work in
progress, not a prize favourite yet.

## How to run

```sh
MAKEFUN_ENV_URL=http://localhost:PORT python3 main.py
```

The engine reads the game from the env server and plays until the game ends.
Deterministic: fixed node budget, no clock, no unseeded randomness.
