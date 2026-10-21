# Month-wise record (December 2025 – September 2026)

One folder per month: what we did, what we found, and that month's evaluation reports.

| Month | Summary | Key finding |
|---|---|---|
| [2025-12_December](2025-12_December) | foundation tasks and first CNN | The 32×32 custom CNN reached 98.51% on the tomato test split (macro-F1 0.9830) and 86.77% over all 15 PlantVillage classes; indicative only, because these images largely overlap its training data (its own Mac split could not be rebuilt). |
| [2026-01_January](2026-01_January) | transfer learning and soybean | ConvNeXt-Tiny (PyTorch) was the best CNN: 99.92% test accuracy, macro-F1 0.9991. |
| [2026-02_February](2026-02_February) | PoCRA videos and the AI for Agri conference | No model experiments this month; no evaluation reports. |
| [2026-03_March](2026-03_March) | VLM papers and first VLM fine-tuning | BLIP-2 reached 89.00% accuracy (macro-F1 0.8928) on the shared 200-image test. |
| [2026-04_April](2026-04_April) | Qwen2.5-VL, the model that worked | Qwen2.5-VL LoRA: **98.50%** accuracy, macro-F1 0.9827, BLEU-4 0.4556, severity R² 0.9654. |
| [2026-05_May](2026-05_May) | PlantDx | 98.00% accuracy, macro-F1 0.9777, BLEU-4 0.386, severity R² 0.966: the same quality as April with reusable code. |
| [2026-06_June](2026-06_June) | publication of PlantDx and BLIP-2 re-run | The 1-epoch BLIP-2 re-run was scored 0% by its own June script; with the April protocol it reaches 89.00% (macro-F1 0.8948). The March run reached 89.00%. |
| [2026-07_July](2026-07_July) | knowledge-grounded PlantDx (tomato and mango) | Tomato: 7.3% → **93.7%** (macro-F1 0.919). Mango: 17.5% → **82.0%** (macro-F1 0.811). |
| [2026-08_August](2026-08_August) | expert-caption training and the TIH dataset | PlantVLM named the right disease for 2 of 6 validation images (chance 1 of 6): 30 images are too few. |
| [2026-09_September](2026-09_September) | TIH private tomato data and cross-domain benchmark | 'moreaccurate' (LoRA r64, 532 px) reached **92.76%** test accuracy (macro-F1 0.9378), +4.8 points over 'strong' (87.98%). |
