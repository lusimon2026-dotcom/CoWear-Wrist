# CoWear-Wrist

Dataset and benchmarks for inertial localization under natural wrist motion.

> **Preview release.** This repository currently contains two complete example sessions and their short excerpts. The complete curated dataset and benchmark resources are planned for release after paper acceptance. These examples are not the full dataset or an evaluation split.

## Wrist-motion conditions

- **Same:** the phone is held by the smartwatch-side hand, with the phone and watch kept together in front of the chest.
- **Different:** the phone is held by the opposite hand, while the smartwatch-side arm swings naturally.

## Available now

Start with the complete sessions:

| Condition | Complete example | IMU records | Ground-truth rows | Shared duration |
| --- | --- | ---: | ---: | ---: |
| Same | [samples/full_sessions/same](samples/full_sessions/same/) | 4,060 | 12,096 | 100.79 s |
| Different | [samples/full_sessions/different](samples/full_sessions/different/) | 30,418 | 15,209 | 152.08 s |

The two sessions provide about **4.2 minutes** of recorded motion. The preview files total approximately **12.7 MB**, including the quick excerpts below. They were not selected to represent performance rankings.

For a quick format inspection, ten-second excerpts are also available in [samples/same](samples/same/) and [samples/different](samples/different/). These excerpts come from the same two sessions; they are not additional independent recordings.

Each example contains:

- `watch_imu.jsonl`: smartwatch accelerometer and gyroscope records.
- `groundtruth.csv`: motion-capture reference position and orientation of the watch marker rigid body.
- `extrinsic_calibration.json`: existing session rotation calibration and coordinate convention.
- `sample_info.json`: source session, quality status, processing and provenance.

Original values, timestamps and interpolation flags are retained. No resampling or additional synchronization is applied. Use IMU `alignedRelativeS` and ground-truth `time_s` directly. The short excerpts retain their original 10–20 s time coordinates. Sensors can have different sample counts and grids; pair them by timestamps, not row number.

The examples illustrate file formats and individual trajectories. They do **not** reproduce the full paper benchmark or represent the complete condition distributions. Both parent sessions belong to the frozen test split. Different quality labels and sampling characteristics remain recorded in `sample_info.json`; the preview does not assert identical sampling rates.

See [PREVIEW_VALIDATION.json](PREVIEW_VALIDATION.json) for the format checks and [samples/checksums.sha256](samples/checksums.sha256) for file integrity. These checks do not constitute quantitative synchronization or attitude-accuracy validation.

## Planned release

- Complete curated watch dataset and data documentation.
- Frozen public splits and benchmark evaluation lists, including documented exclusions.
- Reproducible preprocessing, scoring and baseline evaluation resources.
- Versioned benchmark results and citation information.

## Reference conventions

IMU values are in the sensor frame. Ground truth describes the motion-capture marker rigid body, not an independently compensated IMU origin or body-center trajectory. The supplied calibration specifies a rotation; no translation lever-arm compensation is implied. Quaternion order is `xyzw`, as stated in the calibration metadata. Diagnostic calibration scores are not independent attitude-accuracy measurements.

## Provenance and licensing

These preview excerpts were selected from the existing CoWear data (`zyshe/CoWear`, revision `4eae17cf80d86da0f8370d7be5eeb5ccaf00e569`). The upstream dataset card declares Apache-2.0; the data samples retain that license. See [samples/LICENSE](samples/LICENSE) and [samples/NOTICE](samples/NOTICE). This preview does not assert that the broader upstream CoWear resource is unpublished. Paper citation details will be added when available.

## Project status

The complete CoWear-Wrist paper benchmark package is not yet downloadable from this repository. Release timing is planned for after paper acceptance and will be updated here.
