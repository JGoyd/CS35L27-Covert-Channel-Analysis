# CS35L27 8051 Firmware Forensic Findings

**Firmware analyzed:** Region 32 (8051, 4096 bytes)  
**Supporting files:** codecctl.txt; all runtime TraceV3 logs (see methods)  
**Analysis Date:** December 18–19, 2025

---

## Major Observed Findings

| # | Technical Finding                  | Offset/Location         | Observation                                   |
|---|------------------------------------|------------------------|-----------------------------------------------|
| 1 | I2S “Bidirectional Mode” Code      | 0xE082C2, 0xE0858E     | MOV #0x03 to I2S register; 2 code paths found; uncommon in speaker amps. |
| 2 | Extended I2C Command Handler 0x81  | 0xE08EA4               | Handler for 0x81 found, non-standard opcode.  |
| 3 | Extended I2C Command Handler 0xC7  | 0xE08F79               | Handler for 0xC7 found, non-standard opcode.  |
| 4 | High Cyclomatic Complexity         | Whole-firmware         | 521 complexity, 407 jumps, 113 calls.         |
| 5 | Call/Return Discrepancy            | Whole-firmware         | 113 calls, 56 returns (imbalance: 57).        |
| 6 | High entropy (DSP section)         | 0x0C00–0x0FFF          | 7.30 bits/byte; matches heavily optimized code.|
| 7 | GPIO Bit 0x3A Manipulation         | Multiple, 5x           | SETB/CLR, matches likely interrupt bit.        |
| 8 | GPIO Bits 0x34, 0x38 Heavy Use     | Multiple, 8x each      | Used for unknown but consistent control.       |
| 9 | No self-modifying/obfuscated code  | All bins               | No encryption loops or anti-analysis found.    |
|10 | Minimal, short ASCII strings       | Several short strings  | 11 detected, none suspicious.                  |

---

- All findings represent directly observable, measurable characteristics or events in binary or logs.
- No risk assignments, theoretical surmise, or narrative included.
- For cross-correlation with runtime, see runtime-trace-analysis.md.

---