# Week 5 Report: AutoML Training & Fine-Tuned Model Evaluation 

**Name:** Jack Sklover

**Date:** 03/22/2026

**Capstone Project:** Financial Fraud Detection System

**My Component:** Transaction Ingestion Workflow

## Part A: Teachable Machine Training 
### Training Setup
- **Task:** Forged vs. Authentic image classification
- **Training images per class:** 26
- **Test images per class:** 5
- **Total training time:** 43 seconds
 
### Test Results 
| # | Actual Class | Predicted Class | Confidence | Correct? | 
|---|--------------|-----------------|------------|----------| 
| 1 | Forged | Authentic | 0.75 | No | 
| 2 | Forged | Forged | 1.00 | Yes | 
| 3 | Forged | Forged | 1.00 | Yes | 
| 4 | Forged | Authentic | 0.61 | No | 
| 5 | Forged | Forged | 0.99 | Yes | 
| 6 | Authentic | Forged | 0.71 | No | 
| 7 | Authentic | Authentic | 1.00 | Yes | 
| 8 | Authentic | Authentic | 1.00 | Yes | 
| 9 | Authentic | Authentic | 1.00 | Yes | 
| 10 | Authentic | Authentic | 0.99 | Yes | 

### Confusion Matrix 
|  | Predicted: Forged | Predicted: Authentic | 
|---|---|---| 
| **Actual: Forged** | TP = 3 | FN = 2 | 
| **Actual: Authentic** | FP = 1 | TN = 4 | 


### Calculated Metrics
- **Accuracy:** 70%
- **Precision:** 75%
- **Recall:** 60%
- **F1 Score:** 66.67% 

### Interpretation 
My model is better at precision, as it has a score of 75% compared to the recall score of 60%. The model allowed two fraudulent examples out of five to escape and be misidentified as authentic, which means it is not able to catch concerning alerts at an incredibly reliable rate. In order to improve this, I would train it with even more example images and fine-tune the criteria in which it analyzes the data.

--- 
## Part B: Generic vs Fine-Tuned Model Comparison 
### Models Tested
1. **Generic:** distilbert-base-uncased-finetuned-sst-2-english (sentiment) 
2. **Fine-Tuned A:** bert-tiny-finetuned-sms-spam-detection/pip — text classification
3. **Fine-Tuned B:** roberta-spam — text classification

### Results 
| Input | Generic Label (Score) | Fine-Tuned A Label (Score) | Fine-Tuned B Label (Score) | Best Model | 
|-------|-----------------------|----------------------------|----------------------------|------------| 
| Record 1 | Negative (0.9972) | Legitimate (0.5029) | Legitimate (1.0000) | Generic | 
| Record 2 | Negative (0.9911) | Legitimate (0.5427) | Fraudulent (1.0000) | Fine-Tuned B | 
| Record 3 | Negative (0.9979) | Fraudulent (0.5601) | Fraudulent (1.0000) | Fine-Tuned B | 
| Record 4 | Negative (0.7697) | Legitimate (0.6578) | Legitimate (0.9880) | Fine-Tuned B | 
| Record 5 | Negative (0.9638) | Legitimate (0.6977) | Legitimate (1.0000) | Fine-Tuned B | 

### Analysis 

**Generic model strengths:** The generic model performed well only during the first three alerts which were high-concern. For the first record, the only model to give the correct classification was the generic model.

**Generic model weaknesses:** It failed for the last two records which were low-risk/routine. For the fourth record, the generic model also had a low confidence score (0.7697). Given that for all five records, the generic model identified them as negative, it seems that it is not very accurate.

**Fine-tuned model advantage:** For the last four records, Fine-Tuned Model B outperformed both of the other two models, both in confidence scores and correctly identifying the alerts as fraudulent or legitimate. Fine-Tuned Model B had the highest confidence scores overall, with four of the five scores being 1.0000 and one being 0.9880. Fine-Tuned Model A was unfortunately not as successful, as it had low confidence scores and only correctly identified 3 of 5 records.

**Biggest surprise:** I did not expect that the generic model would outperform both of the fine-tuned models for the first record. Both of the fine-tuned models incorrectly identified the alert as legitimate, while the generic model correctly identified the alert as negative. One other thing that surprised me was Fine-Tuned Model A's confidence scores, which never exceeded 0.6977; the scores were very low in comparison to the other models' scores.

### Recommended Model for My Capstone Component 

**Component:** Transaction Ingestion Workflow

**Primary model:** roberta-spam — This model has the highest confidence scores and was able to most accurately identify fraudulent versus legitimate alerts. There was a mistake for record #1, but out of the three models tested, it was by far the most accurate. However, I would likely try to find another model to potentially replace it.

**Confidence threshold:** I would likely use around ~0.75, because the AI can make mistakes. I would only want to flag an alert if it was highly likely that it was fraud, so I would not want the threshold to be low. However, there are also cases where the confidence is lower but it is still fraud, so I would choose 0.75.

**Priority metric:** Recall is the priority metric because false negatives pose gigantic risks; for example, allowing fraudulent transactions to be cleared or identity fraud is a large liability that has ramifications. For these reasons, recall would be paramount to prioritize.

--- 
## Limitations & Next Steps 
I would definitely find alternatives to just text classification, because it did not always generate the correct results. I would add more data to work with as well, as only five records is not enough to properly assess the effectiveness of the model. I would probably like to reevaluate the types of models I have been using and figure out what the best alternatives are to provide correct analysis.
