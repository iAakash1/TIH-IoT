# PlantDx MLX adapters (Qwen2.5-VL-7B-Instruct-4bit, QLoRA)

LoRA adapters of the knowledge-grounded PlantDx models (tomato and mango) from the Chanakya fellowship,
trained with `mlx_vlm.lora` on an Apple M4 Pro. Each folder also holds the run's `adapter_config.json`.

**These are retrained adapters, not the July 2026 files.** The July adapters (sha256 tomato 9d4b21f4…,
mango c944488f…) were no longer on the Mac. Both runs were trained again with the same code
(github.com/iAakash1/experimentation, commit `9f08d99`), the same configs
(`configs/train/qwen25vl_tomato.yaml`, `qwen25vl_mango.yaml`), seed 20260711, `mlx` 0.31.2, `mlx-vlm` 0.6.4,
and training data identical row for row to July. GPU training is not bit-for-bit reproducible, so the
weights and checksums differ from July.

| File | Bytes | SHA-256 | Training finished | Test accuracy (retrained) | Macro-F1 (retrained) | July accuracy / macro-F1 |
|---|---:|---|---|---:|---:|---|
| `qwen25vl_tomato_qlora/adapters.safetensors` | 161,529,623 | `a4872a5cbbf072caecb5221a613994efd935099b42b10733a8b758e920db3ee0` | 2026-11-01 06:01:29 | 86.9% | 0.847 | 93.7% / 0.919 |
| `qwen25vl_mango_qlora/adapters.safetensors` | 161,529,623 | `f10dea4c14165a9002034c48094fdb0a4a6575aa299347eed39f7c6b6b6b1aa4` | 2026-11-01 07:36:48 | 86.0% | 0.891 | 82.0% / 0.811 |

Test sets: 910 PlantVillage tomato images and 200 MangoLeafBD images, the same held-out splits as July.

## Use

Put each `adapters.safetensors` next to its `adapter_config.json` in
`projects/09_plantdx_mlx_knowledge_grounded/checkpoints/<run>/` of github.com/iAakash1/handover, then, on a Mac
with Apple Silicon:

```bash
plantdx infer --adapter checkpoints/qwen25vl_tomato_qlora --image leaf.JPG
```
