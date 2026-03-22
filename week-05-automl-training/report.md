# Week 5 Report: AutoML Training & Fine-Tuned Model Evaluation 

**Name:** Jack Sklover

**Date:** 03/22/2026

**Capstone Project:** Financial Fraud Detection System

**My Component:** Transaction Ingestion Workflow

## Part A: Teachable Machine Training 
### Training Setup
- **Task:** Forged vs. Authentic image classification
- **Training images per class:** 30
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
|  | Predicted: [Class 1] | Predicted: [Class 2] | 
|---|---|---| 
| **Actual: [Class 1]** | TP = ___ | FN = ___ | 
| **Actual: [Class 2]** | FP = ___ | TN = ___ | 
### Calculated Metrics- **Accuracy:** ___% - **Precision:** ___% - **Recall:** ___% - **F1 Score:** ___% 
2026-03-09
### Interpretation 
[2-3 sentences: Is your model better at precision or recall? Which errors did it 
make? 
What would improve it?] --- 
## Part B: Generic vs Fine-Tuned Model Comparison 
### Models Tested
1. **Generic:** distilbert-base-uncased-finetuned-sst-2-english (sentiment) 
2. **Fine-Tuned A:** [model name] — [what it does] 
3. **Fine-Tuned B:** [model name] — [what it does] 
14 / 25
### Results 
week-05-lab-instructions.md
2026-03-09
| Input | Generic Label (Score) | Fine-Tuned A Label (Score) | Fine-Tuned B Label 
(Score) | Best Model | 
|-------|-----------------------|-----------------------------|---------------------------|------------| 
| Record 1 | | | | | 
| Record 2 | | | | | 
| Record 3 | | | | | 
| Record 4 | | | | | 
| Record 5 | | | | | 
### Analysis 
**Generic model strengths:** [When did the generic model perform well?] 
**Generic model weaknesses:** [When did it fail or give low confidence?] 
**Fine-tuned model advantage:** [Where did the fine-tuned models clearly 
outperform the generic one?] 
**Biggest surprise:** [What result did you not expect?] 
### Recommended Model for My Capstone Component 
**Component:** [Your capstone component name] 
**Primary model:** [Name] — [Why this model for your task] 
**Confidence threshold:** [What threshold would you use? Why?] 
**Priority metric:** [Precision, Recall, or F1? Why does this matter for your 
project?] --- 
## Limitations & Next Steps 
[What would you do differently with more data or time? Would you fine-tune your 
own 
model? What additional models would you test?] 
