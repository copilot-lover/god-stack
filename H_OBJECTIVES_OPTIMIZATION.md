# OBJECTIVES & OPTIMIZATION

--------------------------------------------------------------------------------
• Main: AR next-unit + **MTP/MUP(4)** (weights: 1.0/0.7/0.5/0.3).  
• Aux: Stage-1 next-unit (0.10), Stage-0 next-byte (0.05).  
• SwitchAll/MoE++ losses: load-balance (bias-based, no harmful aux grads), gate-entropy reg, capacity penalty.  
• Optimizer/schedule: AdamW, cosine LR, grad clip, grad checkpointing, microbatch autotune.  
• Quant-aware path:
  1) Pretrain (bf16/fp16) to stability
  2) Enable INT4/FP8 w/ calibration on held-out
  3) Recovery fine-tune 5–20k steps (small LR) to restore PPL.

--------------------------------------------------------------------------------
