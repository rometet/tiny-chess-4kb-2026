# Tiny chess contest engine

Deterministic Python 3.13 chess agent for make.fun tiny-chess-01. Run in the official environment: python main.py with MAKEFUN_ENV_URL configured. Designed for legal UCI moves, bounded search, and a 4 KB source limit.

## Search notes

Quiescence search passes the king-in-check flag into each recursive call, so checking captures are searched as evasions instead of being cut off at the leaf. Check nodes that run out of replies return a mate score instead of a static evaluation, so forced mates are no longer scored as quiet positions.

## Verification

Perft and movegen agree with the reference generator on the standard test positions; `best()` is deterministic across repeated calls and played 16 consecutive legal half-moves from the start position.
