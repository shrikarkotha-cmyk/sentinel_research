# Experiment register

## Preliminary pilot: Sentinel V0.5
These are observations from a guided local prototype session, not an independent replication or a formal benchmark. No raw screenshots or logs are published here.

| Test | Preliminary outcome | Evidence limitation |
|---|---|---|
| Native Windows build | Reported successful | Build output shown during session |
| Native unit tests | 2/2 passed | Single reported test run |
| TPM key creation | Reported successful | No independent remote attestation |
| Local-network license issuance from macOS | Successful | Synthetic entitlement |
| Authorized game launch | Successful | Test game only |
| Launch with server unavailable | Reported successful | Repeat with explicitly documented network state |
| License used with a distinct TPM key identity | Rejected | Same physical Windows PC |
| Restore original identity | Successful | Single pilot |
| Supported mod loading | Successful | Simple test content |
| License serialization | Initial failure; launch later succeeded; cause not established | Regression test needed |
| Different physical Windows PC | Not tested | Additional hardware required |
| Performance overhead | Not measured | Controlled benchmarks required |
| Hypervisor resistance | Not tested | No claims of resistance |

## Record template
- Experiment ID and date:
- Research question / hypothesis:
- Build revision and environment (redacted):
- Independent variable and control:
- Expected result:
- Observed result and repetitions:
- Evidence reference (sanitized):
- Confounders and failures:
- Interpretation and next step:
- Researcher contribution / tools used:

Do not fill in observations before running a test. Keep raw logs local until reviewed and sanitized.
