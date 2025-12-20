# Analysis Methods

This document describes only the data sources and factual binary/trace analysis techniques used in this forensic investigation.

## Data Sources
- CS35L27 8051 firmware binary (Region 32, 4096 bytes) extracted from hardware.
- `codecctl.txt`: Registry and configuration dump obtained via device utilities; used for register offset and initialization value analysis.
- TraceV3 files: 
    - logdata_LiveData.tracev3 (3.3 MB)
    - 00000000000076e4.tracev3 (7.6 MB)
    - 000000000000442d.tracev3 (870 KB)
    - 00000000000012fa.tracev3 (643 KB)
    - 0000000000000005.timesync (46 KB)

## Objective Analysis Techniques

- Static code analysis of 8051 binaries using Ghidra and Binwalk.
- String and pattern search via `strings`, regex, and custom scripts.
- Use of `codecctl.txt` for mapping register use and initialization state.
- Function boundary, call/return and jump/dispatch analysis via 8051 disassembly.
- Entropy mapping of binary regions for obfuscation/encryption checks.
- Systematic cross-check of firmware code/constant addresses with observed runtime behaviors in TraceV3 (hex and ASCII context).
- Counting and cataloging of event types including extended I2C commands, GPIO toggling, and I2S register values.

No non-public sources, inference, or speculation beyond direct result of binary/runtime/config file examination are recorded here.
