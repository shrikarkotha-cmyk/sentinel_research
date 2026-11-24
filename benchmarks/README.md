# Performance and comparative DRM benchmark plan

Status: proposed protocol, November 24, 2026. No controlled comparative DRM performance results have been collected. Earlier graphical workload measurements are not measurements of DRM overhead.

## Research questions

Does Sentinel add measurable startup or gameplay overhead relative to an equivalent unprotected build? Under matched conditions, how does this overhead compare with legally accessible alternatives such as Steam DRM and Denuvo Anti-Tamper? Does AI-assisted maintenance preserve performance and compatibility after reviewed corrections?

## Comparison design

| Condition | Purpose | Availability |
| --- | --- | --- |
| Original Starfall Trail without Sentinel | Controlled reference | Planned developer-authorized baseline |
| Same Starfall Trail revision with Sentinel | Estimate Sentinel overhead | Prototype available; controlled measurements pending |
| Same workload with Steam DRM | Comparative protection measurement | Requires authorized integration |
| Same workload with Denuvo | Comparative protection measurement | Requires publisher or vendor cooperation |
| Other lawfully accessible DRM configurations | Additional comparisons | Subject to permission and comparable builds |

The primary comparison should use the same game source, assets, optimization settings, hardware, OS, drivers, resolution, graphics settings, scene, and input workload. Only protection configuration should differ. Record build hashes and all material differences. Different commercial games, patches, or storefront releases may be discussed as exploratory observations, but cannot establish the causal performance effect of DRM. Do not use unauthorized copies or remove third-party protections to obtain comparison builds.

If matched Denuvo or other proprietary builds cannot be obtained, explicitly report that limitation rather than claiming Sentinel is faster. Published vendor or independent benchmarks may be reviewed separately with their methodology and limitations.

## Measurements

| Metric | Unit or summary |
| --- | --- |
| Cold and warm startup | Milliseconds, median and p95 |
| Average FPS and 1% low FPS | Frames per second |
| Frame time | Milliseconds, median and p95/p99 |
| CPU and GPU utilization | Percent, with sampling method recorded |
| Memory usage | Peak and typical working set in MiB |
| Asset loading | Milliseconds |
| Installation size | MiB |
| Activation latency and success | Milliseconds and proportion |
| Offline relaunch, supported mods and recovery | Success/failure and player-facing steps |

## Procedure and reporting

Use repeatable scripted gameplay or a fixed replay with the same workload in each condition. Separate first activation from already-activated launches, and cold launches from warm launches. Control background processes, thermal conditions, power settings and network state. Randomize or alternate conditions where feasible. Record failed runs rather than silently discarding them. Use the existing research protocol's functional repetition and 30-launch timing targets; predeclare graphical trial durations and repetitions before measurement.

Preserve raw anonymized samples and report median, p95, variability and uncertainty. For startup time, percentage overhead = 100 × (protected median - baseline median) / baseline median. For FPS, report absolute differences and percentage change relative to the baseline, with the direction of improvement made explicit. Do not infer commercial performance from a lightweight test game alone.

Use a separate experiment to evaluate activation service load, with bounded synthetic accounts and increasing workloads against an isolated owned service. Report request arrival rate, concurrency, duration, success and rejection rates, latency percentiles, CPU, memory and database consistency. A target of 50,000 synthetic players is not equivalent to 50,000 simultaneous requests. No external services or real customer accounts are targets.

For adaptive maintenance, repeat the same performance and compatibility gates before and after each approved candidate change. See [Sentinel Adaptive](../docs/sentinel-adaptive.md).

Suggested CSV columns: experiment_id,build_revision,condition,run_number,workload_id,startup_ms,launch_success,average_fps,p95_frame_ms,peak_memory_mib,notes.

Publish both favorable and unfavorable results. Performance and protection strength must be evaluated separately; lower overhead does not establish equivalent security.
