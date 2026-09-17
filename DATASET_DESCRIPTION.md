# SherdLock Multiphysics Fragment Corpus v1.0

SherdLock is an original deterministic synthetic dataset containing 480 mixed-fragment conservation cases: 360 training and 120 test. It contains no personal data, excavated objects, museum scans, or upstream copyrighted measurements. Each case simulates two thin-walled ceramic vessels, eight retained fragments, two distractors, erosion, scanner noise, tap-response variation, and twenty-four reversible brace candidates.

The organizer raw archive contains `manifest.csv`, `targets.jsonl`, `SCHEMA.json`, `BUILD_INFO.json`, `DATASET_CARD.md`, `DATASET_DESCRIPTION.md`, `LICENSE`, and `cases/*.npz`. `targets.jsonl` is organizer-only input: preparation converts training rows into public `target_json` labels and test rows into private `answers.csv`; it is never copied to prepared public data.

Prepared public data contains `train.csv`, `test.csv`, `sample_submission.csv`, `DATASET_CARD.md`, `DATASET_DESCRIPTION.md`, `SCHEMA.json`, `LICENSE`, and `cases/*.npz`. `DATASET_DESCRIPTION.md` is this overview and exact file contract. Prepared private data contains only `answers.csv`.

`train.csv` columns are `case_id`, `case_file`, `profile_family`, `fracture_family`, `clay_family`, and `target_json`. `test.csv` has the same five predictors and omits `target_json`. `sample_submission.csv` and `answers.csv` both have exactly `case_id,reconstruction_json`.

All point coordinates and translations are in millimetres. Rotation is an eight-bin cyclic orientation (`0` through `7`, each bin representing 45 degrees). Image and fracture-map values are digitizer counts. Tap responses are signed ADC counts. Brace contact area, optical obstruction, reversibility, and coarse benefit are unitless normalized features. Private load-panel values are simulator utilities, not measured forces or probabilities.

Training and test are disjoint in profile, fracture, clay, and joint-family tuples. This is a stylized thin-shell simulator, not an archaeological authentication system or safety-certified conservation model. It omits real mineral chemistry, long-term adhesive ageing, moisture transport, nonlinear fracture propagation, human handling, irregular scan occlusion, and curatorial ethics. Results must not be applied to real artifacts without expert inspection and physical validation.

Licence: CC BY 4.0. The Source URL must be a versioned public release of the participant-safe corpus; the organizer raw upload and private generator must remain private because they contain or reconstruct hidden evaluator state.
