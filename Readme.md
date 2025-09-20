# PMC-Multi-Agent-Search-Summarization

## Overview
This project implements a lightweight multi-agent workflow for analyzing biomedical literature from the **PubMed Central Open Access (PMC OA Comm)** dataset. The workflow is designed for Sanofi R&D teams (or similar research groups) who need to quickly retrieve, summarize, and structure scientific articles to support discovery.

The workflow includes:
- **Retriever Agent**: Finds relevant articles given a user query.
- **Summarizer Agent**: Generates concise 2–3 sentence summaries with keywords.
- **Verifier Agent (optional)**: Classifies summaries into research themes (e.g., Deep Learning, Clinical Trial, Traditional Methods).

The project is implemented as a Jupyter Notebook (`notebook.ipynb`).

---

## Dataset
We use the **PMC OA Comm dataset** hosted on Amazon S3:
- Bucket: `s3://pmc-oa-opendata/oa-comm/`
- File list (CSV): `s3://pmc-oa-opendata/oa_comm/txt/metadata/csv/oa_comm.filelist.csv`
- Full-text files: `s3://pmc-oa-opendata/oa_comm/txt/all/PMID.txt`

The notebook works with a **subset (< 100 documents)** of articles for demonstration.

---

## Installation & Setup
Clone the repository:
```bash
git clone https://github.com/your-username/PMC-Multi-Agent-Search-Summarization.git
cd PMC-Multi-Agent-Search-Summarization
```

Install dependencies (preferably in a virtual environment):
```bash
pip install -r requirements.txt
```

Required packages include:
- `pandas`
- `transformers`
- `sentence-transformers`
- `scikit-learn`

---

## Usage
Launch the notebook:
```bash
jupyter notebook notebook.ipynb
```

Inside the notebook, follow these sections:
1. **Setup & Data Access** – Connect to S3 and load subset of articles.
2. **Retriever Agent** – Embed queries and retrieve top-K relevant documents.
3. **Summarizer Agent** – Generate summaries from abstracts.
4. **Verifier Agent (optional)** – Classify summaries into themes.
5. **Report Generation** – Output structured results.

### Example Queries
1. Adverse events with mRNA vaccines in pediatrics
2. Transformer-based models for protein folding
3. Clinical trial outcomes for monoclonal antibodies in oncology

---

## Design Choices & Tradeoffs
- **CPU-Friendly Models**: Used lightweight Hugging Face models (T5-small, BART-base, DistilBERT, MiniLM) for accessibility.
- **Subset Data**: Limited to < 100 articles to keep runtime reasonable.
- **Optional Verifier**: Keeps pipeline flexible (skip for speed, include for deeper analysis).

---

## Deliverables
- `notebook.ipynb` – Complete implementation of the workflow.
- `README.md` – This file, with instructions and project details.

---

## Future Improvements
- Scale retrieval to larger subsets using FAISS/Annoy.
- Fine-tune summarization for biomedical domain.
- Add richer visualization of results (e.g., word clouds, graphs).
