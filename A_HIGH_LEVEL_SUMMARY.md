# HIGH-LEVEL SUMMARY

--------------------------------------------------------------------------------
• Input as raw bytes → adaptive “units” (no BPE).  
• AU-Net 3-stage hierarchy with a **recurrent latent reasoning** core that you can turn up at test time (R loops per next-unit).  
• **Full MoE** in both attention and FFN (dual-path sparsity) using **SwitchAll** routing; **MoE++** load balancing and low-overhead dispatch.  
• Experts: Knowledge, Math, Writing/Composition, Tool-Calling, Web/Search, Visual Formatting (ASCII/tables), Visual Understanding (images), Attention Compression, Short-Context Optimization.  
• Precision: INT4×INT4→FP16 accum, **headwise FP8 fallback**, **3-bit KV**.  
• Context scaling: Long-Context Compression + ALiBi/YaRN + Retrieval-Augmented Memory (RAM).  
• **No speculative decoding.** Use MTP/MUP(4) auxiliary prediction only.

--------------------------------------------------------------------------------
