# Tools Used
- Flowise
- Groq API

# Components

- **Alert Classifier:** This Flowise chatbot classifies security alerts by security using Groq API. When you use the chatbot, you can enter an alert which produces a summary stating the severity (LOW, MEDIUM, HIGH or CRITICAL), confidence score, and a sentence-long reasoning.
- **Threat Analyzer:** This Flowise chatbot uses Groq API in the form of a threat intelligence analyst to provide a structured analysis given an alert and its severity classification. This produces an attack type, indicators, potential impact, and related mitre techniques.
- **Response Recommender:** The response recommender employs Groq API as an incident response coordinator, which recommends actions against attacks. This includes immediate acctions, and containment strategy.
