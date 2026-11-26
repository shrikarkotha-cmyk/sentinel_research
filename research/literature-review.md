# Initial literature review

Draft, 2026-11-23. This is an annotated starting bibliography, not an exhaustive review. Claims below refer to the cited sources, not measured Sentinel results.

## Storefront DRM
Valve, [Steam DRM](https://partner.steamgames.com/doc/features/drm). Official developer documentation distinguishes basic copying deterrence from stronger anti-piracy protection. Implication: evaluate credential copying separately from resistance to executable modification.

## Hardware-backed licensing
Microsoft, [How Windows uses the TPM](https://learn.microsoft.com/en-us/windows/security/hardware-security/tpm/how-windows-uses-the-tpm).
Microsoft, [CNG Key Storage Providers](https://learn.microsoft.com/en-us/windows/win32/seccertenroll/cng-key-storage-providers).
Microsoft, [Key Attestation (MS-WCCE)](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-wcce/adc2aab5-701b-4f91-9dc0-5615543712bf).
These primary technical sources describe hardware-backed key storage and how a relying party can establish properties of a TPM key. Key possession, non-exportability, attestation, and whole-system trust are distinct concepts. Implication: measure what a device-bound license actually guarantees; do not claim that it protects an entire executable.

## Virtualization compatibility
Microsoft, [Virtualization-based security](https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-vbs). Windows uses virtualization for legitimate security isolation. Implication: virtualization presence is not evidence of piracy; any environment diagnostics should be nonblocking and privacy-preserving.

## Economic context
Volckmann, W. M., II (2025). [Revenue effects of Denuvo digital rights management on PC video games](https://www.sciencedirect.com/science/article/pii/S1875952124002532). Entertainment Computing, 52, 100885. This peer-reviewed paper examines the revenue implications of DRM circumvention. It motivates studying the launch window, but its results do not establish Sentinel's efficacy or revenue effects. Full methodology and limitations should be reviewed before quoting numerical estimates.

## Next questions
- How do different key storage providers affect portability and recovery?
- How much startup latency does local verification add?
- Which supported mod types are compatible?
- What remains unverified during offline operation?

The researcher should read each source and record their own interpretation before relying on it in a paper.
