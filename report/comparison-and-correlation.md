# Comparison and Correlation Report

## Section 1: Firmware vs. Runtime Correlation Table

| Firmware Feature / Function     | Expected Runtime Behavior           | Observed Behavior          | Correlation Strength |
|---------------------------------|-------------------------------------|----------------------------|---------------------|
| Secure Init Sequence            | System boots with verification      | Matches expectation        | High                |
| Config Param 'debug_mode' = 0   | No extra debug output               | No debug output observed   | High                |
| User Auth Check Present         | Requires authentication consistently| Inconsistent (see below)   | Medium              |
| Hidden Function: backdoor()     | No invocation in clean firmware     | Triggered in backdoor run  | High (backdoor only)|
| CRC Verification Enabled        | Only valid firmware loads           | Matches expectation        | High                |

> Table interpretation: Entries in the observed behavior column are based on runtime traces and logs. Correlation strength is assessed as High/Medium/Low based on coverage between firmware expectation and actual trace.

## Section 2: Comparison to Expectations

### Clean Firmware
- **Expectation:** All security checks active; no unauthorized pathways; firmware behaves as documented.
- **Observed:** All runtime behaviors matched expectations. No surprising side effects or runtime anomalies detected.

### Backdoor Firmware
- **Expectation:** Presence of a concealed function which can bypass authentication or provide root access when triggered with a specific input/state.
- **Observed:** Backdoor function detected and invoked under specific test conditions. System granted elevated permissions without standard authentication. All other behaviors were as per clean firmware.

### Summary of Observed Results
- Clean firmware displayed full conformance to security expectations.
- Backdoor firmware confirmed to exhibit correlation between a firmware function and an exploitable runtime path, validating the analysis hypothesis.

---

_This report summarizes the cross-comparison between firmware static structure and runtime analysis along with validation against security expectations._
