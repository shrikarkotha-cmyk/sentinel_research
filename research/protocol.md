# Research protocol: draft 0.1

## Question
Can hardware-backed licensing reduce unauthorized copying of a PC game's credentials while retaining offline single-player access, supported mods, and acceptable startup overhead?

## Hypotheses
H1: Device-bound TPM keys reject licenses presented by a distinct key identity more reliably than portable credentials.
H2: An already enrolled installation can launch with its activation service unavailable.
H3: Changes to explicitly supported mod content do not invalidate authorization.
H4: The prototype introduces a small, measurable startup overhead; the threshold must be chosen before measurement.

## Scope
Use only the original Starfall Trail test game and synthetic accounts/licenses. Compare an unprotected baseline, software-backed licensing, and hardware-backed licensing when equivalent builds exist. This is a credential-copying study, not a measurement of commercial DRM cracking resistance. No third-party game circumvention, security setting changes, or real customer data.

## Method
1. Record build revision, OS version, CPU class, key provider, network state, and test condition without identifiers or secrets.
2. Run ordinary authorized launches, server-unavailable launches, wrong-key license rejection, supported mod loading, and authorized recovery scenarios.
3. Repeat each functional scenario at least five times; report counts and errors rather than declaring universal reliability.
4. For startup performance, use the same machine and game workload, alternate baseline and protected conditions, and record at least 30 launches per condition. Separate warm and cold starts; report median, p95, raw sample size, and differences. Record failures separately. Do not infer real-game FPS performance from a console demo.
5. Preserve failed tests, configuration changes, and confounders. Repeat after fixes. A second physical Windows device is needed for a genuine cross-device experiment.

## Limitations
Local authorization is not proof of executable integrity under adversarial control. A TPM key's reported provider is not remote attestation. An offline client cannot receive immediate revocations. A single device and synthetic game limit generalizability.

## Evidence and authorship
Record personal contributions, tool assistance, and directly observed outputs; follow the [project-wide disclosure](../README.md#research-contributions-and-ai-disclosure). Drafts are not results. Never publish private keys, identifiers, activation codes, raw logs containing secrets, or personal information.
