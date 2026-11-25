# Sentinel protection configurations

Status: proposed policy, not implemented product tiers.

## Standard and Enhanced

Standard prioritizes broad compatibility and minimal overhead, using protected device credentials when available. Enhanced may apply stricter device-binding policies and additional integrity verification, subject to measured security benefits, platform compatibility, and recovery tests. Both retain storefront-first activation, offline play after enrollment, no separate account, developer-side AI only, and supported mod boundaries. Do not silently downgrade security policy or lock out legitimate players without an accessible recovery path. No invasive monitoring, intentional disruption, or blanket virtualization restrictions.

Publishers should select configurations based on measured evidence, not marketing labels. No claim of Denuvo-equivalent resistance is supported by the current prototype.

## Separate disclaimer: player impact and limitations

Enhanced protection may add startup or asset-verification overhead and may require recovery after device credential loss, hardware replacement, or operating-system reinstallation. Compatibility with specific platforms and approved modifications must be established by testing. Exact impacts are currently unknown. Before offering a configuration, disclose measured performance and compatibility results, recovery requirements, and known limitations in clear language. Do not advertise zero overhead, universal compatibility, or guaranteed crack resistance. A disconnected device cannot receive revocations or fixes until it reconnects or installs an update. Preserve ordinary offline access for already-authorized players and publish an end-of-service preservation plan.

## Release gates

Require a reproducible security improvement over Standard, matched performance measurements, legitimate-player failure and recovery testing, human review, and an accurate player-facing disclosure. If the tradeoff is excessive, redesign or withhold the configuration. These policies do not authorize testing outside owned software or approved synthetic infrastructure.
