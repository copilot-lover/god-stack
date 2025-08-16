# PRECISION & KERNELS

--------------------------------------------------------------------------------
• Attention: INT4×INT4 → FP16 accum; softmax FP16; **per-head FP8 fallback** on instability (auto-revert to FP16 if needed).  
• FFN: A4.8-style low-bit path (INT4 activations/weights) with FP16 accum.  
• **Modern FP8 training** (for speed, minimal quality loss):
  - Formats: E4M3 (activations), E5M2 (weights), blockwise/per-channel scaling, dynamic rescale.
  - Sensitive ops (recurrent accum, norms, router logits) remain FP16/FP32.
• FlashAttention: **OFF by default**; autotuner may enable if attention >40% wall-time.

--------------------------------------------------------------------------------
