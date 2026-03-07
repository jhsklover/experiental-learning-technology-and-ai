# Model Comparison Report — Week 4 

**Name:** Jack Sklover 

**Date:** 03/08/2026

**Capstone Project:** Financial Fraud Detection System

**My Component:** Transaction Ingestion Workflow and Dashboard

## Test Setup 

**Input dataset:** 5 fraud investigation text samples covering: 
- 2 clearly concerning/high-severity records
- 1 ambiguous/edge case record
- 2 routine/benign records

**Models tested:**
week-04-lab-instructions.md
1. distilbert-base-uncased-finetuned-sst-2-english (sentiment) 
2. facebook/bart-large-mnli (zero-shot classification) 
3. dslim/bert-large-NER (named entity recognition) 
4. Groq Llama 3.1 8B (LLM classification) 

**Evaluation criteria:** label accuracy, confidence score, speed, ease of 
integration in n8n 

## Results Summary 
| Record | Sentiment | Zero-Shot | NER Entities | Groq | 
|--------|-----------|-----------|-------------|------| 
| 1 | NEGATIVE (0.9812) | routine transaction | N/A | HIGH | 
| 2 | NEGATIVE (0.9544) | fraudulent activity | N/A | ROUTINE | 
| 3 | NEGATIVE (0.9100) | routine transaction | "Miami" | CRITICAL | 
| 4 | NEGATIVE (0.9936) | routine transaction | N/A | HIGH | 
| 5 | NEGATIVE (0.9946) | routine transaction | N/A | ROUTINE | 
## Analysis 
**Where models agreed:** None of the records produced results where all of the models agreed. Full consistency was not achieved across all models.
**Where models disagreed:** [Which records got different classifications? What 
might explain the difference?] 
**Most accurate model overall:** [Based on your 5 records, which model gave the 
most sensible results?] 
**Fastest/most practical:** [Which model would be easiest to use at scale?] 
## Recommended Models for My Capstone Component 
**Component:** [Your capstone component name] 
**Primary model:** [Name] — [1 sentence: why this one for your task] 
**Secondary model (if applicable):** [Name] — [1 sentence: what role it plays] 
**Rejected models and why:**- [Model name]: [1-2 sentences on why it's not the right fit] 
## Failure Cases and Limitations 
[Describe at least one case where a model gave a wrong or surprising result. 
What does this tell you about using this model in production?] 

## Next Steps 

Given that the Hugging Face sentiment and zero-shot models did not produce accurate results across all records, those would not be suitable to use for data analysis. I would expand upon this experiment by testing a larger collection of records, with a more expansive group of classifications, since results can fall outside of "fraudulent activity", "routine transaction", and "requires review": there could be options for neutral but leaning toward negative or positive. I think that HF Zero-Shot has potential, but the model used provided inaccurate results; I'd like to replace it with a different model, such as MoritzLaurer/DeBERTa-v3-base-mnli, or roberta-large-mnli.
