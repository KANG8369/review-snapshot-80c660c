# ROS 2 Package-Generation Benchmark: Review Artifact

This frozen artifact contains the five ROS 2 package-generation benchmark cases
used in the paper. Each case contains:

- `description.yaml`: the public package-generation task supplied to the Coder;
- `metric.yaml`: evaluation-only functional requirements and pass criteria;
- `reference/`: the source package used to construct and inspect the case.

The `metric.yaml` files and `reference/` packages are included for review and
must not be supplied to the Coder when reproducing the generation experiments.
Build validation and inspection-based FR evaluation are separate checks; these
files do not establish successful runtime robot behavior.

| Case | FRs | PCs |
| --- | ---: | ---: |
| `laser_scan_merger` | 7 | 16 |
| `human_detector` | 6 | 18 |
| `turtlebot3_aruco_tracker` | 3 | 7 |
| `turtlebot3_follower` | 5 | 17 |
| `nav2_waypoint_follower` | 8 | 23 |

Copyright and license notices in the reference packages are retained for
third-party attribution. This review artifact intentionally contains no Git
history or author-identifying repository metadata.
