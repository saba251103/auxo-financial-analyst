# AuxoAI Financial Analyst Chatbot

AI Engineering Take-Home Assignment Submission  
AuxoAI Hiring 2026

## Overview

This project is an intelligent financial analyst chatbot built on top of the provided Infosys financial documents.

The system is designed to behave like a grounded financial analyst rather than a keyword-based search tool.

It supports:

- Financial metric lookups
- Cross-document reasoning
- Qualitative document analysis
- Stock analytics
- Multi-source analyst-style summaries
- Follow-up conversational memory
- Intelligent structured output selection:
  - Text / markdown for quick answers
  - PDF for narrative summaries
  - Excel for data-heavy analytical outputs

The chatbot uses the **Google Gemini API** for grounded reasoning.

---

# How to Run (Google Colab)

## Step 1: Open the Notebook

Open the submitted Google Colab notebook:

```text
Untitled12_(8).ipynb
```

or upload the notebook to Google Colab manually.

---

## Step 2: Upload Required Dataset Files

Upload the following provided files into the Colab session.

Required files:

```text
infosys-ar-25.pdf
ifrs-usd-press-release_q1.pdf
ifrs-usd-press-release_q2.pdf
ifrs-usd-press-release_q3.pdf
ifrs-usd-press-release_q4.pdf
investor-sheet.xlsx
500209.csv
```

Upload using:

Google Colab left sidebar → Files → Upload

OR:

```python
from google.colab import files
files.upload()
```

---

## Step 3: Install Dependencies

Run the dependency installation cell.

---

## Step 4: Add Gemini API Key

Create a free Gemini API key:

https://aistudio.google.com/apikey

Then add it in Colab:

```python
import os
os.environ["GEMINI_API_KEY"] = "YOUR_API_KEY"
```

Or securely via Colab Secrets.

---

## Step 5: Run Notebook Cells Sequentially

Run all notebook cells from top to bottom.

This initializes:

- document ingestion
- vector database creation
- structured financial loaders
- stock analytics engine
- routing engine
- Gemini response generation
- export generation

Recommended:

```text
Runtime → Run all
```

---

# Running the Chatbot

Main function:

```python
process_query("What was FY26 revenue?")
```

Examples:

Financial lookup:

```python
process_query("What was revenue in FY26?")
```

Strategic analysis:

```python
process_query("What strategic risks were mentioned?")
```

Stock analytics:

```python
process_query("What was Infosys stock performance in FY26?")
```

Cross-document reasoning:

```python
process_query("Compare FY25 and FY26 performance and explain market sentiment")
```

Follow-up memory:

```python
process_query("What was FY26 revenue?")
process_query("Compare with FY25")
```

Hallucination check:

```python
process_query("Did Infosys acquire OpenAI?")
```

or can also use the 

# Demo Function


```python
demo_chatbot("What did management say about AI strategy?", 1)
```

Displays:

- query
- response
- sources
- export type
- generated file

---

# Generated Outputs

Reports are automatically created in the Colab working directory.

Examples:

PDF:

```text
financial_report_20260517_xxxxxx.pdf
```

Excel:

```text
financial_analysis_20260517_xxxxxx.xlsx
```

Download from:

Google Colab → Files sidebar



# Deliverables Included

This submission includes:

- Google Colab notebook
- README.md
- REFLECTION.md
