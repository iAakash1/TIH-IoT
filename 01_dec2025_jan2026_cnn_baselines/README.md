# 01 · December 2025 – January 2026: foundation tasks and CNN baselines

**In short:** we learned image processing and preprocessing (December tasks from TIH), then trained CNN
classifiers on PlantVillage tomato leaves (10 classes: 9 diseases + healthy).

## What was done

**December 2025: TIH foundation tasks**
- *Week 1 (2–5 Dec):* basic image operations (read, resize, crop, rotate, flip, colour spaces, blur,
  interpolation, Sobel/Canny, sharpening), each written with OpenCV and again from scratch in NumPy, with
  timing comparisons.
- *Week 2 (8–12 Dec):* preprocessing for training (resize, normalise, crop, augment) and image-quality checks
  for prediction (blur, brightness, contrast, noise, resolution, format).
- *Week 3 (15–19 Dec):* CNN theory (layers, activations, losses), then a CNN trained from scratch on PlantVillage.

**January 2026: transfer learning**
- MobileNetV2, EfficientNetB3 and ConvNeXt-Tiny (Keras, ImageNet weights, two-stage fine-tuning).
- ConvNeXt-Tiny in PyTorch on the GPU workstation.
- Crop validation: a check that rejects images that are not crop leaves (green-pixel ratio + embedding similarity).

## Folders

| Folder | What it is |
|---|---|
| `cottoncrop_repo_snapshot/` | Copy of [iAakash1/CottonCrop](https://github.com/iAakash1/CottonCrop) without its dataset. `preprocessing/` is the Week-2 module; `validation/` the crop check; `model/` the Keras models. |
| `keras_pipeline_kamaaksha/` | Custom CNN (`model/train_cnn.py`), transfer-learning scripts, final `.keras` models, `config.py` (full pipeline: validate → preprocess → predict). |
| `pytorch_convnext/` | Notebooks (data split, ConvNeXt training), the trained model `models/convnext_tomato_best.pth`, and `splits/split_70_15_15.csv` (the exact image list used for train/val/test). |

## Results (evaluation reports in [`../evaluation_reports_oct2026`](../evaluation_reports_oct2026))

| Model | Evaluated on | Accuracy | Macro-F1 |
|---|---|---:|---:|
| Custom CNN, 32×32 input | tomato test split, 2,411 images* | 98.51% | 0.9830 |
| MobileNetV2 (Keras) | held-out 20% validation, 3,198 images | 90.90% | 0.8939 |
| EfficientNetB3 (Keras) | same | 93.59% | 0.9275 |
| ConvNeXt-Tiny (Keras) | same | 96.15% | 0.9507 |
| ConvNeXt-Tiny (PyTorch) | test split, 2,411 images | **99.92%** | 0.9991 |

\* Indicative only: the CNN's own 80/20 split was drawn on a Mac and could not be rebuilt, so these test images largely overlap its training data.

PlantVillage photos are clean lab images, so very high accuracy here does not guarantee field performance.
This is why the later work moved to Vision-Language Models and to the TIH tomato dataset.
