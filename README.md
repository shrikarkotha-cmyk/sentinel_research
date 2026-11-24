# Sentinel Research

**Independent cybersecurity and software engineering research | Early-stage prototype**

Sentinel investigates whether hardware-backed game licensing can deter unauthorized credential copying while preserving offline single-player gameplay, supported modifications, and reasonable performance.

## Research question
Can a hardware-backed licensing system improve resistance to credential copying without imposing significant costs on legitimate players?

## Current status
A guided pilot using the original Starfall Trail C++ test game demonstrated local license issuance, authorized launch, rejection with a different key identity on the same PC, and supported mod loading. These preliminary observations are not independent replication, proof of commercial anti-piracy effectiveness, or a performance benchmark.

## Research index
- [Working research paper](research/paper-draft.md): consolidated background, methods and preliminary observations.
- [V1 development roadmap](docs/v1-roadmap.md): revised architecture, milestones and first coding session.
- [Publisher incentives and prior art](research/002-publisher-incentives-and-prior-art.md): competitor analysis.
- [Research integrity and contributions](research/integrity.md): authorship and research practices.
- [Research protocol](research/protocol.md): hypotheses, controls, and methodology.
- [Initial literature review](research/literature-review.md): technical and academic background.
- [Experiment register](experiments/README.md): pilot observations and evidence limitations.
- [Benchmark plan](benchmarks/README.md): proposed quantitative evaluation.
- [Research journal](journal/README.md): template for the student's own reflections.

## Design principles
Offline play after enrollment; supported mods; minimal overhead; privacy; recovery for legitimate users; no mandatory virtualization blocking. These are research goals, not proven guarantees.

## Research integrity
Only owned test software and synthetic credentials are in scope. Prototype development and initial documentation have involved AI assistance; the researcher records personal contributions and validates claims independently. No private credentials or original raw logs are included. Source code will be considered for publication only after review. No claim of being uncrackable or commercially validated is made.
