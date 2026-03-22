# Week 5: AutoML & No-Code Model Training 

Trained a custom image classifier with Google Teachable Machine and compared 
generic vs fine-tuned Hugging Face models for the **Transaction Ingestion Workflow** component 
of our **Financial Fraud Detection System** capstone.

## Custom Model Training
- Built a **Authentic/Forged** image classifier with Teachable Machine
- Achieved **70**% accuracy on 10 held-out test images
- Precision: **75**% | Recall: **60**% | F1: **66.67**%

## Fine-Tuned Model Comparison 
Compared 3 models (1 generic + 2 fine-tuned) on 5 test inputs: 
- Generic: distilbert-sst-2 (sentiment)
- Fine-Tuned A: bert-tiny-finetuned-sms-spam-detection (text classification)
- Fine-Tuned B: roberta-spam (text classification)

## Finding 
Recommended **roberta-spam** for **Transaction Ingestion Workflow** because it provided the most accurate analysis of the input texts, correctly identifying if they were legitimate or fraudulent 80% of the time. 
Fine-tuned models showed **higher** performance with more relevant labels and correct analysis. 

See `report.md` for full analysis.
