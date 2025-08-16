# TRAINING PLAN (PHASES)

--------------------------------------------------------------------------------
1) Pretrain backbone (bf16/fp16), English-only: Wikipedia + curated long-news + reference.  
2) Introduce experts progressively (SwitchAll+MoE++ already on), small gate-entropy reg, bias LFB.  
3) Enable low-bit kernels (INT4/FP8), calibrate per-layer scales; **recover** 5–20k steps.  
4) Light SFT for formatting, tool JSON, style control; tiny RL for budgeted reasoning (reward correctness + low R unless needed).  
5) Vision branch fine-tune on VQA/DocVQA.

--------------------------------------------------------------------------------
