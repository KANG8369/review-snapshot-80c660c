# ROS 2 Package-Generation Benchmark

## Benchmark Cases

| Task ID | Category | Case | FRs | PCs |
| ---: | --- | --- | ---: | ---: |
| 1 | Perception | `laser_scan_merger` | 7 | 16 |
| 2 | Perception | `human_detector` | 6 | 18 |
| 3 | Localization | `turtlebot3_aruco_tracker` | 3 | 7 |
| 4 | Control | `turtlebot3_follower` | 5 | 17 |
| 5 | Control | `nav2_waypoint_follower` | 8 | 23 |

Each case is stored under `benchmarks/<case_name>/` and contains:

| File | Role during the reported evaluation |
| --- | --- |
| `description.yaml` | Public task specification supplied to the Coder and Evaluator. It contains package intent, functional requirements (FRs), and an optional target environment. |
| `metric.yaml` | Evaluation-only criteria supplied to the Evaluator, not the Coder. It repeats each public FR's ID and text and adds one or more hidden pass criteria (PCs). |
| `reference/` | Original package retained for benchmark provenance and manual review. It was not supplied to either agent as an input or used as candidate evidence. |

The Coder generates a complete ROS 2 package from the Description. A candidate
must pass build validation before FR evaluation. The Evaluator inspects the
buildable candidate against the Description and Metric without modifying the
package. An FR passes only when all of its associated PCs pass; a package
passes the reported procedure only when it builds and every FR is judged to
pass. This inspection-based result does **not** validate runtime robot behavior.

PCs must follow their public parent FRs and must not impose additional hidden
behavior or arbitrary implementation choices. Different implementations are
acceptable when they satisfy the public requirement. The hidden PCs are
included here for peer review but must not be shown to the Coder when
reproducing a generation run.

## Included Documentation and Validation

- [`benchmarks/README.md`](benchmarks/README.md) summarizes the case layout.
- [`docs/description-format.md`](docs/description-format.md) and
  [`docs/metric-format.md`](docs/metric-format.md) define the YAML formats.
- [`templates/`](templates/) contains example Description and Metric files.
- [`scripts/`](scripts/) contains lightweight format and consistency validators.

With Python 3.10+ and PyYAML 6.0.3 installed, run from the repository root:

```bash
python3 scripts/validate_all_fr_pc_metrics.py .
python3 scripts/validate_templates.py .
```

These scripts check structural rules, FR ID/text alignment, and PC counts. They
do not judge whether a PC faithfully captures its parent FR, evaluate a
generated package, or run a robot. The five reference packages retain their
third-party copyright and license notices for attribution.
