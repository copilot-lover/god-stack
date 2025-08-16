# REFERENCES (for this spec’s design choices)

--------------------------------------------------------------------------------
• DeepNorm / DeepNet (residual scaling for deep decoders)  
• Scaling Up Test-Time Compute with Latent Reasoning (recurrent depth approach)  
• MoE++ (routing/dispatch & load-balance improvements)  
• SwitchAll / SwitchHead (dual-path MoE for attention + FFN)  
• FP8 mixed-format training practices (E4M3/E5M2, blockwise scaling)  
• Context scaling via ALiBi/YaRN, compression, and retrieval memory  
• Multimodal vision encoders (SigLIP/EVA-ViT families), VQA/DocVQA datasets
--------------------------------------------------------------------------------

### Attention Variants (updated spec with MQA/MHLA)
- **MHA (Multi-Head Attention):** full multi-heads; best quality on short contexts (≤8k units).
- **GQA (Grouped-Query Attention):** Q heads share K/V in groups (e.g., 4:1) for mid-length contexts (8k–64k units); 4× KV memory savings.
- **MQA (Multi-Query Attention):** all Q heads share a single K/V head for very long contexts (≥64k units); ~32× KV savings.
- **Linear Attention (MHLA):** feature-map based kernel (e.g., FAVOR+) with O(n) memory/time; fallback for extreme contexts.
- **Policy:** automatic selection:
  - Short (≤8k units): **MHA**
  - Medium (8k–64k units): **GQA**
  - Long (≥64k units): **MQA**
  - Extreme (beyond RAM budget): **Linear**
- **KV cache:** integrates with 3-bit KV paging; fewer KV heads → fewer pages → lower bandwidth.
- **Telemetry:** logs variant, KV head count, pages touched, and wall-time per step.
