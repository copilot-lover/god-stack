# CONTEXT WINDOW SCALING

--------------------------------------------------------------------------------
• **Primary window**: 64k pooled units (~96k “token-equiv”).  
• **Effective window**: 128k–256k via Attention Compression + ALiBi/YaRN.  
• **Beyond**: Retrieval-Augmented Memory (RAM) indexes old segments and brings back only relevant chunks.  
• KV cache: 3-bit, per-head/per-channel scales, paged (default page = 16k units).

--------------------------------------------------------------------------------
