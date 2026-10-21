# BLIP-2 re-run with full evaluation (15 Jun 2026)

**What is here:** A 1-epoch BLIP-2 OPT-2.7B LoRA re-run with BLEU/ROUGE/CLIP evaluation. Model: `outputs/blip2_plantvillage/best`.

**Results:** BLEU-1 0.2081, BLEU-4 0.0819, ROUGE-L 0.3017; classification 0% (`evaluation_report.json`).

**Finding:** One epoch was not enough for BLIP-2 to reproduce the disease field; the longer March run reached 89%.
