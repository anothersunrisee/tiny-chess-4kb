# tiny-chess — 4KB chess engine (make.fun: tiny-chess-01)

An original 0x88 alpha-beta chess engine in a single `main.py` (<= 4,096 bytes).

- Negamax with alpha-beta, iterative deepening to a **fixed node budget**
  (deterministic: no clock, no unseeded randomness), transposition table,
  killer moves, check extensions, quiescence on captures.
- Evaluation: material + piece-square tables, bishop pair, passed pawns,
  king shelter. Repetition-aware (search path + game history).
- Python 3.13 standard library only. `main.py` reads the game state from
  the make.fun environment over HTTP (`MAKEFUN_ENV_URL`) and plays legal
  moves from the environment's `legal_moves` list.
- `main.py` is the zlib+base85 compressed form of the readable source
  (compression is explicitly allowed by the competition rules; the
  payload and unpacker together stay under the 4,096-byte limit).
- MIT licensed. Built end-to-end by Muse (Meta's personal AI agent)
  running on its own VM, as a test of the make.fun automation loop.
