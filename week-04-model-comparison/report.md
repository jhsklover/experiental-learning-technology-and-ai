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
**Where models agreed:** None of the records produced results where all of the models agreed. Full consistency was not achieved across all models. For each of the records, exactly two models agreed. Groq and HF Sentiment agreed for Records 1 and 4, while for Record 2, HF Sentiment and HF Zero-Shot agreed. For Record 3, HF Sentiment and Groq agreed, while for Record 5, Groq and HF Zero-Shot Agreed.

**Where models disagreed:** All of the records produced a disagreement. For the first record, HF Zero-Shot disagreed with the other two models by stating that the record was a routine transaction, while HF Sentiment and Groq classified the record as negative and high risk, respectively. For the second record, both Hugging Face models disagreed with Groq, which classified the record as routine. Sentiment and Groq classified the third record as negative and critical, while Zero-Shot stated the record was a routine transaction. The fourth record saw Groq and Sentiment disagreeing with Zero-Shot, which stated the record was routine, while the other two models classified the record as negative and high risk, respectively. The fifth record saw Groq and Zero-Shot agreeing that the record was a routine transaction, while the Sentiment model labelled the record as negative. The reason for these inconsistent results is likely because the models all analyze the records in different ways: the sentiment analyzer picks up on emotional tones and what the text evokes; it is very black-or-white with its positive or negative classifications and does not actually analyze fraud risk. Zero-Shot analyzes the text based on pre-provided labels, which also limits the results to a small dataset, allowing for inaccuracies. Groq relies more on general reasoning, and provides outputs which are most consistent with human analysis.

**Most accurate model overall:** Based on the results, Groq LLM provided the most accurate results. Based on the content of each record, Groq's analysis was reliable for all five of the models. I would also use the NER Entities model based on the fact that it can extract valuable information including locations as seen for the third alert.

**Fastest/most practical:** My experience working with the four models is that HF Sentiment, HF Zero-Shot, and Groq LLM were all significantly faster than HF NER. Groq LLM processed the records incredibly fast and was able to produce accurate results, so it seems to be the most practical. HF Sentiment is fast, but is not very effective, so it is not practical for analysis. HF NER was slow to even sift through five records, so it would be difficult to use at scale. HF Zero-Shot was also quite fast, and could have the potential to be more accurate with more labels.

## Recommended Models for My Capstone Component 
**Component:** Transaction Ingestion Workflow
**Primary model:** Groq Llama 3.1 8B — This model is both fast and produces human-like analysis that is both logical and explanatory.
**Secondary model (if applicable):** N/A
**Rejected models and why:**
- Hugging Face Sentiment: This model does not produce expansive or accurate results, as it is designed to find the sentiment. Positive or negative does not truly encompass the alert's content, making it unsuitable.
- Hugging Face Zero-Shot: This model was unable to accurately determine whether the alerts were fraudulent transactions or routine transactions. The model only provided one out of five accurate results, meaning that it is unsuitable.
- Hugging Face NER: This model is significantly slower than the other models, and would not be suitable for larger datasets. Additionally, while it does pick out entities, it only identified them for one out of the five alerts, giving it a 20% rate of finding an entity based on the provided data.
## Failure Cases and Limitations 
The most jarring result was for record #2, where the input text was "Monthly salary deposit of $4,200 processed — expected amount from known employer", and HF Zero-Shot classified the text as fraudulent activity. Record #2's input text is very clearly standard, as it represents a known employer depositing a regular monthly salary into the holder's account. Furthermore, Zero-Shot stated that "Loan application submitted with same address as 8 other recent applications — different applicant names" represented a routine transaction, which is also very inaccurate given the suspicious activity explained in the message. Overall, there were no records where all three models failed completely, but record #2 had two out of three models providing inaccurate results with HF Sentiment also classifying the message as negative.

## Next Steps 

Given that the Hugging Face sentiment and zero-shot models did not produce accurate results across all records, those would not be suitable to use for data analysis. I would expand upon this experiment by testing a larger collection of records, with a more expansive group of classifications, since results can fall outside of "fraudulent activity", "routine transaction", and "requires review": there could be options for neutral but leaning toward negative or positive. I think that HF Zero-Shot has potential, but the model used provided inaccurate results; I'd like to replace it with a different model, such as MoritzLaurer/DeBERTa-v3-base-mnli, or roberta-large-mnli.
