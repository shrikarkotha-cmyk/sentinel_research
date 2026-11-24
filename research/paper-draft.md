# Sentinel: Evaluating Player-Centered Hardware-Backed Licensing for PC Games

Working paper, version 0.1 | November 23, 2026 | Preliminary research, not peer reviewed

## Abstract

Game publishers use anti-piracy systems to protect revenue during commercially important release periods, but authorization failures and performance regressions can burden legitimate owners. This project investigates whether hardware-backed licensing, local integrity verification, and developer-controlled security updates can deter unauthorized credential copying while preserving indefinite offline single-player access, supported modifications, and predictable performance. A preliminary Windows/macOS prototype demonstrated successful license issuance and local launch, rejection of a copied license under a different device key on the same Windows PC, and loading of a supported modification. No cross-device replication, graphical performance measurements, or comparative anti-tamper effectiveness results are yet available. The proposed evaluation separates credential-copy resistance from executable protection and compares security, reliability, and performance against defined controls.

## 1. Introduction

The research is motivated by player frustration with existing digital rights management (DRM). Publishers and players face different costs: publishers risk lost sales, whereas legitimate players risk activation failures, reduced compatibility, and overhead. The central question is whether continuously maintained game protection can improve this balance without introducing recurring online authorization requirements.

## 2. Background and related work

### 2.1 Publisher incentives

Volckmann [1] studied 86 Denuvo-protected PC games released between 2014 and 2022. Secondary reporting [2] describes estimated revenue losses of roughly 20 percent for first-week circumvention and 5 percent around week six. These estimates use indirect sales measures and a statistical counterfactual; they are not universal revenue forecasts or proof that any DRM product generates equivalent savings. The full methodology must be independently reviewed before the final paper makes quantitative causal claims.

Irdeto advertises binary-level integration, hardware binding, launch-window protection and performance-aware integration [3]. A publisher may rationally prefer an established supported service to building an internal security team. This is an inference about incentives, not direct evidence about individual procurement decisions.

### 2.2 Player experience

Thoman's comparison of Final Fantasy XV builds found no clear in-game frame rate penalty but observed loading differences, with other build changes potentially contributing [4]. In 2021, Irdeto confirmed a domain availability issue following reports that several games could not launch [5]. These examples justify studying both startup reliability and performance rather than assuming that DRM always reduces FPS.

### 2.3 Alternatives and prior art

Valve states that its Steam DRM wrapper alone is insufficient as a dedicated anti-piracy solution [6]. General-purpose application protection and licensing systems, including VMProtect, Digital.ai and Thales Sentinel LDK, also exist. DRM-free distribution represents a different strategy rather than a technical anti-tamper substitute. See the companion [market and prior-art review](002-publisher-incentives-and-prior-art.md).

Microsoft patent US12111893B2 describes TPM-based software licensing [7]. Microsoft also documents hardware-backed key protection and attestation [8]. The present study does not claim to invent hardware-bound licensing, and a patent citation is not a freedom-to-operate analysis. The proposed contribution is a reproducible evaluation of a particular player-centered combination of policies and technologies.

## 3. Proposed system and threat model

Sentinel consists of a developer-controlled packaging tool, a local authorization runtime, an activation and recovery service, and an experimental developer-side improvement process. A signed license binds a synthetic entitlement to an enrolled device identity. Existing licenses are verified locally without mandatory periodic connectivity. Supported mod assets are kept separate from signed original files.

A TPM protects appropriately configured device keys, not the entire application. Hardware key possession is different from remote attestation. A locally controlled execution environment cannot be assumed trustworthy merely because it has a TPM. The system targets unauthorized credential copying and unauthorized changes to designated files in an owned test application; it does not yet establish resistance to professional circumvention.

### 3.1 Offline authorization and recovery

A disconnected client cannot receive revocation notices or new security updates. Permanent offline access therefore sacrifices immediate revocation of already issued authorizations. Optional synchronization may deliver approved updates and facilitate recovery, but missing a connection must not invalidate an otherwise valid license. New installations and device recovery may require connectivity. Distinguish existing offline play from first activation during an outage.

### 3.2 Continuous maintenance

The proposed adaptive process operates in the development environment, not autonomously on player machines. Reproduce reported defects using authorized test fixtures, propose a fix, run regression and compatibility tests, review changes, and release approved signed updates via the normal distribution channel. NIST SSDF [9] and The Update Framework [10] provide relevant secure development and update-system guidance. No claim of automatic security discovery or self-repair is supported by the present prototype.

