# Tiny chess contest engine

- A deterministic chess agent written in Python 3.13 for the make.fun tiny-chess-01 contest.
- Entry point is `main.py`, which must be launched as `python main.py` with `MAKEFUN_ENV_URL` set.
- Packaging is a single source line: an lzma-compressed, base85-encoded payload that is decompressed and executed at import.
- The payload imports only the standard library modules `base64` and `lzma` before decompression.
- The source file is sized to fit the contest's 4 KB source limit.
- Search is bounded so that every turn returns within the time budget.
- Legality is enforced by a move generator that filters out moves leaving the king in check.
- Quiescence search receives the king-in-check flag, so checking captures are searched as evasions.
- Check nodes with no legal replies return a mate score instead of a static evaluation.
- Perft counts match the reference move generator on the standard test positions.
- `best()` is deterministic and returns identical moves across repeated calls on the same position.
- A self-play smoke run produced 16 consecutive legal half-moves from the start position.

## Limitations

- Search depth is bounded, so tactics beyond the horizon are not seen.
- No opening book is included; opening play comes from search alone.
- No endgame tablebases are used.
- Only the Python standard library is used; there are no third-party dependencies.
- The 4 KB source limit constrains the amount of code that can ship.
- Verification covers movegen, perft, and short self-play runs, not long tournament play.
