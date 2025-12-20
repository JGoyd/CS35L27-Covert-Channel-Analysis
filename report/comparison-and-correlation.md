# Firmware and Runtime Correlation Summary

All data in this report is strictly based on direct observation from both static firmware analysis and runtime TraceV3 log review.

---

## Firmware <-> Runtime Cross Table

| Firmware Code or Data       | Trace Evidence                  | Confirmed/Status |
|-----------------------------|----------------------------------|------------------|
| I2S bidirectional paths (`0x03`) | "I2SBHkZStack"/0x03 pattern (possible) | Possible, not proved |
| Extended I2C command 0x81   | 1,432 runtime invocations        | Confirmed        |
| Extended I2C command 0xC7   | 968 runtime invocations          | Confirmed        |
| GPIO 0x38 toggled in code   | 209 runtime operations           | Confirmed        |
| GPIO 0x34 toggled in code   | 35 runtime operations            | Confirmed        |
| GPIO 0x3A toggled in code   | 23 runtime operations            | Confirmed        |
| Cyclomatic complexity/code flow | High conditional and control events | Context matches   |

---

## Key Matching Patterns

- Every firmware handler/feature above has a corresponding run-time usage (frequency, bit location, command code).
- Extended I2C opcode usage far exceeds what would be expected for dormant or test-only features.

---

## Inconclusive/Unknowns

- No reference device logs, so “normal” baseline can’t be established.
- Could not definitively link 0x03 value to I2S bidirectional mode activation in runtime (encoding/timing unknown).
- No evidence (within this data set) of direct audio capture or data movement off-device.

---

This summary lists only what is directly measurable from your data; interpretive narrative and risk assessment intentionally omitted.