The publisher may retain lightweight protection indefinitely, with a documented removal option and end-of-service preservation plan. The Harbor design brief [11] originally emphasizes a launch-window sunset; its revised architecture favors official successor builds over a client-side switch. Sentinel adopts the official release approach but treats long-term retention as an optional publisher policy. A device that never connects cannot receive a successor release.

## 4. Methodology

Compare equivalent unprotected, software-key, and TPM-key configurations of the original test game. Use synthetic entitlements and only owned systems. Predefine functional conditions: authorized launch, network unavailable after enrollment, a distinct device key, supported mod loading, corrupted protected files, and authorized recovery. Run at least five repetitions per functional scenario. For timing comparisons, alternate conditions on the same hardware, collect at least 30 launches per condition, and report median, p95, sample size, and failures. Separate warm and cold launches. A future graphical test game is required for frame timing and FPS measurements.

## 5. Preliminary observations

| Pilot test | Observed outcome |
|---|---|
| Windows build and native tests | Successful, two reported tests passed |
| Activation using macOS service | Successful |
| Local authorized launch | Successful |
| Launch with service stopped | Reported successful; explicit network isolation not independently verified |
| Copied license with distinct key on the same PC | Rejected |
| Restore original enrolled identity | Successful |
| Supported community mod | Loaded |
| Cross-device cloning, graphical performance, hypervisor resistance | Not measured |

A license parsing error occurred before successful launch. Newline normalization was attempted and subsequent output reported zero CRLF endings; the root cause is not independently established. A regression test is needed. The pilot demonstrates feasibility, not statistical reliability or commercial effectiveness.

## 6. Discussion and limitations

The principal limitation is the difference between a valid authorization check and security of the application as a whole. Offline operation, flexible recovery, and compatibility introduce security and operational trade-offs. Platform-specific key providers require separate testing. Virtualization is not evidence of wrongdoing; legitimate environments should not be blocked solely because they are virtualized. Current evidence comes from one small demo and one physical Windows client. No comparison against Denuvo under equivalent conditions has been performed. The Harbor document is a design input, not empirical proof; its server-only key derivation proposal does not explain how a disconnected client would reconstruct the key, and requires redesign before implementation.

## 7. Conclusion

The initial pilot supports further research on local hardware-backed licensing and player-centered policies. It does not establish commercial superiority. The next milestone is a reproducible baseline and reliable license and recovery behavior, followed by controlled performance and compatibility measurements. The final paper will be revised after data collection and independent review.

## References

1. Volckmann, W. M., II (2025). Revenue effects of Denuvo digital rights management on PC video games. Entertainment Computing, 52, 100885. https://doi.org/10.1016/j.entcom.2024.100885
2. Ars Technica (2024). Reporting on the economic study. https://arstechnica.com/gaming/2024/10/the-true-cost-of-game-piracy-20-percent-of-revenue-according-to-a-new-study/
3. Irdeto. Video Game Anti-Piracy. Vendor documentation. https://irdeto.com/video-games/denuvo-anti-piracy/video-game-anti-piracy
4. Thoman, P. (2018). Final Fantasy XV DRM performance analysis. PC Gamer. https://www.pcgamer.com/denuvo-drm-performance-final-fantasy-15/
5. PC Gamer (2021). Denuvo service outage report. https://www.pcgamer.com/a-great-day-for-drm-as-denuvo-lapse-renders-tons-of-games-temporarily-unplayable/
6. Valve. Steam DRM. https://partner.steamgames.com/doc/features/drm
7. Microsoft Technology Licensing LLC (2024). US12111893B2. https://patents.google.com/patent/US12111893B2/en
8. Microsoft. Trusted Platform Module fundamentals. https://learn.microsoft.com/en-us/windows/security/hardware-security/tpm/tpm-fundamentals
9. Souppaya, M., Scarfone, K., and Dodson, D. (2022). Secure Software Development Framework, version 1.1. NIST SP 800-218. https://doi.org/10.6028/NIST.SP.800-218
10. The Update Framework. Overview. https://theupdateframework.com/docs/overview/
11. Harbor Anti-Tamper: Pitch and Design Brief (2026). Project-supplied design document, pp. 24-32. https://harbor-anti-tamper-pitch-and-design-qzyj.pages.grok.bot/

See [research integrity and contributions](integrity.md). This working paper requires student review, source verification, and further experiments before submission.
