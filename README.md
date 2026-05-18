# 📂 Thesis Evaluation Data — RAG Queries, Gold Labels & Datasets

> **ENSSEA Master's Thesis** | Si Tayeb Houari | 2025–2026  
> Evaluation resources for the Hybrid Multilingual RAG + Sentiment pipeline.

---

## 📁 Repository Structure

```
thesis-evaluation-data/
│
├── 📁 rag_evaluation/
│   ├── rag_eval_queries.csv        # Evaluation queries (AR / FR / EN)
│   ├── gold_labels.csv             # Relevance judgments per query
│   └── rag_eval_results.csv        # Model output vs gold labels
│
├── 📁 sentiment_evaluation/
│   ├── sentiment_test_set.csv      # Held-out sentiment evaluation set
│   └── ensemble_predictions.csv   # Ensemble model predictions
│
├── 📁 forecasting_data/
│   ├── algeria_macro_indicators.csv  # GDP, inflation, unemployment, FX
│   └── yearly_sentiment_index.csv    # Annual sentiment scores (2000–2025)
│
├── 📁 dataset_samples/
│   ├── labr_sample.csv             # Sample from LABR (Arabic sentiment)
│   └── sentiment140_sample.csv     # Sample from Sentiment140
│
└── README.md
```

---

## 📊 RAG Evaluation Format

### `rag_eval_queries.csv`

| Column | Description | Example |
|--------|-------------|---------|
| `query_id` | Unique query identifier | Q001 |
| `query` | The evaluation question | "What was Algeria's inflation rate in 2020?" |
| `language` | Query language | AR / FR / EN |
| `query_type` | Type of question | Factual / Analytical / Comparative |
| `source_doc` | Source document name | IMF_Report_2020.pdf |
| `relevant_page` | Page(s) containing the answer | 12, 13 |
| `notes` | Additional context | Covers COVID-19 period |

---

### `gold_labels.csv`

| Column | Description | Example |
|--------|-------------|---------|
| `query_id` | Links to `rag_eval_queries.csv` | Q001 |
| `chunk_id` | Relevant chunk identifier | chunk_045 |
| `relevance_score` | 0 = not relevant, 1 = relevant, 2 = highly relevant | 2 |
| `answer_span` | Expected answer text (paraphrased) | "Inflation reached 2.4% in 2020…" |
| `doc_section` | Document section title | "3.2 Price Stability" |

---

## 📈 Yearly Sentiment Index Data

### `yearly_sentiment_index.csv`

| Column | Description |
|--------|-------------|
| `year` | Year (2000–2025) |
| `finbert_score` | FinBERT sentiment score |
| `xlm_score` | XLM-RoBERTa sentiment score |
| `lexicon_score` | Economic lexicon polarity score |
| `econ_ft_score` | Fine-tuned economic model score |
| `ensemble_score` | Final weighted ensemble score |
| `label` | Positive / Neutral / Negative / Highly Negative |
| `event` | Associated economic event (if any) |

---

## 🔗 External Datasets Used

| Dataset | Language | Size | License | Link |
|---------|----------|------|---------|------|
| LABR (Large-Scale Arabic Book Reviews) | Arabic | 63,000 reviews | Research | [HuggingFace](https://huggingface.co/datasets/mohamedadaly/labr) |
| Sentiment140 | English | 1.6M tweets | Open | [HuggingFace](https://huggingface.co/datasets/stanfordnlp/sentiment140) |
| Bank of Algeria Annual Reports | AR / FR | 2000–2024 | Public | [bank-of-algeria.dz](https://www.bank-of-algeria.dz) |
| IMF Article IV Consultations (Algeria) | EN / FR | 2000–2024 | Public | [imf.org](https://www.imf.org) |
| World Bank Open Data (Algeria) | — | Macro indicators | Open | [data.worldbank.org](https://data.worldbank.org) |

---

## 📋 RAG Evaluation Metrics

The evaluation pipeline measures:

| Metric | Description |
|--------|-------------|
| **Precision@k** | Fraction of top-k retrieved chunks that are relevant |
| **Recall@k** | Fraction of relevant chunks retrieved in top-k |
| **MRR** | Mean Reciprocal Rank — position of first relevant result |
| **NDCG@k** | Normalized Discounted Cumulative Gain |
| **Faithfulness** | LLM-as-judge: is the answer grounded in retrieved context? |
| **Answer Relevance** | Does the answer actually address the query? |

---

## ⚠️ Access & Usage Notes

- All data in this repository is used strictly for **academic research purposes**.
- External datasets (LABR, Sentiment140) are linked by reference only; download them from their original sources.
- Official reports (Bank of Algeria, IMF) are publicly available documents.
- Gold labels were manually annotated by the thesis author.

---

## 🔗 Related Repositories

| Repo | Description |
|------|-------------|
| [thesis-multilingual-rag-sentiment](https://github.com/YOUR_USERNAME/thesis-multilingual-rag-sentiment) | Main thesis repository |
| [rag-sentiment-app](https://github.com/YOUR_USERNAME/rag-sentiment-app) | Deployed web application |
| [thesis-notebooks](https://github.com/YOUR_USERNAME/thesis-notebooks) | Analysis notebooks |

---

*© 2026 Si Tayeb Houari — ENSSEA Master's Thesis*
