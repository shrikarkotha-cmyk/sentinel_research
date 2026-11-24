# Sentinel Foundation V1

Status: proposed development plan, originally November 23, 2026; updated November 24, 2026. V0.5 remains the initial pilot baseline. Later progress is tracked in the [research overview](../README.md).

## Design decisions

- Offline single-player authorization survives network outages and does not require periodic check-ins. Optional updates are not launch prerequisites.
- Keep the C++ runtime, Python activation service, TPM-backed key provider, signed licenses, signed file manifests and supported mod boundaries from V0.5, subject to source review.
- Use established cryptographic libraries and normal OS loading and update mechanisms. Defer binary rewriting, invasive monitoring and advanced anti-tamper research.
- No kernel drivers, tool scanning, VM bans, hidden telemetry, intentional crashes, or changes to player saves as enforcement responses.
- Platform-specific key providers must be tested separately. Do not equate a TPM key with proof of the whole environment.
- Developer-side adaptation proposes fixes, tests them, and requires human review and approved signed release. No autonomous code modification on player devices.
- Publisher chooses long-term lightweight maintenance or a clean official exit. Publish an end-of-service plan and preserve legitimate offline play.

## Milestones and completion gates

| Milestone | Deliverable | Completion gate |
|---|---|---|
| V1.0 baseline | Private source snapshot and clean build; repeat V0.5 tests | Build reproducible, test environment recorded, raw results sanitized |
| V1.1 authorization | Robust parsing, signature validation and documented error handling | Valid, altered, malformed and wrong-identity fixtures behave as expected |
| V1.2 reliability | Offline and recovery test matrix; supported mod boundaries | Activated offline launches and permitted mods pass; failures handled clearly |
| V1.3 developer toolkit | Package an owned test game with an explicit signed manifest and mod policy | A clean machine can use documented steps without exposing signing keys |
| V1.4 performance | Same-build comparison and graphical demo | Raw samples and limitations published; matched authorized DRM comparison when available |
| V1.5 maintenance | Developer-side regression pipeline and reviewed update process | Controlled comparison of diagnosis time, validated repair rate and regression risk; rejected update leaves installed game usable |
| V1.6 portability | Evaluate other OS providers and compatibility | Results documented per platform; unsupported platforms have clear behavior |

These are plans, not implemented features. No claim of stronger anti-tamper than Denuvo.

## Next research phase

The [Sentinel Adaptive proposal](sentinel-adaptive.md) defines where and when analysis runs, evidence requirements, human review, and evaluation gates. The [comparative benchmark protocol](../benchmarks/README.md) defines controlled performance tests and isolated activation scalability experiments. Both remain planned. Preserve the storefront-first player experience and offline authorization demonstrated in the V0.8.2 pilot.

## First coding session (historical plan)

Preserve the original working V0.5 directory. Work in a separate local copy or private source repository. Audit all files before sharing; never upload signing private keys, license files, activation codes, TPM references, databases or raw logs. The current public repository contains research, not the C++ implementation.

Run the existing Release build's CTest suite and record actual results. Inspect the license parser and its current tests. Add synthetic tests for valid and invalid signatures, malformed hex, LF and CRLF serialization, wrong device identity and missing files. Fix only demonstrated problems. Review code before rebuilding, compare test results, then record the lesson in the journal.

Learning objective: distinguish signing (authenticity), hashing (integrity), and device key possession (identity). Understand what the parser reads and why a verifier must reject malformed input without crashing. All tests operate on the original demo and synthetic credentials.
