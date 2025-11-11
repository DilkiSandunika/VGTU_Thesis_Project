# Automated Functional Requirements Extraction System

This project implements an end-to-end AI agent for automatically extracting Functional Requirements (FRs) from diverse software documentation sources. It leverages Google's Gemini Large Language Model (LLM) and prompt engineering principles to parse, understand, and structure requirements with high accuracy and compliance awareness.

## ✨ Key Features

Automated Extraction: Processes raw text from sources like user stories, interview notes, and change requests.

LLM-Powered Intelligence: Uses the Gemini API to understand context, identify requirements, and generate structured output.

Zero-Shot & Few-Shot Learning: Demonstrates the ability to extract requirements both with and without prior examples.

Domain-Specific Awareness: Tailors extraction to domains like Healthcare, Finance, and E-commerce.

Compliance Tagging: Automatically tags extracted requirements with relevant industry standards (e.g., HIPAA, GDPR, FDA 21 CFR, PCI DSS).

Automated Quality Validation: Measures the quality of extracted FRs using metrics for faithfulness, relevance, and compliance.

## ⚙️ System Pipeline

The system processes documents through a five-stage pipeline to ensure high-quality, structured output:

Input (X) → Document Preprocessing → Knowledge Base Construction → Contextual Retrieval & Prompting → LLM Processing → Quality Validation → Output (y)

Document Preprocessing: Cleans and structures the input document, identifying its type, domain, and compliance context.

Knowledge Base Construction: Builds a temporary knowledge base with relevant domain vocabulary, compliance rules, and FR templates.

Contextual Retrieval & Prompting: Engineers a detailed prompt for the LLM, incorporating the preprocessed document and the knowledge base.

LLM Processing: Sends the prompt to the Gemini API to generate a structured JSON output of functional requirements.

Quality Validation: Parses the LLM's response and calculates quality metrics to evaluate the results against predefined targets.

## 🛠️ Technology Stack

Language: Python 3

LLM: Google Gemini (gemini-1.5-pro-latest or similar)

Core Libraries:
google-generativeai: For interacting with the Gemini API.

python-dotenv: For managing environment variables (like API keys).

tabulate: For formatting and displaying metric tables.

## 📈 Reflection & Future Enhancements
### What Worked Well

Consistent JSON Output: Strict prompt engineering resulted in reliable JSON that was easily parsed.

High Faithfulness: The model excelled at tracing extracted requirements back to the source text.

Effective Compliance Tagging: The system successfully identified and tagged requirements with the correct regulatory standards.

### Areas for Improvement
True RAG Implementation: The current knowledge base is rule-based. Future work should integrate a vector database (e.g., FAISS, Pinecone) for true Retrieval-Augmented Generation, allowing the system to pull from a much larger corpus of documents.

Semantic Quality Metrics: Quality validation could be enhanced by using an LLM to evaluate the semantic similarity and correctness of the requirements.

Iterative Refinement: Implement a loop where requirements that fail quality checks are automatically sent back to the LLM with feedback for refinement.

### What your system does as a complete AI agent.

This AI agent automates the extraction of functional requirements from raw software documentation, processing it through a complete five-stage pipeline from ingestion to quality validation. The system uses the Gemini model as its core intelligence, guided by carefully constructed prompts that provide crucial context like the document's domain, compliance standards, and a strict JSON output schema. This prompt engineering was used in both a zero-shot capacity for direct extraction and a few-shot capacity where examples were provided to improve the model's performance on a new task.
