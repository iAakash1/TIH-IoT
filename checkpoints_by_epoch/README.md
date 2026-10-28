# Checkpoints saved during training (by epoch)

The final model of each run lives in its month folder; these are the snapshots saved along the way, kept so
every stage of training can be inspected or resumed.

| Folder | Run | What each checkpoint is |
|---|---|---|
| `tih_tomato_moreaccurate/checkpoint-656, -1312, -1908` | TIH tomato 'moreaccurate' (16 Sep 2026, ICAIN paper) | end of epoch 1, epoch 2 and epoch 2.909; checkpoint-1908 is the best one (validation macro-F1) and is the published adapter. Each has the adapter, optimizer/scheduler state and `trainer_state.json` (full loss and metric history) |
| `tih_tomato_qwen_qlora_strong/checkpoint-656, -1312, -1968` | TIH tomato 'strong' (15 Sep 2026) | end of epochs 1, 2 and 3 |
| `plantvlm_run_002_fold0/epoch-1 ... epoch-5` | PlantVLM on 150 expert captions (5 Aug 2026) | LoRA adapter after each epoch; epoch 3 was the best |
