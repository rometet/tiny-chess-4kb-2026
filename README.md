# Tiny Chess: 4 KB Python Agent

## Architecture
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