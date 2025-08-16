# EVALUATION & SHIP GATES

--------------------------------------------------------------------------------
• Language: held-out Wiki/News PPL; LAMBADA-style cloze.  
• Reasoning scaling: accuracy vs R on GSM8K-lite, 2-hop QA; monotonic to R=16.  
• Retrieval: BEIR NDCG@10, MS-MARCO MRR@10; citation presence/consistency.  
• Tool calling: JSON schema validity ≥98%; API-Bank end-to-end.  
• Visuals: VQA (GQA/OK-VQA), DocVQA samples; table/diagram lint pass ≥97%.  
• Routing health: expert-share variance within ±20%; no chronic capacity pegs.  
• Precision: PPL ≤ +5% vs fp16 after low-bit enable.

--------------------------------------------------------------------------------
