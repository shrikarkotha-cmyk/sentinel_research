# Matched gameplay qualification of Sentinel Forge V0.18.1

A Windows 11 workstation with a Ryzen 7 9800X3D and RTX 5080 ran two builds of the same scripted 960×600 quest. Both executed the real workbench's movement, inventory, crafting, asset loading, CPU rasterization and OpenGL pixel transfer. The protected build verified its signed installation once at startup. Four alternating pairs per presentation mode produced 32,000 measured frames. All 16 trials completed the same number of quests and agreed on the rolling pixel-sample checksum.

| Paired cost, median [minimum, maximum] | Backbuffer | Presented |
|---|---:|---:|
| Average FPS | 0.05% [−1.64, 10.31] | 0.08% [−0.00, 0.41] |
| 1% low FPS | 1.73% [−3.15, 31.14] | 3.59% [−6.77, 24.82] |
| 0.1% low FPS | 7.74% [3.35, 68.81] | 10.84% [−2.80, 73.93] |
| First completed frame | +91.32 ms [+42.72, +111.14] | +95.77 ms [+82.48, +117.42] |
| Peak working set | +2.46 MB [+1.77, +2.61] | +2.51 MB [+2.49, +3.01] |

All pairs met the startup and memory targets. Both median average-FPS differences were below 1%, but the worst uncapped pair exceeded that threshold. Presented 1% lows missed the 2% target. One-percent and 0.1% lows use the mean times of each trial’s slowest 20 and 2 frames, respectively. A single workstation and four pairs are insufficient to qualify general studio workloads.

Median control/protected FPS was 678.80/681.94 without presenting and 59.79/59.70 while presenting. The largest adverse uncapped pair slowed on both executables. Several displayed runs had 138–195 ms stalls in both paths near the same frame positions. The verifier ran before rendering. Attribution requires separate timing for simulation, rasterization, upload, GPU completion and swap. GPU and VRAM samples included the desktop. The ordinary game’s keyboard-driven UI and window timer were outside the replay.

A display operation failed after ten complete trials. The final result retained those ten records exactly and added the six outstanding trials. The display interruption limits comparisons of ambient conditions. The 0.1% low is unusually sensitive to isolated stalls. No enforcement checks were removed in response to these findings.

## Defensive corrections and functional results

The synthetic storefront now validates ownership flags before writing, reads only a stored active value of 1 as owned, and rejects explicit empty transaction identifiers. A busy issuer advises retrying the same unexpired grant. Five focused regressions passed. The changed paths also passed 72 player cases, 16 recovery cases, nine bound-grant cases and 11 enabled workbench audit cases. A hardware-reference audit case skipped; the earlier owner-observed physical TPM and disconnected launch remain the applicable evidence.

At 16 in-process handler workers, the corrected issuer completed 1,000 arrivals in 0.149 s and 10,000 in 1.366 s. Baseline times were 0.143 s and 1.347 s on equivalent inputs. Each run issued the expected 80% valid licenses and denied the remaining 20% with zero incorrect decisions. Both SQLite integrity checks passed. The 50,000-arrival and PostgreSQL figures remain historical results. These measurements do not include 1,000 or 10,000 concurrent network connections.

## Engine and platform status

A small original Godot .NET beacon game compiled against the genuine 4.5.1 API and source generator. Its bootstrap contains one verification call and its interface starts with gameplay disabled. The first compiler attempt lacked the generator's project-directory setting; the corrected compile passed with warnings treated as errors. The editor, export pipeline and actual scene were unavailable. Its signed payload is the existing workbench. A future exported-title qualification must cover the engine application and content under their own approved title and manifest.

Unity and Unreal remain source examples. Local Linux, Proton and Steam Deck tests were unavailable. The recorded Windows, Linux and Apple Silicon hosted results, optional Intel native-only qualification and earlier physical Windows acceptance retain their original scope. The next milestone is frame-stall attribution and one exported Godot title with authorized startup, offline play, denial and recovery on equipped hardware.
