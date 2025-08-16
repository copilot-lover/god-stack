# DATASETS (ENGLISH-ONLY) & EXPERT MAPPING

--------------------------------------------------------------------------------
Backbone mix (all experts see a share unless constrained):
• Wikipedia (full + Simple), curated long-form news/editorials, high-quality reference sites.

Per-expert adds:
• Knowledge — Wikidata descriptions, Britannica-style, textbooks/explainers.  
• Math — GSM8K, SVAMP, ASDiv, MATH, AQuA-RAT, synthetic arithmetic & table-math, light physics word-problems.  
• Writing/Composition — CNN/DM, XSum, Newsroom, GovReport, TL;DR, arXiv abs↔full; curated style corpora; instruction pairs for concision/expansion/tone.  
• Tool-Calling — ToolBench, Gorilla/API-Bench, API-Bank + schema-noise and no-tool negatives.  
• Web/Search — BEIR subsets (NQ, HotpotQA, FiQA), MS-MARCO Passage, KILT samples.  
• Visual Formatting — synthetic CSV/JSON→table; mined Wiki tables; box-drawing/trees/grids (with lint-based structure loss).  
• Visual Understanding — COCO Captions, GQA, OK-VQA, TextCaps, AI2D, DocVQA-like layout samples.  
• Attention Compression — book-level/ArXiv multi-section with summary-matching objectives.  
• Short-Context Optimization — short prompts (<128 units) from QA/search/tool triggers with latency-weighted loss.

--------------------------------------------------------------------------------
