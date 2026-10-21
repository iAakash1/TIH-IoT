# June 2026: publication of PlantDx and BLIP-2 re-run

## Work done

- PlantDx code published on GitHub (2–3 Jun).
- BLIP-2 re-run for 1 epoch with full evaluation (15 Jun); Florence-2 re-attempted.
- Expert-validated caption image set prepared (24 Jun); seven-VLM zero-shot benchmark (25 Jun).

## Findings

- The 1-epoch BLIP-2 re-run scored 0% classification (BLEU-1 0.2081): one epoch is too short; the March run reached 89%.
- Zero-shot benchmark (PoCRA report): Qwen3-VL-8B produced degenerate output on 16 of 30 images; general VLMs are unreliable without fine-tuning.

## Results

| Model / evaluation set | Accuracy | Macro-F1 |
|---|---:|---:|
| BLIP-2 1-epoch re-run (200) | 0.00% | 0.0000 |

## Evaluation reports in this folder

| File | Copied from |
|---|---|
| [`03_mar_aug2026_vlm_plantvillage__tp__evaluation_report.json`](evaluation_reports/03_mar_aug2026_vlm_plantvillage__tp__evaluation_report.json) | `03_mar_aug2026_vlm_plantvillage/tp/evaluation_report.json` |

## Code and models

- [BLIP-2 re-run](../../03_mar_aug2026_vlm_plantvillage/tp)
- [PoCRA report (zero-shot benchmark)](../../docs/06-PoCRA-PCCOE-Tomato-Mango-Report-Version1.docx)
