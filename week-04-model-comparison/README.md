# Week 4: Model Comparison 

Tested 4 AI models on 5 fraud investigation text samples to evaluate their suitability for the Transaction Ingestion Workflow component of our Financial Fraud Detection System capstone.

## Models Tested
- HF Sentiment (distilbert-sst-2) 
- HF Zero-Shot (bart-large-mnli)
- HF NER (bert-large-NER)
- Groq Llama 3.1 8B

## Finding 
Recommended HF NER (bert-large-NER) and Groq Llama 3.1 8B for the Transaction Ingestion Workflow because they were the most accurate during the data analysis, and provided insight toward the data's important entities and properties of each alert, respectively.
See `report.md` for full analysis.
