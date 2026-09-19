# SherdLock Multiphysics Fragment Corpus v1.0

SherdLock is an original deterministic synthetic dataset containing 480 mixed-fragment conservation cases: 360 training and 120 test. It contains no personal data, excavated objects, museum scans, or upstream copyrighted measurements. Each case simulates two thin-walled ceramic vessels, eight retained fragments, two distractors, erosion, scanner noise, tap-response variation, and twenty-four reversible brace candidates.

The organizer raw archive contains `manifest.csv`, `targets.jsonl`, `SCHEMA.json`, `BUILD_INFO.json`, `DATASET_CARD.md`, `DATASET_DESCRIPTION.md`, `LICENSE`, and `cases/*.npz`. `targets.jsonl` is organizer-only input: preparation writes public training labels to `train_labels.csv` and test answers to private `answers.csv`; the organizer file itself is never copied to prepared public data.

Prepared public data contains `train.csv`, `train_labels.csv`, `test.csv`, `sample_submission.csv`, `DATASET_CARD.md`, `DATASET_DESCRIPTION.md`, `SCHEMA.json`, `LICENSE`, and `cases/*.npz`. `DATASET_DESCRIPTION.md` is this overview and exact file contract. Prepared private data contains only `answers.csv`.

`train.csv` and `test.csv` have the identical ordered feature schema `case_id,case_file,profile_family,fracture_family,clay_family`. `train_labels.csv` has `case_id,target_json` and joins one-to-one to the 360 training feature rows by `case_id`; `target_json` is the supervised reconstruction-and-brace label described in the challenge. `sample_submission.csv` and `answers.csv` both have exactly `case_id,reconstruction_json`.

Every case NPZ contains a length-10 Unicode `fragment_ids` array. `fragment_ids[i]` is the exact submission identifier for index `i` across `point_cloud`, `fracture_maps`, `photo_views`, `tap_response`, and `coarse_pose`. Each pair in `brace_endpoints` uses those same zero-based indices. Brace catalogue row `j` is named `b{j:02d}`, from `b00` through `b23`. These identifiers are strings and have no physical unit or ordinal meaning.

`brace_features` has shape `24 x 10`, float16, with this fixed column order: `0 anchor_span`, `1 normal_mismatch`, `2 curvature_mismatch`, `3 installation_access`, `4 removal_clearance`, `5 reversibility`, `6 contact_area_cost`, `7 optical_obstruction_cost`, `8 coarse_expected_benefit`, `9 handling_clearance`. Values are unitless in `[0,1]`. Lower is preferable for mismatch/span/cost/obstruction columns 0–2, 6, and 7; higher is preferable for access/clearance/reversibility/benefit columns 3–5, 8, and 9.

All point coordinates and translations are in millimetres. Rotation is an eight-bin cyclic orientation (`0` through `7`, each bin representing 45 degrees). Image and fracture-map values are digitizer counts. Tap responses are signed ADC counts. Brace contact area, optical obstruction, reversibility, and coarse benefit are unitless normalized features. Private load-panel values are simulator utilities, not measured forces or probabilities.

Training and test are disjoint in profile, fracture, clay, and joint-family tuples. This is a stylized thin-shell simulator, not an archaeological authentication system or safety-certified conservation model. It omits real mineral chemistry, long-term adhesive ageing, moisture transport, nonlinear fracture propagation, human handling, irregular scan occlusion, and curatorial ethics. Results must not be applied to real artifacts without expert inspection and physical validation.

Licence: CC BY 4.0. The Source URL must be a versioned public release of the participant-safe corpus; the organizer raw upload and private generator must remain private because they contain or reconstruct hidden evaluator state.
