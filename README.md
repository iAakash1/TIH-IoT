# TIH-IoT: Crop Disease Detection, Chanakya Fellowship (TIH IIT Bombay)

Image-based crop disease detection with CNNs and Vision-Language Models for **tomato, mango and soybean**,
carried out from **December 2025 to September 2026** under the TIH IIT Bombay Chanakya Fellowship (Agri-AI 2025).

**Team:** Kamaaksha Rajendra Kharul, Aakash Trimbak Jawle, Dr. Santwana Gudadhe (Faculty Mentor, PCCOE Pune).
**TIH mentors:** Harish Lokawad, Hrishikesh Patil, Rutuja.

This repository holds everything produced during the fellowship: code, trained models (via Git LFS), evaluation
reports, split files and documents. Datasets are **not** included (PlantVillage, MangoLeafBD, SoyNet and the
TIH tomato dataset have their own licences or owners).

```bash
git lfs install
git clone https://github.com/iAakash1/TIH-IoT.git
```

## Timeline

| Month | Work | Folder |
|---|---|---|
| Dec 2025 | TIH foundation tasks: image operations (package vs scratch), training/inference preprocessing, quality guardrails, CNN theory; custom CNN trained from scratch (29 Dec) | [01_dec2025_jan2026_cnn_baselines](01_dec2025_jan2026_cnn_baselines) |
| Jan 2026 | Keras transfer learning (MobileNetV2, EfficientNetB3, ConvNeXt-Tiny), PyTorch ConvNeXt-Tiny, crop validation; SoyNet soybean (Keras + PyTorch) on the VDI | [01_…](01_dec2025_jan2026_cnn_baselines), [02_jan2026_soybean_soynet](02_jan2026_soybean_soynet) |
| Feb 2026 | Video editing for the PoCRA project; attended the AI for Agri conference | – |
| Mar 2026 | VLM literature study; LLaVA-1.6 and BLIP-2 LoRA fine-tuning on PlantVillage | [03_mar_aug2026_vlm_plantvillage/outputs](03_mar_aug2026_vlm_plantvillage/outputs) |
| Apr 2026 | Research papers (below); Florence-2 attempt; Qwen2.5-VL-7B LoRA (98.50%); CLIP OOD + GradCAM pipeline | [03_…/qwen](03_mar_aug2026_vlm_plantvillage/qwen) |
| May 2026 | PlantDx restructured pipeline, 15 PlantVillage classes (98.00%) | [03_…/PlantDx](03_mar_aug2026_vlm_plantvillage/PlantDx) |
| Jun 2026 | PlantDx code published; BLIP-2 re-run; expert-validated caption set; 7-VLM zero-shot benchmark | [03_…/tp](03_mar_aug2026_vlm_plantvillage/tp) |
| Jul 2026 | Knowledge-grounded PlantDx with MLX QLoRA: tomato 93.7%, mango 82.0% | [experimentation/research/mlx_pipeline](https://github.com/iAakash1/experimentation/tree/refactor/professional-research-layout/research/mlx_pipeline) |
| Aug 2026 | PlantVLM on 150 expert captions; TIH tomato dataset received; SigLIP/OpenCLIP prototype | [03_…/newpipe](03_mar_aug2026_vlm_plantvillage/newpipe), [05_…](05_aug2026_siglip_openclip_tih_prototype) |
| Sep 2026 | TIH private tomato dataset (11 classes): Qwen2.5-VL QLoRA runs (92.76% test); cross-domain benchmark (69.32%) | [04_…/experiments/tih_tomato_qwen](04_jul_sep2026_plantdx_mlx_and_tih_tomato/experiments/tih_tomato_qwen) |
| Oct 2026 | 1 Oct: ICAIN 2026 paper accepted. Every saved model re-evaluated with its original split | [evaluation_reports_oct2026](evaluation_reports_oct2026) |

## Month-wise record

Each month (December 2025 to September 2026) has its own folder in [`month_wise/`](month_wise) with a short README
(work done, findings, results) and that month's evaluation reports:
[Dec 2025](month_wise/2025-12_December) · [Jan](month_wise/2026-01_January) · [Feb](month_wise/2026-02_February) ·
[Mar](month_wise/2026-03_March) · [Apr](month_wise/2026-04_April) · [May](month_wise/2026-05_May) ·
[Jun](month_wise/2026-06_June) · [Jul](month_wise/2026-07_July) · [Aug](month_wise/2026-08_August) ·
[Sep 2026](month_wise/2026-09_September)

## Results

| Crop | Model | Eval set | Accuracy | Macro-F1 | Report |
|---|---|---|---:|---:|---|
| Tomato | Custom CNN 32x32 (TF/Keras) | tomato test, 2,411 | 98.51% | 0.9830 | [report](evaluation_reports_oct2026/keras/custom_cnn_best_tomato_test) |
| Tomato | MobileNetV2 (Keras) | held-out val, 3,198 | 90.90% | 0.8939 | [report](evaluation_reports_oct2026/keras/mobilenetv2_keras) |
| Tomato | EfficientNetB3 (Keras) | held-out val, 3,198 | 93.59% | 0.9275 | [report](evaluation_reports_oct2026/keras/efficientnetb3_keras) |
| Tomato | ConvNeXt-Tiny (Keras) | held-out val, 3,198 | 96.15% | 0.9507 | [report](evaluation_reports_oct2026/keras/convnext_tiny_keras) |
| Tomato | ConvNeXt-Tiny (PyTorch) | test, 2,411 | 99.92% | 0.9991 | [report](evaluation_reports_oct2026/convnext_torch) |
| Tomato | LLaVA-1.6-Mistral-7B LoRA | PlantVillage val, 200 | 2.00% | 0.0151 | [report](evaluation_reports_oct2026/llava_v16) |
| Tomato | BLIP-2 OPT-2.7B LoRA (Mar) | PlantVillage val, 200 | 89.00% | 0.8928 | [report](evaluation_reports_oct2026/blip2_march) |
| Tomato | Florence-2-base-ft zero-shot | PlantVillage val, 200 | 0.00% | 0.0000 | [report](evaluation_reports_oct2026/florence_zeroshot) |
| Tomato | Qwen2.5-VL-7B zero-shot | PlantVillage val, 200 | 8.50% | 0.0800 | [report](evaluation_reports_oct2026/qwen_zeroshot) |
| Tomato | BLIP-2 OPT-2.7B LoRA, 1-epoch re-run (Jun) | PlantVillage val, 200 | 0.00% | 0.0000 | [report](03_mar_aug2026_vlm_plantvillage/tp/evaluation_report.json) |
| Tomato | Qwen2.5-VL-7B LoRA r32 (Apr) | PlantVillage val, 200 | 98.50% | 0.9827 | [report](03_mar_aug2026_vlm_plantvillage/qwen/evaluation_report.json) |
| Tomato | Qwen2.5-VL-7B LoRA, PlantDx 15-class (May) | PlantVillage val, 200 | 98.00% | 0.9777 | [report](03_mar_aug2026_vlm_plantvillage/PlantDx/outputs/evaluations/report.json) |
| Tomato | Qwen2.5-VL-7B-4bit QLoRA, knowledge-grounded (MLX) | test, 910 | 93.70% | 0.919 | [results](https://github.com/iAakash1/experimentation/tree/refactor/professional-research-layout/research/mlx_pipeline) |
| Tomato | PlantVLM, 150 expert captions (Aug) | val, 6 images | 33.3% retrieval | 0.278 | [report](03_mar_aug2026_vlm_plantvillage/newpipe/runs/run_002_fold0/evaluation/val_report.json) |
| Tomato (TIH) | Qwen2.5-VL-7B QLoRA 'strong' | test, 649 | 87.98% | 0.8991 | [report](04_jul_sep2026_plantdx_mlx_and_tih_tomato/reports/tih_tomato_qwen_qlora_strong/test_finetuned/metrics.json) |
| Tomato (TIH) | Qwen2.5-VL-7B QLoRA 'moreaccurate' | test, 649 | 92.76% | 0.9378 | [report](04_jul_sep2026_plantdx_mlx_and_tih_tomato/reports/tih_tomato_moreaccurate/test_finetuned/metrics.json) |
| Tomato (TIH) | 'moreaccurate', external | Dataset/testing, 176 | 69.32% | 0.7195 | [report](04_jul_sep2026_plantdx_mlx_and_tih_tomato/reports/tih_tomato_moreaccurate_external/metrics.json) |
| Mango | Qwen2.5-VL-7B-4bit QLoRA (MLX) | test, 200 | 82.00% | 0.811 | [results](https://github.com/iAakash1/experimentation/tree/refactor/professional-research-layout/research/mlx_pipeline) |
| Soybean | ResNet50 (PyTorch) | test, 560 | 91.61% | 0.7814 (Healthy-class F1) | [metrics](02_jan2026_soybean_soynet/results/experiments/resnet50) |
| Soybean | EfficientNetB3 (PyTorch) | test, 560 | 93.93% | 0.8317 (Healthy-class F1) | [metrics](02_jan2026_soybean_soynet/results/experiments/efficientnet_b3) |
| Soybean | EfficientNetB0 (PyTorch) | test, 560 | 93.39% | 0.8195 (Healthy-class F1) | [metrics](02_jan2026_soybean_soynet/results/experiments/efficientnet_b0) |
| Soybean | MobileNetV2 (PyTorch) | test, 560 | 92.50% | 0.8000 (Healthy-class F1) | [metrics](02_jan2026_soybean_soynet/results/experiments/mobilenetv2) |
| Soybean | ResNet50 (Keras) | test, 558 | 95.16% | 0.8556 (Healthy-class F1) | [report](02_jan2026_soybean_soynet/results/experiments/final_report.md) |

## Publication

**Efficient QLoRA Fine-Tuning of Qwen2.5-VL for Multi-Class Tomato Disease Classification and Cross-Domain Evaluation**. Submission 953, accepted on 1 October 2026 for the Proceedings of ICAIN 2026 (Springer LNNS series; indexed in
zbMATH, Scopus, DBLP), among the top 20% of reviewed papers. Based on the TIH tomato work in
[`04_jul_sep2026_plantdx_mlx_and_tih_tomato`](04_jul_sep2026_plantdx_mlx_and_tih_tomato).

## Repository layout

| Folder | Contents |
|---|---|
| `01_dec2025_jan2026_cnn_baselines/` | `cottoncrop_repo_snapshot/` (preprocessing package, crop validation, Keras TL), `keras_pipeline_kamaaksha/` (CNN + TL models and training code), `pytorch_convnext/` (notebooks, model, `splits/split_70_15_15.csv`) |
| `02_jan2026_soybean_soynet/` | Keras and PyTorch pipelines, `results/experiments/*` (metrics, histories, Grad-CAM, models), `splits/` |
| `03_mar_aug2026_vlm_plantvillage/` | `outputs/` (LLaVA, BLIP-2 adapters), `tp/` (BLIP-2 re-run), `florence/`, `qwen/`, `other/`, `latest_changes/`, `PlantDx/`, `newpipe/` (PlantVLM) |
| `04_jul_sep2026_plantdx_mlx_and_tih_tomato/` | Knowledge-grounded PlantDx package (`src/plantdx`), configs, `research/`, TIH `checkpoints/`, `reports/`, `experiments/` |
| `05_aug2026_siglip_openclip_tih_prototype/` | SigLIP / OpenCLIP contrastive pipeline for the TIH dataset |
| `evaluation_reports_oct2026/` | Re-evaluation of every saved model (`evaluation_report.json`, predictions, confusion matrices) and the scripts that produced them |
| `month_wise/` | One folder per month: README with work, findings and results, plus that month's evaluation reports |
| `docs/` | PoCRA reports, PlantDx engineering history, presentations |

Original development history lives in the source repositories:
[iAakash1/experimentation](https://github.com/iAakash1/experimentation),
[iAakash1/CottonCrop](https://github.com/iAakash1/CottonCrop),
[iAakash1/VLM](https://github.com/iAakash1/VLM),
[kharulkamaaksha/Crop_Disease_VLM](https://github.com/kharulkamaaksha/Crop_Disease_VLM),
[kharulkamaaksha/VLM](https://github.com/kharulkamaaksha/VLM),
[kharulkamaaksha/Tomato_12th_Aug_2026](https://github.com/kharulkamaaksha/Tomato_12th_Aug_2026).

## Research papers studied (March to April 2026)

1. K. Nguyen Quoc, L. Le Thi Thu, L.-D. Quach, *A Vision-Language Foundation Model for Leaf Disease Identification*, 2025. [arXiv:2505.07019](https://arxiv.org/abs/2505.07019)
2. M. Gupta, P. Desai, R. Greer, *Agro-Consensus: Semantic Self-Consistency in Vision-Language Models for Crop Disease Management in Developing Countries*, 2025. [arXiv:2510.21757](https://arxiv.org/abs/2510.21757)
3. M. Z. Hossain et al., *A Lightweight and Explainable Vision-Language Framework for Crop Disease Visual Question Answering*, 2026. [arXiv:2601.05143](https://arxiv.org/abs/2601.05143)
4. Z. Zhao et al., *Image Fusion via Vision-Language Model (FILM)*, ICML 2024. [arXiv:2402.02235](https://arxiv.org/abs/2402.02235)
5. H. Liu et al., *Visual Instruction Tuning (LLaVA)*, NeurIPS 2023. [arXiv:2304.08485](https://arxiv.org/abs/2304.08485)
6. J. Li et al., *BLIP-2*, ICML 2023. [arXiv:2301.12597](https://arxiv.org/abs/2301.12597)
7. J. Bai et al., *Qwen2.5-VL Technical Report*, 2025. [arXiv:2502.13923](https://arxiv.org/abs/2502.13923)
8. P. Panchal et al., *Deep Learning-Driven Image Captioning: Progress Through Transformers and Large Language Models*, PLOS ONE, 2026. [doi:10.1371/journal.pone.0345012](https://doi.org/10.1371/journal.pone.0345012)

## Notes

- Code is kept exactly as it was run; scripts contain the original absolute paths of the training machines.
  Point them at your own dataset copy before running.
- The knowledge-grounded MLX experiments (tomato and mango, July 2026) ran on an Apple Silicon Mac. Their
  results, confusion matrices and configs are in [iAakash1/experimentation → research/mlx_pipeline](https://github.com/iAakash1/experimentation/tree/refactor/professional-research-layout/research/mlx_pipeline).
- Intermediate training checkpoints (`checkpoint-*`, `epoch-*`) are omitted; the selected best adapters are included.
