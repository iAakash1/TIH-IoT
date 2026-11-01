# PlantDx MLX adapters (Qwen2.5-VL-7B-Instruct-4bit, QLoRA)

LoRA adapters of the knowledge-grounded PlantDx models (tomato and mango) from the Chanakya fellowship,
trained with `mlx_vlm.lora` on an Apple M4 Pro. Each folder also holds the run's `adapter_config.json`.

**These are retrained adapters, not the July 2026 files.** The July adapters (sha256 tomato 9d4b21f4…,
mango c944488f…) were no longer on the Mac. Both runs were trained again with the same code
(github.com/iAakash1/experimentation, commit `9f08d99`), the same configs
(`configs/train/qwen25vl_tomato.yaml`, `qwen25vl_mango.yaml`), `mlx` 0.31.2, `mlx-vlm` 0.6.4, and training data
identical row for row to July (split seed 20260711). `mlx_vlm.lora` takes no seed of its own, so the order of the
training examples, the LoRA initialisation and dropout differ between runs: the weights, checksums and scores
differ from July.

| File | Bytes | SHA-256 | Training | Test accuracy | Test macro-F1 | July accuracy / macro-F1 |
|---|---:|---|---|---:|---:|---|
| `qwen25vl_tomato_qlora/adapters.safetensors` | 161,529,623 | `a501137b0c5eef4346229be888f2cedc135d7e0434f74c6b136b177052860c3f` | snapshot at iteration 13,200 of 16,201, chosen on the validation split | 90.9% | 0.877 | 93.7% / 0.919 |
| `qwen25vl_mango_qlora/adapters.safetensors` | 161,529,623 | `f10dea4c14165a9002034c48094fdb0a4a6575aa299347eed39f7c6b6b6b1aa4` | final, iteration 3,600, finished 2026-11-01 07:36:48 | 86.0% | 0.891 | 82.0% / 0.811 |
| `qwen25vl_tomato_qlora/final_iteration_16201/adapters.safetensors` (earlier tomato file, kept for reference) | 161,529,623 | `a4872a5cbbf072caecb5221a613994efd935099b42b10733a8b758e920db3ee0` | final, iteration 16,201, finished 2026-11-01 06:01:29 | 86.9% | 0.847 | – |

Test sets: 910 PlantVillage tomato images and 200 MangoLeafBD images, the same held-out splits as July.

**Why the tomato file is a snapshot, not the last iteration.** Training saves the adapter every 200 iterations at
a constant learning rate, and the scores move a lot from one snapshot to the next. The final tomato adapter
(iteration 16,201; byte-identical to the iteration-16,200 snapshot) answered most healthy leaves with the single
word "A" (14 of 80 right on the test set). Fifteen different weight files (snapshots from iteration 4,000 to
16,000, and the final file) were therefore scored on the validation split (895 images, never used in training),
and the one with the highest validation
macro-F1, iteration 13,200 (92.6%, macro-F1 0.904), was evaluated once on the test set: 90.9% (827 of 910),
macro-F1 0.877, healthy leaves 67 of 80 right, one answer without a class name. It replaced the final file because
its test macro-F1 is higher, the rule written down before the test result. It is weaker than the final file on spider mites,
leaf mold, mosaic virus and target spot (F1 0.79–0.85). The mango adapter is the final one of its run and gets 8 of
25 die back images right (July 1 of 25).

Logs, the selection (scripts, validation scores, answers) and full evaluations of both tomato files:
`projects/09_plantdx_mlx_knowledge_grounded/retrained_2026-11/` in github.com/iAakash1/handover.

## Use

In a clone of github.com/iAakash1/handover, `python setup/download_models.py 09_plantdx` downloads both files
into `projects/09_plantdx_mlx_knowledge_grounded/checkpoints/<run>/` (next to the same `adapter_config.json`) and
checks the checksums (`--all` also fetches the earlier tomato file, into
`projects/09_plantdx_mlx_knowledge_grounded/retrained_2026-11/qwen25vl_tomato_qlora/final_iteration_16201/`). Then,
from that project folder on a Mac with Apple Silicon:

```bash
plantdx infer --adapter checkpoints/qwen25vl_tomato_qlora --image leaf.JPG
```
