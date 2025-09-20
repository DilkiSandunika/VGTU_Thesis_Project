# Subject Domain Analysis Based On Text Mining Using a Large Language Model

**Author:** Dilki Sandunika Rathnayake (20242001)  
**University:** VILNIUS GEDIMINAS TECHNICAL UNIVERSITY (VILNIUS TECH)  
**Thesis:** Master Graduation Thesis, 2025

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/python-3.9%2B-blue.svg)](https://www.python.org/downloads/)

---

## 1. Abstract

This repository contains the end-to-end implementation for the Master's thesis, "Subject Domain Analysis Based On Text Mining Using a Large Language Model." The project addresses the critical challenge of manually extracting Functional Requirements (FRs) from software documentation, a process that is often time-consuming, error-prone, and inconsistent.

This work proposes and implements a novel, automated pipeline that leverages a **Retrieval-Augmented Generation (RAG)** architecture. By combining the contextual retrieval of domain-specific knowledge and compliance rules with the advanced generative capabilities of Large Language Models (LLMs), this system extracts, validates, and standardizes FRs from unstructured text. The primary goal is to enhance the **consistency, compliance, and traceability** of requirements, providing a robust foundation for the software development lifecycle.

## 2. Key Features

*   **Automated FR Extraction:** Identifies and extracts functional requirements from raw text documents (e.g., SRS files).
*   **Compliance & Consistency Verification:** Validates extracted requirements against a custom, domain-specific knowledge base of rules, standards, and templates.
*   **Retrieval-Augmented Generation (RAG):** Reduces LLM hallucinations and improves accuracy by grounding the generation process in retrieved, factual context.
*   **Traceability:** Links each extracted requirement back to its original source sentence in the input document.
*   **Modular and Reproducible:** The code is structured to be easily understood, reproduced, and extended for further research.

## 3. Architecture Overview

The core of this project is an end-to-end pipeline that treats the complex process of FR extraction as a "black box." The system takes source documents and a knowledge base as input and produces structured, validated functional requirements as output.

**High-Level Flow:**

```
[Input Documents + Knowledge Base] -> [RAG Pipeline] -> [Structured, Validated FRs]
```

**Detailed Steps:**

1.  **Ingestion & Indexing:** The knowledge base (containing compliance rules, templates, and domain vocabulary) is loaded and indexed into a searchable vector database.
2.  **Input Processing:** A user submits a source document (e.g., an SRS file) for analysis.
3.  **Contextual Retrieval:** For each segment of the source document, the system retrieves the most relevant rules and context from the indexed knowledge base.
4.  **Augmented Prompting:** A detailed, context-rich prompt is constructed for the LLM, containing the original text, the retrieved knowledge, and a clear set of instructions.
5.  **Intelligent Generation:** The LLM processes the prompt to generate functional requirements in a structured format.
6.  **Validation & Output:** The generated requirements are validated against the metrics defined in the thesis (Faithfulness, Compliance Score) and presented in a clean, structured format (e.g., JSON).

**(Recommended: Create a simple diagram using a tool like draw.io or Excalidraw and embed the image here)**
`![Architecture Diagram](path/to/your/architecture_diagram.png)`

## 4. Dataset

This implementation uses a combination of a public dataset and a custom-built knowledge base to demonstrate the methodology.

*   **Source Documents:** We use a selection of Software Requirements Specification (SRS) documents from the **[PURE (PUblic REquirements) dataset](https://github.com/RE-Lab-Projects/PURE)**, a well-established resource in requirements engineering research.
*   **Knowledge Base:** A custom knowledge base was created to simulate a real-world compliance environment. It is located in `data/raw/knowledge_base/` and includes:
    *   `compliance_rules.txt`: A set of rules that functional requirements must adhere to.
    *   `template_guide.txt`: A structural template for how FRs should be written.

## 5. Getting Started

Follow these instructions to set up the project environment and run the demonstration.

### Prerequisites

*   Python 3.9 or higher
*   Git
*   An API Key from an LLM provider (e.g., OpenAI).

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/Dilki-Sandunika-Rathnayake-Thesis.git
    cd Dilki-Sandunika-Rathnayake-Thesis
    ```

2.  **Create and activate a virtual environment (recommended):**
    ```bash
    python -m venv venv
    # On Windows
    .\venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Set up your environment variables:**
    *   Create a file named `.env` in the root directory of the project.
    *   Add your Large Language Model API key to this file. The .gitignore file is already configured to prevent this file from being committed to GitHub.
    ```
    # .env file content
OPENAI_API_KEY="your_api_key_here"
    ```

5.  **Download the data:**
    *   Download a few SRS `.txt` files from the [PURE dataset](https://github.com/RE-Lab-Projects/PURE).
    *   Place them inside the `data/raw/source_documents/` directory.

## 6. How to Run the Demo

This project can be run either directly in your browser using Google Colab (recommended) or on your local machine.

### A. Running on Google Colab (Recommended Method)

This is the easiest way to see the system in action, as it requires no local installation. Each notebook can be opened with a single click.

1.  **`01_data_exploration.ipynb`** - Parses the raw XML and creates a clean CSV of requirements.
    [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DilkiSandunika/VGTU_Thesis_Project/blob/main/notebooks/01_data_exploration.ipynb)

2.  **`02_knowledge_base_creation.ipynb`** - Builds the vector database from the knowledge base files.
    [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DilkiSandunika/VGTU_Thesis_Project/blob/main/notebooks/02_knowledge_base_creation.ipynb)

3.  **`03_end_to_end_pipeline_demo.ipynb`** - The main demonstration. This notebook runs the full RAG pipeline and shows the final results.
    [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DilkiSandunika/VGTU_Thesis_Project/blob/main/notebooks/03_end_to_end_pipeline_demo.ipynb)

#### **Instructions for Colab:**
*   When you open a notebook, you will need to upload the required data files as instructed in the notebook's first few cells.
*   For the `03_...` notebook, you **must enable a GPU accelerator**. To do this, go to **Runtime > Change runtime type > Hardware accelerator** and select **T4 GPU**.
*   You will also need to add your free Hugging Face token to Colab's "Secrets" manager with the name `HF_TOKEN` to run the final notebook.

### B. Running Locally

Follow these instructions if you have a local Python environment set up.

1.  Ensure you have followed all the steps in the **"Installation"** section above.
2.  Make sure your virtual environment is activated:
    ```bash
    # On Windows using Git Bash
    source venv/Scripts/activate
    ```
3.  Launch Jupyter Lab from your terminal:
    ```bash
    jupyter lab
    ```
4.  Once Jupyter Lab opens in your browser, navigate to the `/notebooks` directory.
5.  Open and run the notebooks sequentially (`01_...`, `02_...`, `03_...`) to execute the full data processing and demonstration pipeline.

## 7. Project Structure

```
.
├── data/
│   ├── raw/                # Original, unmodified data
│   │   ├── source_documents/ # SRS files from PURE dataset go here
│   │   └── knowledge_base/   # Custom compliance and template files
│   └── processed/          # Processed data, including the vector DB
├── notebooks/              # Jupyter notebooks for exploration and demonstration
├── src/                    # Core Python source code
│   ├── data_processing.py  # Functions for cleaning and preparing text
│   ├── rag_pipeline.py     # Main RAG architecture logic
│   └── validation.py       # Functions for calculating evaluation metrics
├── .env.example            # Example environment file
├── requirements.txt        # Project dependencies
└── README.md               # This file
```

## 8. Methodology & Evaluation

This implementation is grounded in the methodologies described in the thesis.

*   **Core Technique:** Retrieval-Augmented Generation (RAG) using a FAISS vector index and a Sentence-Transformer model for embeddings.
*   **Evaluation Metrics Implemented:** The `src/validation.py` module includes functions to assess the quality of the generated requirements based on:
    *   **Faithfulness:** How well the output is grounded in the provided source text.
    *   **Compliance Score:** A custom metric that checks adherence to the rules in the knowledge base.
    *   **Technical Term Coverage:** Measures the use of correct domain-specific terminology.

## 9. License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## 10. Acknowledgements

I would like to express my sincere gratitude to my thesis supervisor, [Supervisor's Name], for their invaluable guidance and support throughout this research.

## 11. Citation

If you use the code or concepts from this research, please cite the original thesis:

```bibtex
@mastersthesis{Rathnayake2025,
  author    = {Dilki Sandunika Rathnayake},
  title     = {Subject Domain Analysis Based On Text Mining Using a Large Language Model},
  school    = {Vilnius Gediminas Technical University},
  year      = {2025},
  address   = {Vilnius, Lithuania}
}
```

