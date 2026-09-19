# Dataset card

## Identity

- Name: SherdLock Multiphysics Fragment Corpus v1.0
- Origin: original deterministic synthetic generation
- Size target: 200 MB to 2 GB raw archive
- Cases: 360 train, 120 test
- Licence: CC BY 4.0

## Generation

Procedural vessel profiles are partitioned into fragments, transformed into independent local scan frames, eroded, and observed through point, fracture-response, rendered RGB, and acoustic-tap channels. Candidate reversible braces receive local anchors and simulated response panels. Independent nuisance gains, viewpoint order, catalogue order, fragment order, and vessel gauges are sampled per case.

## Labels

Public training labels are stored separately in `train_labels.csv` and contain fragment membership, distractor state, discrete poses, and the oracle brace set. `train.csv` and `test.csv` contain the same five feature columns. Each NPZ's `fragment_ids` string array is the authoritative submission-ID catalogue and aligns positionally with all fragment tensors; brace rows map to `b00` through `b23`. Private test answers additionally contain true seam pairs, per-brace load effects, base load deficits, interference penalties, and normalization constants. Those private evaluator values are never copied to participant files.

The ten ordered `brace_features` columns are anchor span, normal mismatch, curvature mismatch, installation access, removal clearance, reversibility, contact-area cost, optical-obstruction cost, coarse expected benefit, and handling clearance. They are synthetic unitless `[0,1]` descriptors, not measured engineering ratings.

## Limitations and biases

The corpus favors approximately axisymmetric thin-walled ceramics, a fixed ten-fragment observation budget, eight orientation bins, two underlying vessels, and twenty-four catalogue braces. Synthetic erosion, color, acoustic response, and loading cannot represent the full variability of real excavated ceramics. The split tests procedural mechanism transfer, not geographical, chronological, cultural, or workshop attribution. No conclusion about authenticity, provenance, monetary value, safe restoration, or real structural integrity is supported.

## Sensitive fields

There are no people, locations, accession numbers, excavation records, or real cultural objects. Case and fragment identifiers are random opaque keys.
