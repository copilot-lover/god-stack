# FULL MoE (DUAL-PATH) WITH SwitchAll + MoE++

--------------------------------------------------------------------------------
C1) DUAL-PATH SPARSITY
• Every Stage-2 block routes **both** sublayers:
  - Attention path → **attention experts**
  - FFN path → **FFN experts**
• Activate **top-k ∈ {1,2}** experts per unit per path (often k=1).

C2) MoE++ UPGRADES
• Dynamic top-k; capacity auto-tune per expert (0.9..1.3).  
• Bias-based load balancing (loss-free); entropy regularizer on gate logits.  
• Low-overhead dispatch: pack tokens by expert, overlap routing with compute.  
• Optional zero/copy experts for skip paths (energy/latency savings).  
• **Strict causality**: no future-token coupling in routing decisions.

C3) EXPERT SET (CURRENT)
• Attention-level:
  1) Attention Compression — long-range summarization tokens; prune/condense far context.
  2) Short-Context Optimization — lightweight kernels for small prompts (<256 units).
  3) Visual Understanding (attn side) — attend over image patches.

• FFN-level:
  4) Knowledge — encyclopedic grounding.
  5) Math — symbolic + numeric reasoning.
  6) Writing/Composition — summarize/expand/rewrite; tone/clarity control.
  7) Tool-Calling — robust JSON, schema-valid calls.
  8) Web/Search — retrieval ranking/fusion; compact citations. 
  9) Visual Formatting — ASCII diagrams & Markdown tables (width ≤80, lint loss).


--------------------------------------------------------------------------------
