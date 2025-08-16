# ARCHITECTURE (AU-Net)

--------------------------------------------------------------------------------
B1) STAGES
• Stage-0 Byte Encoder
  - Tiny AR byte stack (4× 384-d) with conv stem + RoPE → byte embeddings.
  - Aux loss: next-byte (weight 0.05).

• Stage-1 Pooled Units
  - Adaptive pooling window: 2–16 bytes per unit (streaming-safe boundary rules).
  - 6× 768-d Transformer to form stable “word-ish” units.
  - Aux loss: next-unit (weight 0.10).

• Stage-2 Global LM (decoder-only)
  - **DeepNorm** Transformer, 36 “logical” layers split as:
    - Prelude: 6 layers
    - Core (shared): 4 layers, **iterated R times** per next-unit
    - Coda: 4 layers
  - **Recurrent latent reasoning loop** replaces CoT:
    - Inference knob: R ∈ {0,4,16,32} (cap 64) with early-halt on convergence (Δ‖h‖/‖h‖ < 1e-3 for 3 steps).
    - Training: sample R from heavy-tailed (lognormal-Poisson), TBPTT through last K=6 steps, inject input embedding e at *every* iteration for stability.
  - **MTP/MUP(4)**: 4 auxiliary heads predict next 1..4 units with loss weights [1.0, 0.7, 0.5, 0.3].
  - **Speculative decoding: OFF.**

B2) DEEPNORM CONSTANTS (decoder-only)
• Let M = Prelude + Coda + R_max×CoreL, with CoreL=4.
  - If R_max=16 → M=6 + 4·16 + 4 = 74 ⇒ α=(2M)^(1/4)=3.49, β=(8M)^(-1/4)=0.20
  - If R_max=32 → M=6 + 4·32 + 4 = 138 ⇒ α=4.08, β=0.17
• Apply Post-style residual:
  y = LN( α·x + F(x) ), with init gains:
  - FFN/V-proj/Out-proj: XavierNormal(gain=β)
  - Q-proj/K-proj: gain=1
• Keep router params and norms in FP16/FP32 (unscaled).

--------------------------------------------------------------------------------
