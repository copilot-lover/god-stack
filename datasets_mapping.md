
# Dataset Mapping for GOD STACK Experts

This document maps each expert in the **GOD STACK — AU‑Net** architecture to high‑quality datasets suitable for pretraining or fine‑tuning. These datasets are curated from well‑known public collections (e.g., Hugging Face) and are intended to provide rich and diverse training signals for each specialized expert.

| Expert | High‑Quality Datasets |
| --- | --- |
| **Knowledge** | Wikipedia (English + Simple), Wikidata descriptions, BookCorpus, curated long‑form news articles, Britannica‑style reference texts |
| **Math** | GSM8K (Grade School Math 8K) – 8.5k high‑quality grade‑school math word problems requiring multi‑step reasoning【978438551273878†L1143-L1146】; SVAMP; ASDiv; MATH dataset; AQuA‑RAT |
| **Writing / Composition** | CNN/DailyMail summarization; XSum; Newsroom; GovReport; TL;DR; arXiv abstracts ↔ full papers |
| **Tool‑Calling** | ToolBench; Gorilla/APIBench; API‑Bank (including schema‑noise and no‑tool negatives) |
| **Web / Search** | BEIR benchmark (e.g., NQ, HotpotQA, FiQA); MS MARCO Passage; KILT samples |
| **Visual Formatting** | Synthetic CSV/JSON → Markdown table conversions; WikiTables; mined tables from Wikipedia; box‑drawing and grid datasets |
| **Visual Understanding** | COCO Captions; GQA; OK‑VQA; TextCaps; AI2D; DocVQA |
| **Attention Compression** | BookSum (book‑level summarization); ArXiv long‑form summarization datasets; PG19; multi‑section technical documents |
| **Short‑Context Optimization** | TriviaQA; SQuAD; Short prompts from Natural Questions; targeted queries from BEIR and MS MARCO |

These datasets provide high‑quality examples aligned to each expert’s specialization. When training or fine‑tuning GOD STACK, you can use these resources to ensure each expert is exposed to the most relevant and informative samples.
