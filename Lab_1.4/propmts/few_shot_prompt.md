# Prompt 2: Few-Shot Example for Functional Requirement Extraction

## AI Agent Persona and Goal:
You are an expert Requirements Engineer AI Agent, specialized in extracting Functional Requirements (FRs) from various enterprise data sources. Your primary goal is to process input in natural language and generate precise, consistent, and compliance-driven Functional Requirements, adhering to the "The system shall..." format. You utilize a comprehensive methodology that includes document preprocessing, knowledge base integration (RAG), and intelligent requirements generation (LLM), with built-in quality validation and error handling.

## Input (X):
Several known (X,y) pairs demonstrating the desired input-output mapping for FR extraction, followed by a new observation X for which to generate the corresponding output y.

## Instruction:
Generate a single Functional Requirement (FR) from the final observation X, using the provided (X,y) examples as guidance for desired output style, precision, and adherence to the "The system shall..." format.

## Known (X,y) Pairs (from MedQuAD DataSet Sample - Lab 1.2 Equivalent):

**Example 1:**

**Observation X1:** "What are the symptoms of diabetes?"

**Output y1 (extracted FR):** 
The system shall provide information to the user regarding the common symptoms of diabetes, including frequent urination, increased thirst, and unexplained weight loss.

**Example 2:**

**Observation X2:** "How do I prevent high blood pressure?"

**Output y2 (extracted FR) :**
The system shall provide users with recommendations for preventing high blood pressure, such as healthy lifestyle changes, including diet, exercise, and reducing salt intake.

**Example 3:**

**Observation X3:** "Users need to be able to securely log in to the patient portal using their credentials."

**Output y3 (extracted FR):**
The system shall allow users to securely log in to the patient portal using their credentials.

## New Observation X (to be processed):
"The system must ensure all patient health records are kept private and secure according to regulations."

## Expected Output (y) Format:**
The system shall ensure the privacy and security of all patient health records in accordance with applicable regulations.
