# Week 7: RAG Security Knowledge Assistant — Evaluation Report

## 1. Setup Summary
- **LLM:** llama-3.3-70b-versatile via Groq API
- **Embeddings:** sentence-transformers/all-MiniLM-L6-v2 via HuggingFace
- **Vector Store:** In-Memory Vector Store
- **Documents loaded:** `mitre-account-discovery.txt` (13 pages); `mitre-phishing-for-information.txt` (6 pages); `mitre-user-execution.txt` (28 pages)


## 2. Test Results
| # | Question | Used Documents? | Quality | Notes |
|---|----------|----------------|---------|-------|
| 1 | How do adversaries access lists of accounts, such as via domain, email, local, and cloud accounts? | Yes | Good | The RAG response was highly accurate; it highlighted all four sub-techniques for account discovery, and outlined specific procedures used to obtain information. The response also included several examples, including Ruler, TA505, and Volt Typhoon. |
| 2 | What social engineering techniques are used when phishing for information? | | | |
| 3 | How do adversaries perform spearphishing voice? | | | |
| 4 | What is the difference between malicious link and malicious file? | | | |
| 5 | How do adversaries deceive users during user execution? | | | |
## 3. Edge Case Observations- **Unrelated question:** [what happened when you asked something off-topic?]- **Topic not in documents:** [did it hallucinate or admit it didn't know?]
## 4. Settings Experiments (if completed)- **Temperature change:** [what effect did you observe?]- **Chunk size change:** [what effect did you observe?]- **Top K change:** [what effect did you observe?]
## 5. Reflection- What surprised you about how RAG works?- How could you improve this chatbot for real-world use?- How might you use RAG in your capstone project
