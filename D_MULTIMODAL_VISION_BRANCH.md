# MULTIMODAL VISION BRANCH

--------------------------------------------------------------------------------
• Encoder: SigLIP/EVA-ViT-style; patch size 14–16; INT4/FP8 quantized outputs.  
• Fusion: at Stage-1, patches → visual units concatenated with text units.  
• Routing: Visual Understanding expert activates only when images present.  
• Tasks: VQA, scene description, diagram/table read (OCR-lite layout cues).  
• Optionally pass visual entities to Graph-Aware attention (if enabled later).

--------------------------------------------------------------------------------
