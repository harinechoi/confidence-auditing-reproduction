# Experiment data

This directory contains the prompts, selected model outputs, cross-model verifier judgments, subset metadata, and derived evaluation summaries released with the paper.
```
experiment data/
  README.md
  model_costs.txt
  MMLU-Pro/
    prompts/           generation + judge templates
    model_outputs/     each model's answers (selected run)
    verifier_outputs/  cross-model judgments + coverage
  MMMU-Pro/
    prompts/
    model_outputs/
    verifier_outputs/  judgments + metrics + coverage
    sample/            dataset revision and which IDs were used
```

Not copied: API tokens, logs, PIDs, raw API dumps, image files, scripts, incomplete model runs, or retry/failure dumps.

## MMLU-Pro

- Sample: first 8,000 MMLU-Pro questions.
- Models (8): gpt-5.5, gpt-5.4-mini, gpt-5.4-nano, Claude Sonnet 5, Claude Haiku 4.5, Llama-3.1-8B, Qwen3-30B-A3B-Thinking-2507, Qwen3.5-35B-A3B.
- Columns in `model_outputs/`: question id, question, options, selected options, reasoning, self_confidence, llm_confidence_vector.
- Each `verifier_outputs/<model>.csv` is that model's answers plus `{other_model}_correctness` and `{other_model}_correctness_probability` from the other seven judges.
- A few Sonnet judge cells are empty (model refusals). See `verifier_outputs/coverage.txt`.

## MMMU-Pro

- Sample: first 1,000 MMMU-Pro `standard (10 options)` test questions, dataset revision `563f3e84bb3b90893083a1f039cfa13077f2302b`. IDs and checksums are in `sample/manifest.json`.
- Models (8): gpt-5.5, gpt-5.4-mini, gpt-5.4-nano, Claude Sonnet 5, Claude Haiku 4.5, Qwen3.5-35B-A3B, Qwen3-VL-30B-A3B-Instruct, Llama-4-Scout-17B-16E-Instruct.
- Generation prompt adds labeled images. Judge prompt attaches images in the same order.
- Sonnet is missing answers for `test_Biology_318` and `test_Agriculture_282`. See `sample/validation.json`.
- `verifier_outputs/metrics.json` has reference-label accuracy and per-pair judgment summaries.

Original MMMU-Pro images are not included in this repository. They should be obtained from the official benchmark distribution in accordance with its license and terms.