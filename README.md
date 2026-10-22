# Confidence Auditing Reproduction Artifacts

This repository contains the public experimental artifacts accompanying the paper:

**From Self-Confidence to Statistical Accuracy: Scaling Human-in-the-Loop Evaluation with Direct and LLM-Assisted Auditing**

The paper studies confidence-stratified partial auditing and cross-model verification for estimating language-model accuracy under limited human-labeling budgets. Experiments use MMLU-Pro and MMMU-Pro to evaluate confidence calibration, partial-audit accuracy recovery, verifier performance, and verifier-assisted label efficiency.

## Repository contents

```text
data/
└── experiment_data/
    ├── README.md
    ├── model_costs.txt
    ├── MMLU-Pro/
    │   ├── models.txt
    │   ├── prompts/
    │   ├── model_outputs/
    │   └── verifier_outputs/
    └── MMMU-Pro/
        ├── models.txt
        ├── prompts/
        ├── model_outputs/
        ├── verifier_outputs/
        └── sample/
```

For additional details about individual files and benchmark configurations, see [`data/experiment_data/README.md`](data/experiment_data/README.md).

## Released artifacts

The repository includes:

- Generation prompts used to elicit model answers and self-reported confidence.
- Verification prompts used for cross-model correctness judgments.
- Selected model outputs for MMLU-Pro and MMMU-Pro.
- Cross-model verifier judgments.
- Verifier-coverage and status summaries.
- Derived verifier metrics for MMMU-Pro.
- The MMMU-Pro subset manifest, run configuration, and validation summary.
- Model-cost information used in the cost-sensitivity analysis.

For each verifier model, the released verifier-output files contain two corresponding fields:

- `[model_name]_correctness`: the verifier’s binary assessment of whether the selected target answer is correct.
- `[model_name]_correctness_probability`: the verifier’s estimated probability that the selected target answer is correct.

The primary paper analysis uses the binary verifier judgments.

## MMLU-Pro

The MMLU-Pro release contains selected usable outputs from eight target models evaluated on a population of up to 8,000 questions. The corresponding verifier files contain cross-model judgments from the other eligible models, excluding self-verification.

See the following files for details:

- [`data/experiment_data/MMLU-Pro/models.txt`](data/experiment_data/MMLU-Pro/models.txt)
- [`data/experiment_data/MMLU-Pro/verifier_outputs/coverage.txt`](data/experiment_data/MMLU-Pro/verifier_outputs/coverage.txt)

## MMMU-Pro

The MMMU-Pro analysis uses the first 1,000 examples, in dataset order, from the test split of the `standard (10 options)` configuration of `MMMU/MMMU_Pro`, fixed at revision:

```text
563f3e84bb3b90893083a1f039cfa13077f2302b
```

Seven model runs contain 1,000 outputs. Claude Sonnet 5 contains 998 outputs because answers are unavailable for `test_Biology_318` and `test_Agriculture_282`.

The exact selected-example identifiers and checksums are provided in:

- [`data/experiment_data/MMMU-Pro/sample/manifest.json`](data/experiment_data/MMMU-Pro/sample/manifest.json)
- [`data/experiment_data/MMMU-Pro/sample/run_config.json`](data/experiment_data/MMMU-Pro/sample/run_config.json)
- [`data/experiment_data/MMMU-Pro/sample/validation.json`](data/experiment_data/MMMU-Pro/sample/validation.json)

The original MMMU-Pro images are not duplicated in this repository. They should be obtained from the official benchmark distribution in accordance with its license and terms.

## Scope

This repository releases prompts, selected model outputs, verifier judgments, subset information, and derived evaluation summaries. It does not include API credentials, raw API dumps, provider logs, retry or failure dumps, benchmark images, or executable experiment scripts.

## Licenses and terms

The released materials remain subject to the licenses and terms of the original benchmarks and model providers. This repository does not grant additional rights to third-party benchmark content or model outputs.

## Citation

Citation information will be added after the arXiv version of the paper becomes available.

## Questions

Please use the repository’s GitHub Issues page for questions concerning the released artifacts.