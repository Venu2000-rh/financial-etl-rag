# Financial Data ETL Pipeline for RAG

A local Python ETL pipeline that extracts public financial data, cleans and
joins it, and flattens it into a RAG-ready gold layer — natural-language
documents optimized for semantic retrieval.

🔗 **[View the project walkthrough](https://Venu2000-rh.github.io/financial-etl-rag/)**

## What it does

Pulls real stock market data and SEC regulatory filings for a handful of
public companies, cleans and joins them into unified company records, then
transforms each record into a short natural-language document — ready to
feed directly into a RAG chatbot (see the companion
[rag-chatbot](https://github.com/Venu2000-rh/rag-chatbot) project).

## How it works

1. **Extract** — pull price history + company info via the Yahoo Finance API (`yfinance`); pull real financial filings via the SEC EDGAR Company Facts API
2. **Clean** — derive summary price metrics (52-week high/low, % change); filter SEC data down to authoritative annual (10-K) figures, handling missing/inconsistent tags
3. **Join** — merge price metrics + fundamentals + company metadata into one record per company
4. **Flatten** — convert each joined record into a natural-language paragraph — the format a retrieval system can search semantically, as opposed to a traditional normalized BI gold layer
5. **Output** — writes one `.txt` document per company to a `docs/` folder

## Tech stack

- Python, Pandas, Jupyter Notebook
- Yahoo Finance API (`yfinance`)
- SEC EDGAR API (`data.sec.gov`)

## Running it

See [setup instructions](./README_SETUP.md) *(or fold your existing setup
steps into this same README under a "## Setup" heading instead of a separate
file — see note below)* for creating a virtual environment, installing
dependencies, and configuring your SEC API User-Agent string before running
`Financial_ETL_Pipeline.ipynb`.

## Why I built this

Inspired by building Gold-layer pipelines that fed a production RAG system
in a financial-services data engineering role — this project simulates that
same flow end-to-end using public data, from raw multi-source extraction
through to a natural-language question-answering interface.
