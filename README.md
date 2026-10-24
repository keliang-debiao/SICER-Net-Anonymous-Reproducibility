SICER-Net Anonymous Reproducibility Package

This repository contains the anonymous implementation package for the Style-Invariant Cue Expert Routing Network (SICER-Net). It includes source code, configuration files, command-line scripts, data-manifest documentation, automated tests, implementation notes, and reference records used to organize the reproducibility workflow.

Repository Contents

SICER-Net-Anonymous-Reproducibility/
├── configs/
│   ├── main.yaml
│   └── ablations.yaml
├── data/
│   └── README.md
├── reference_records/
│   ├── PROVENANCE.md
│   ├── ablation_reference.log
│   ├── baseline_reference.log
│   ├── development_cv_reference.log
│   ├── efficiency_reference.log
│   ├── external_validation_reference.log
│   ├── robustness_reference.log
│   ├── statistical_reference.log
│   ├── table3_five_fold.csv
│   └── table8_calibration.csv
├── scripts/
│   ├── audit_data.py
│   ├── build_splits.py
│   ├── check_cross_corpus.py
│   ├── evaluate_external.py
│   ├── export_tables.py
│   ├── fit_calibrators.py
│   ├── run_ablations.py
│   ├── run_baselines.py
│   ├── run_robustness.py
│   ├── run_statistics.py
│   ├── train_cv.py
│   ├── train_final.py
│   └── validate_repository.py
├── sicer_net/
│   ├── __init__.py
│   ├── baselines.py
│   ├── calibration.py
│   ├── config.py
│   ├── cues.py
│   ├── data.py
│   ├── engine.py
│   ├── losses.py
│   ├── metrics.py
│   ├── model.py
│   ├── robustness.py
│   └── statistics.py
├── tests/
│   ├── test_calibration.py
│   ├── test_cues.py
│   ├── test_metrics.py
│   ├── test_router.py
│   └── test_splits.py
├── .gitignore
├── IMPLEMENTATION_NOTES.md
├── LICENSE
├── pyproject.toml
├── README.md
├── REPOSITORY_MANIFEST.md
├── requirements.txt
└── run_pipeline.sh

Configuration Files

configs/main.yaml contains the project, data, preprocessing, model, training, calibration, statistical-analysis, external-evaluation, and efficiency settings.

configs/ablations.yaml defines the component configurations used by the ablation workflow.

Core Python Package

The sicer_net/ directory contains the reusable Python implementation:

config.py provides configuration loading utilities.

data.py contains data auditing, perceptual-duplicate grouping, manifest handling, dataset loading, and grouped partitioning functions.

cues.py implements RGB, one-level Haar high-frequency, and chromatic inconsistency cue construction.

model.py defines the frozen CLIP encoder interface, cue-specific residual adapters, reliability-conditioned routing, prediction heads, and calibrated deployment wrapper.

losses.py contains the reliability, cross-style contrastive, style-adversarial, routing-load, and group-distributionally robust optimization objectives.

calibration.py provides global temperature scaling and style-balanced reliability calibration components.

metrics.py contains classification, threshold-based, and calibration metric utilities.

statistics.py provides fold-level interval estimation, paired bootstrap, permutation testing, Holm correction, and McNemar testing utilities.

robustness.py defines the image perturbations used by the robustness workflow.

baselines.py contains the baseline-model registry and associated construction utilities.

engine.py contains training, prediction, checkpoint-management, and artifact-serialization functions.

Command-Line Scripts

The scripts/ directory contains entry points for each stage of the repository workflow:

audit_data.py audits dataset files and constructs integrity information.

check_cross_corpus.py checks overlap between development and external corpora.

build_splits.py creates duplicate-aware grouped development partitions.

train_cv.py manages cross-validation training.

run_baselines.py manages protocol-matched baseline runs.

fit_calibrators.py fits the calibration components from cross-fitted predictions.

train_final.py trains the final development-corpus model using the configured protocol.

evaluate_external.py applies the locked model and calibration components to the external corpus.

run_ablations.py manages the component-ablation configurations.

run_robustness.py applies the configured corruption and perturbation checks.

run_statistics.py performs the configured statistical analyses.

export_tables.py converts serialized artifacts into table-oriented files.

validate_repository.py checks the repository structure and required files.

The top-level run_pipeline.sh file groups the repository stages into a single shell entry point.

Data Documentation

The data/README.md file describes the expected directory layout, manifest fields, label representation, style metadata, source identifiers, and local placement of the public datasets. Dataset image files are not included in this repository.

Automated Tests

The tests/ directory contains checks for:

cue construction and tensor dimensions;

reliability-conditioned routing behavior;

grouped partition construction;

calibration components; and

metric calculations.

Reference Records

The reference_records/ directory contains provenance documentation, execution-style log records, and table-oriented CSV files included for pipeline and reporting checks. PROVENANCE.md describes the status and intended use of these files.

Supporting Files

IMPLEMENTATION_NOTES.md records fixed operational details for cue construction, trainable heads, routing, calibration, and optimization.

REPOSITORY_MANIFEST.md maps the main repository paths to their purposes.

requirements.txt lists the pinned Python dependencies.

pyproject.toml contains the package metadata, build-system settings, dependency declarations, and test configuration.

.gitignore excludes local environments, datasets, caches, checkpoints, and generated artifacts from version control.

LICENSE contains the MIT License for the repository.

License

The code in this repository is provided under the MIT License. See LICENSE for the complete license text.
