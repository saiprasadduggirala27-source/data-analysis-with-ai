# From IMF Country Report to Dashboard: An LLM Pipeline for Vietnam

**IMF Country Report No. 25/283 — Vietnam: 2025 Article IV Consultation**


**Programme:** MSc Data Science  
**University:** University of Hertfordshire

---

## 1. Project Overview

This project develops an AI-assisted pipeline to analyse the International Monetary Fund's (IMF) 2025 Article IV Consultation report for Vietnam.

The project combines Python, Gemini and Retrieval-Augmented Generation (RAG) to extract economic information, generate summaries, identify financial stability themes, retrieve evidence-based answers and visualise findings through a dashboard.

The main objective is to demonstrate how Large Language Models (LLMs) can support macroeconomic and financial stability analysis while maintaining reliability through source verification, numerical validation and human evaluation.

## 2. IMF Report

**Source document:** Vietnam: 2025 Article IV Consultation—Press Release; Staff Report; and Statement by the Executive Director for Vietnam.

- Institution: International Monetary Fund
- Country: Vietnam
- Report number: 25/283
- Publication year: 2025

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Data processing and analysis |
| Google Colab | Notebook execution environment |
| Gemini API | Summarisation, extraction and question answering |
| PyMuPDF | PDF text extraction |
| Pandas | Data manipulation |
| Matplotlib | Data visualisation |
| Sentence Transformers | Text embeddings |
| MiniLM | Semantic embedding model |
| BGE | Semantic embedding model |
| FAISS | Vector indexing and retrieval |
| JSON | Structured output storage |

## 4. Project Workflow

The project consists of four main tasks and additional experiments.

### Task 1 – PDF Processing and Summarisation

- Extract text from the Vietnam IMF PDF.
- Clean and normalise the extracted text.
- Identify the main report sections.
- Divide the document into overlapping token-based chunks.
- Use Gemini to generate section summaries and an executive summary.
- Evaluate summaries for consistency, completeness and factual alignment.

### Task 2 – Thematic Extraction and Financial Indicators

The notebook analyses seven financial stability themes:

1. Inflation and Prices
2. Interest Rates and Credit
3. Housing and Real Estate
4. Banking Capital and Liquidity
5. Sovereign Debt
6. Labour Market Dynamics
7. Systemic Financial Risk

It also identifies macroeconomic strengths and vulnerabilities, extracts financial indicators, generates time-series data and validates structured JSON outputs.

### Task 3 – Retrieval-Augmented Generation (RAG)

- Generate embeddings using MiniLM and BGE.
- Create FAISS vector indexes.
- Retrieve relevant report passages.
- Generate answers grounded in retrieved evidence.
- Validate chunk citations.
- Evaluate retrieval using Hit@1, Hit@k and MRR@10.

### Extension 1 – Multi-Query RAG

Gemini generates alternative formulations of each question. The resulting retrieval rankings are combined using Reciprocal Rank Fusion (RRF).

The experiment compares standard single-query retrieval with Multi-Query RAG to investigate improvements in retrieval coverage, faithfulness and answer completeness.

### Extension 2 – Gemini Model Benchmarking

Different Gemini model variants are compared using structured extraction tasks.

The experiment considers:
- JSON schema compliance.
- Numerical accuracy.
- Response latency.
- LLM judge evaluation.

### Task 4 – Data Visualisation and Dashboard

Pandas is used to transform extracted data into suitable formats, while Matplotlib produces visualisations covering:

- Financial stability theme distribution.
- Inflation and credit growth.
- Banking-sector resilience.
- Macroeconomic and fiscal developments.
- Retrieval performance.
- LLM evaluation results.

## 5. Key Vietnam Economic Indicators

The project examines important indicators reported in the IMF assessment.

| Indicator | Value | Period |
|---|---:|---|
| Real GDP growth forecast | 6.5% | 2025 |
| Headline CPI inflation forecast | 3.4% | 2025 |
| Non-performing loan ratio | 5.3% | March 2025 |
| Unemployment rate projection | 2.3% | 2025 |
| Tier 1 capital ratio | 10.6% | 2024 Q2 |
| Public and publicly guaranteed debt | 31.3% of GDP | 2024 |

**Note:** The central bank policy-rate indicator uses a fallback value in the notebook because an exact comparable figure was not identified. The fallback is not an actual policy rate.

## 6. Installation and Execution

### Option 1 – Google Colab

1. Open the project notebook in Google Colab.
2. Upload the Vietnam IMF Country Report PDF.
3. Ensure the PDF path matches the configured notebook path:

   `/content/1934-7685-002.2025.issue-283-en.pdf`

4. Add your Gemini API key to Colab Secrets using the name:

   `GEMINI_API_KEY`

5. Enable access to the secret when prompted.
6. Select **Runtime → Run all** to execute the notebook.

### Option 2 – Local Environment

Clone the repository:

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd <YOUR_PROJECT_FOLDER>
```

Install the required dependencies:

```bash
pip install pymupdf pandas numpy matplotlib
pip install sentence-transformers faiss-cpu
pip install google-genai
```

Configure your Gemini API key as an environment variable and update the PDF path in the notebook before execution.

**Note:** The notebook may require additional dependencies depending on the cells and runtime environment.

## 7. Output Files

The notebook saves generated results in the `vietnam_imf_outputs` directory.

Expected outputs include:

- Cleaned report text.
- Section summaries.
- Executive summary.
- Financial stability theme counts.
- Extracted financial indicators.
- Time-series data.
- Structured JSON files.
- RAG retrieval and evaluation results.
- Multi-Query RAG comparison results.
- Dashboard visualisations.

The exact files depend on which notebook cells complete successfully.

## 8. Key Findings

The analysis highlights Vietnam's strong economic growth outlook, with real GDP growth projected at 6.5% in 2025 and period-average inflation forecast at 3.4%.

However, the IMF report also identifies financial stability concerns relating to rapid credit growth, corporate indebtedness, real estate vulnerabilities, corporate bond maturities and banking-sector liquidity.

The analysis emphasises the importance of stronger banking-sector capital and liquidity buffers, improved stress testing, effective supervision and financial-sector resilience.

The RAG experiments also demonstrate that embedding-model selection and alternative question formulations can influence retrieval performance.

## 9. Limitations and Validation

The project recognises several limitations:

- PDF extraction can affect table formatting and numerical interpretation.
- LLMs may confuse similar financial indicators.
- Retrieval performance depends on chunking and embedding quality.
- Citation validity does not guarantee factual correctness.
- LLM judge scores are not a substitute for human evaluation.
- Some extracted time-series values require manual verification.

Python validation, source quotation matching, citation checks and human review are used to improve reliability.

## 10. Conclusion

This project demonstrates how AI and Python can be combined to analyse an IMF country report and transform its contents into structured economic information and dashboard visualisations.

It integrates document processing, LLM summarisation, thematic analysis, financial indicator extraction, RAG-based question answering and model evaluation.

The project also demonstrates the importance of source verification and human oversight when applying AI to economic and financial analysis.

## 11. 
References

International Monetary Fund (2025). Vietnam: 2025 Article IV Consultation. IMF Country Report No. 25/283.

Reimers, N. and Gurevych, I. (2019). Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks.

Johnson, J., Douze, M. and Jégou, H. (2019). Billion-scale similarity search with GPUs.

Google Gemini API Documentation.

FAISS Documentation.

Hugging Face Sentence Transformers Documentation.

