# Research 002: Publisher incentives, alternatives and prior art

Date: 2026-11-23. AI-assisted desk research; preliminary review, not original experimental findings.

## Research questions
Why do publishers buy anti-tamper products despite usability concerns? What alternatives exist? Which proposed Sentinel features are already described publicly?

## Economic and operational rationale
Volckmann (2025) studies the revenue implications of circumvention in 86 Denuvo-protected PC games. Early circumvention is associated with larger estimated revenue losses than late circumvention (roughly 20% in week one versus 5% around week six, as reported by Ars Technica). These are model estimates for a selected sample, not guaranteed revenue gains from installing DRM. The full journal article was inaccessible during this review; the dissertation abstract and reporting were available.
Irdeto markets binary-level integration, hardware-bound offline tokens, selective function profiling, integration support, emergency assistance and Proton compatibility. These are vendor-described capabilities, not independently verified comparative performance measurements. Publishers may prefer a proven supplier over internal engineering and ongoing maintenance; this is a plausible commercial inference, not a verified explanation for every customer.

## Documented usability concerns
Amplitude removed Denuvo from Humankind before launch following performance concerns. Resident Evil Village had multiple protection layers, complicating attribution. Irdeto confirmed a domain availability problem in November 2021 that affected game launches. These cases motivate tests of latency, reliability and recovery; they do not establish universal performance penalties.

## Alternatives
- Valve Steam DRM: ownership verification; Valve says the wrapper alone is not sufficient anti-piracy protection.
- Digital.ai (formerly Arxan): application protection marketed to game developers.
- VMProtect: general-purpose code protection and licensing, including hardware-bound serials.
- Thales Sentinel LDK: commercial software licensing and protection using hardware, software and cloud options. Existing use of the Sentinel name warrants review before commercialization.
- GOG: DRM-free offline installers and preservation; a different business model rather than an anti-tamper competitor.

## Prior art and novelty
Microsoft Technology Licensing LLC patent US12111893B2 (priority 2019-12-24; granted 2024-10-08) describes TPM-backed software license protection and validation including offline scenarios. This establishes relevant prior art, not a finding that our implementation infringes a patent. Denuvo publicly describes hardware binding, offline entitlements, post-build integration, selective profiling, performance validation, Proton support and removable protection. Its specific use of TPMs, indefinite offline guarantees and general mod compatibility were not established in the reviewed sources. Absence of public documentation is not proof a feature has never been tried.

## Trade-offs to investigate
TPM-backed key possession is distinct from executable integrity. Device recovery after hardware/key loss can impose support costs. Cross-platform support requires different security providers and fallback policies; Windows 11 generally requires TPM 2.0 while Apple silicon uses Secure Enclave. Indefinite offline authorization cannot receive immediate server-side revocation. These are engineering trade-offs, not claims about a competitor's private design decisions.

## Revised research direction
Compare player-first licensing policies under controlled conditions: unprotected baseline, software-key licensing and TPM-key licensing on the original test game. Measure launch success, startup latency, supported mod behavior, server-outage resilience and recovery. Evaluate a planned protection sunset and transparent documentation as policy goals. Keep credential-copy resistance separate from executable tamper resistance and commercial revenue impact. Do not claim superiority to Denuvo without comparable evidence. No third-party circumvention experiments.

## References
- Volckmann, W. M. II (2025). Revenue effects of Denuvo digital rights management on PC video games. Entertainment Computing 52, 100885. https://doi.org/10.1016/j.entcom.2024.100885
- Volckmann dissertation abstract: https://escholarship.org/uc/item/79n341wr
- Ars Technica, 2024, study coverage: https://arstechnica.com/gaming/2024/10/the-true-cost-of-game-piracy-20-percent-of-revenue-according-to-a-new-study/
- Irdeto, Video Game Anti-Piracy: https://irdeto.com/video-games/denuvo-anti-piracy/video-game-anti-piracy
- Ars Technica, Humankind, 2021: https://arstechnica.com/gaming/2021/07/denuvo-drm-removed-from-upcoming-strategy-game-dev-blames-performance-impact/
- PC Gamer, service interruption, 2021: https://www.pcgamer.com/a-great-day-for-drm-as-denuvo-lapse-renders-tons-of-games-temporarily-unplayable/
- Valve: https://partner.steamgames.com/doc/features/drm
- Digital.ai: https://digital.ai/catalyst-blog/guarding-the-realm-of-play-digital-ai-application-securitys-decade-long-legacy/
- VMProtect: https://vmpsoft.com/products/vmprotect
- Thales: https://docs.sentinel.thalesgroup.com/softwareandservices/ldk/default.htm
- GOG: https://www.gog.com/blog/the-gog-preservation-program/
- Microsoft patent: https://patents.google.com/patent/US12111893B2/en
- Microsoft TPM fundamentals: https://learn.microsoft.com/en-us/windows/security/hardware-security/tpm/tpm-fundamentals
- Windows 11 requirements: https://learn.microsoft.com/en-us/windows/whats-new/windows-11-requirements
- Apple Secure Enclave: https://support.apple.com/en-ca/guide/security/sec59b0b31ff/web

Next step: read and independently annotate the patent, official product documentation and economic study; document uncertainties before revising the experimental protocol.
