# Tiny Chess: 4 KB Python Agent

## Architecture
- The entrypoint uses Python 3.13.
- The chess engine uses standard-library Python only.
- The source payload is encoded in base85.
- The payload decompresses with lzma.
- Chess moves use UCI coordinate notation.
- The engine searches moves without a network connection.
- Legal move generation checks king safety.
- Captures and check evasions use quiescence search.
- Search uses a finite depth budget.
- There is no opening book.
- There are no tablebases.
- The packed entry stays below 4096 bytes.
- Modular design with compressed payload (lzma + base85 encoding)
- Single-file execution via Python 3.13 standard library
- UCI protocol compliance for chess move generation
- Deterministic decision-making with no randomness

## Legal Moves
- Validates moves against checkmate/illegal positions
- Rejects captures that leave king in check
- Enforces proper piece movement rules
- Supports en passant and castling rules

## Quiescence Search
- Focuses on tactical patterns: captures, evasions, promotions
- Avoids shallow moves that could lead to immediate threats
- Limits depth to prevent infinite recursion

## Size Constraints
- Payload compressed to <4096 bytes
- Base85 encoding for compact storage
- No external dependencies or libraries

## Tests
- Smoke tested three independent chess positions.
- Self-play verified 24 consecutive legal half-moves.
- Most recent maximum move duration was 1.052 seconds.
- Tournament strength remains unverified.
- Smoke tests verify legal output on known positions
- Self-play tests evaluate move consistency
- Local validation checks code size compliance
- Official transcript checks are required before the entry can be submitted

## Limitations
- No opening books or endgame tablebases
- Tactical search has finite depth
- No network dependencies for competition
- No proven superiority over baseline engines

## License
- MIT License (see LICENSE file)
- Commercial use permitted with attribution
- Code available for testing and verification