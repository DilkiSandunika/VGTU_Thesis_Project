# FR Extraction AI Agent

## Overview

This directory contains prompt examples for the **Automated Functional Requirements Extraction System** using Large Language Models (LLM) and Retrieval-Augmented Generation (RAG). The system processes diverse software documentation sources (SRS, user stories, change requests, interview notes, etc.) and extracts structured, compliant functional requirements.

## System Architecture Concept

The AI agent functions as an **end-to-end solution**:

```
Input (X) → [AI Agent Pipeline] → Output (y)
         ↓
    [Document Preprocessing]
         ↓
    [Knowledge Base Construction]
         ↓
    [Contextual Retrieval (RAG)]
         ↓
    [LLM Processing & Generation]
         ↓
    [Quality Validation]
         ↓
    Structured Functional Requirements
```

## Prompt Files

### 1. `simple_zero_shot_prompt.md`
**Type**: Zero-Shot Learning  
**Purpose**: Demonstrates single-instance FR extraction without prior examples  
**Use Case**: Quick extraction from new documents when similar examples aren't available

**Key Features**:
- Single input document processing
- Standard FR format application
- Compliance tagging
- Domain terminology identification
- Quality metrics computation

**Example Domain**: Healthcare EHR system with HIPAA/HL7 compliance

### 2. `few_shot_prompt.md`
**Type**: Few-Shot Learning  
**Purpose**: Demonstrates FR extraction after learning from multiple (X,y) examples  
**Use Case**: Improved accuracy when example requirements are available

**Key Features**:
- Three training examples from different domains (Healthcare, E-commerce, Finance)
- Pattern learning from diverse compliance contexts (FDA 21 CFR, PCI DSS, GDPR, SOX)
- Application to new unseen input
- Consistent formatting and quality standards

**Training Examples Included**:
1. Medical Device Software (FDA 21 CFR Part 11)
2. Online Retail Platform (PCI DSS, GDPR)
3. Banking Mobile Application (SOX, Basel III)

**New Task**: Telemedicine Platform (HIPAA, HL7 FHIR)

## How to Use These Prompts

### For Researchers/Developers:

1. **Choose appropriate prompt type**:
   - Use **Zero-Shot** for quick, one-off extractions
   - Use **Few-Shot** for consistent extraction across similar document types

2. **Customize the input section**:
   - Replace `Raw Content` with your actual document
   - Specify correct `Domain` and `Compliance Standards`
   - Set appropriate `Document Type`

3. **Submit to LLM** (e.g., GPT-4, Claude, or custom fine-tuned model)

4. **Evaluate output** using provided metrics:
   - Faithfulness (grounding in source)
   - Answer Relevance (alignment with intent)
   - Technical Term Coverage
   - Compliance Score

### For Integration with RAG System:

These prompts can be integrated into your RAG pipeline:

```python
# Pseudocode example
def extract_requirements(document, domain, standards):
    # 1. Preprocess document
    cleaned_doc = preprocess(document)
    
    # 2. Retrieve relevant context from knowledge base
    context = rag_retrieval(cleaned_doc, domain)
    
    # 3. Construct prompt with context
    if has_training_examples:
        prompt = construct_few_shot_prompt(cleaned_doc, context, examples)
    else:
        prompt = construct_zero_shot_prompt(cleaned_doc, context)
    
    # 4. Generate requirements via LLM
    requirements = llm.generate(prompt)
    
    # 5. Validate and structure output
    validated_frs = validate_requirements(requirements, standards)
    
    return validated_frs
```

## Evaluation Metrics (From RAGAS Framework)

Both prompts support automated quality assessment:

| Metric | Description | Target |
|--------|-------------|--------|
| **Faithfulness** | FRs grounded in source content | ≥ 0.90 |
| **Answer Relevance** | FRs address document intent | ≥ 0.90 |
| **Technical Term Coverage** | Domain terminology captured | ≥ 0.85 |
| **Compliance Score** | Regulatory alignment | ≥ 0.95 |
| **Recall@k** | Expected FRs in top-k outputs | ≥ 0.80 |

## Domain-Specific Adaptations

The prompts can be adapted for various domains by modifying:

1. **Compliance Standards**: 
   - Healthcare: HIPAA, HL7, FDA 21 CFR
   - Finance: SOX, Basel III, PCI DSS
   - Automotive: ISO 26262, ASPICE
   - Aerospace: DO-178C, ARP4754A

2. **Domain Terminology**:
   - Medical: PHI, EHR, diagnosis, prescription
   - Financial: transaction, account, cardholder data
   - Industrial: safety-critical, fail-safe, redundancy

3. **Document Types**:
   - Agile: User stories, epics, backlog items
   - Traditional: SRS, vision documents, use cases
   - Regulatory: Compliance documents, audit reports

## Expected Output Format

All prompts generate FRs in the following structure:

```
FR-[ID]: The system shall [action] [object] [under conditions].
Source: "[exact quote from input]"
Domain Terms: [term1, term2, term3]
Compliance Tags: [Standard/Regulation (specific clause if applicable)]
Confidence Score: [0.0-1.0]
```

## Validation Checklist

Before considering output complete, verify:

- [ ] All FRs follow "The system shall..." format
- [ ] Each FR traces back to source content
- [ ] Domain-specific terminology correctly identified
- [ ] Applicable compliance standards tagged
- [ ] No hallucinated requirements (all grounded in input)
- [ ] Ambiguous language avoided (clear, testable statements)
- [ ] Completeness: all functional aspects addressed

**Key Technologies**:
- Large Language Models (GPT-4, BERT, T-5)
- Retrieval-Augmented Generation (RAG)
- RAGAS Evaluation Framework
- BPMN Process Modeling


---

**Last Updated**: November 4, 2025  
**Version**: 1.0  
**Status**: Initial Release
