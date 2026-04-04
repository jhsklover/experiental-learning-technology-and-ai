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
| 2 | What social engineering techniques are used when phishing for information? | Yes | Good | The RAG response accurately highlighted the different social engineering techniques that are used during phishing, like impersonation, and senses of urgency. |
| 3 | How do adversaries perform spearphishing voice? | Yes | Good | The information presented was accurate, but the results looked nearly identical to that of the previous question; that is due to the social engineering techniques being applicable as the answer for this question as well. |
| 4 | What is the difference between malicious link and malicious file? | Yes | Good | The response correctly distinguished the differences between malicious link and malicious file, with multi-sentence explanations on both. It explained that the malicious link is what gets sent and clicked on, while the malicious file contains malware. |
| 5 | How do adversaries deceive users during user execution? | Yes | Good |  |

## 3. Edge Case Observations
- **Unrelated question:** When I asked the chatbot "what is the weather like today?" it answered "hmm, I'm not sure", meaning that it admitted it had no idea.
- **Topic not in documents:** The chatbot admitted it didn't know when asked "what are the latest CVEs from 2026?"
- **Question about technique/topic not uploaded:** When asking the chatbot about what Setuid and Setgid are which relates to the Abuse Elevation Control Mechanism topic, it admitted it did not know.

## 4. Settings Experiments (if completed)
- **Temperature change:** Changing the temperature from 0.3 to 0.7 made the answers to the questions broader and more conversational, using language with more of a flow and breaking down the topic into simpler terms. The chatbot still provided accurate answers, but they were less specific.
- **Chunk size change:** Changing the chunk size from 1000 to 500 made the responses significantly shorter than before, but each response broke down a different piece of information in more detail. The information was still accurate, but also displayed less documents as sources.
- **Top K change:** Changing Top K to 6 improved the chatbot's recall. In previous answers, the chatbot did not mention the "ClickFix" strategy when asked "How do adversaries deceive users during user execution?". This allowed for more varied information, displaying more tactics and context than in previous answers.

## 5. Reflection
- What surprised you about how RAG works?
- How could you improve this chatbot for real-world use?
- How might you use RAG in your capstone project

`https://cloud.flowiseai.com/chatbot/7acf3c94-0917-4dc6-a7f2-5f25761df1c0`
