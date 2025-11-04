# Prompt 2: Few-Shot Functional Requirements Extraction

## System Role
You are an expert Requirements Engineering AI agent specialized in extracting Functional Requirements (FRs) from diverse software documentation sources. You learn from provided examples to understand the expected extraction patterns, formatting conventions, and domain-specific terminology.

## Learning Approach
This is a **few-shot learning** task. You will be provided with several (X, y) pairs showing example inputs and their corresponding correctly extracted functional requirements. Use these examples to understand:
- FR structuring patterns
- Domain terminology recognition
- Compliance mapping strategies
- Quality validation criteria

Then apply this learned pattern to extract FRs from a new, unseen input.

---

## Training Examples

### Example 1: Healthcare Domain

**Input (X₁)**:
```
Document Type: Change Request
Domain: Medical Device Software
Compliance: FDA 21 CFR Part 11
Content:
"We need to add digital signature capability to the prescription module. 
When a doctor finalizes a prescription, they must sign it electronically. 
The signature should be timestamped and include the doctor's credentials. 
This is required for regulatory compliance."
```

**Output (y₁)**:
```
FR-101: The system shall enable electronic signature functionality for prescription finalization.
Source: "add digital signature capability to the prescription module"
Domain Terms: electronic signature, prescription, finalization
Compliance Tags: FDA 21 CFR Part 11 (electronic signatures)
Confidence Score: 0.96

FR-102: The system shall require physician electronic signature upon prescription finalization.
Source: "When a doctor finalizes a prescription, they must sign it electronically"
Domain Terms: physician, prescription finalization, mandatory signature
Compliance Tags: FDA 21 CFR Part 11 §11.50 (signature requirements)
Confidence Score: 0.98

FR-103: The system shall timestamp all electronic signatures applied to prescriptions.
Source: "The signature should be timestamped"
Domain Terms: timestamp, electronic signature, prescription
Compliance Tags: FDA 21 CFR Part 11 §11.50(a) (signature manifestations)
Confidence Score: 0.97

FR-104: The system shall include physician credentials with each electronic signature.
Source: "include the doctor's credentials"
Domain Terms: physician credentials, electronic signature, authentication
Compliance Tags: FDA 21 CFR Part 11 §11.50(a) (printed name)
Confidence Score: 0.95
```

---

### Example 2: E-commerce Domain

**Input (X₂)**:
```
Document Type: User Story
Domain: Online Retail Platform
Compliance: PCI DSS, GDPR
Content:
"As a customer, I want to save my payment information securely so that I can 
checkout faster next time. The card details should be encrypted and I should 
be able to delete them anytime. I also want to see when my information was 
last used."
```

**Output (y₂)**:
```
FR-201: The system shall allow customers to save payment information for future transactions.
Source: "save my payment information securely so that I can checkout faster"
Domain Terms: payment information, customer account, saved credentials
Compliance Tags: PCI DSS (secure storage), GDPR (consent)
Confidence Score: 0.97

FR-202: The system shall encrypt all stored payment card details.
Source: "The card details should be encrypted"
Domain Terms: encryption, payment card details, data security
Compliance Tags: PCI DSS Requirement 3 (protect stored cardholder data)
Confidence Score: 0.99

FR-203: The system shall enable customers to delete their saved payment information at any time.
Source: "I should be able to delete them anytime"
Domain Terms: data deletion, customer control, payment information
Compliance Tags: GDPR Article 17 (right to erasure)
Confidence Score: 0.98

FR-204: The system shall display the last usage timestamp for saved payment information.
Source: "I also want to see when my information was last used"
Domain Terms: usage history, timestamp, payment information
Compliance Tags: GDPR Article 15 (right of access)
Confidence Score: 0.94
```

---

### Example 3: Financial Services Domain

**Input (X₃)**:
```
Document Type: SRS Excerpt
Domain: Banking Mobile Application
Compliance: SOX, Basel III
Content:
"The transaction history feature must show all account activities for the past 
7 years. Each transaction record includes date, amount, merchant name, and 
transaction type. Users can search and filter by date range or transaction type. 
For compliance, all queries must be logged with user ID and timestamp."
```

**Output (y₃)**:
```
FR-301: The system shall maintain transaction history records for a minimum of 7 years.
Source: "show all account activities for the past 7 years"
Domain Terms: transaction history, retention period, account activities
Compliance Tags: SOX (recordkeeping), Basel III (operational risk data)
Confidence Score: 0.97

FR-302: The system shall store transaction date, amount, merchant name, and transaction type for each record.
Source: "Each transaction record includes date, amount, merchant name, and transaction type"
Domain Terms: transaction attributes, merchant information, transaction type
Compliance Tags: Basel III (data granularity requirements)
Confidence Score: 0.98

FR-303: The system shall enable users to search transaction history by date range.
Source: "Users can search and filter by date range"
Domain Terms: search functionality, date range filter, transaction history
Compliance Tags: Standard banking practice
Confidence Score: 0.96

FR-304: The system shall enable users to filter transaction history by transaction type.
Source: "filter by date range or transaction type"
Domain Terms: filter functionality, transaction type, history view
Compliance Tags: Standard banking practice
Confidence Score: 0.96

FR-305: The system shall log all transaction history queries with user ID and timestamp.
Source: "all queries must be logged with user ID and timestamp"
Domain Terms: audit logging, query tracking, user identification
Compliance Tags: SOX (audit trail), Basel III (access monitoring)
Confidence Score: 0.99
```

---

## New Task: Apply Learned Pattern

Now that you have learned from these examples, extract functional requirements from the following new input:

### Input (X_new)

**Document Type**: Interview Notes  
**Domain**: Healthcare - Telemedicine Platform  
**Compliance Standards**: HIPAA, HL7 FHIR, FDA (if applicable)  
**Raw Content**:
```
Interview with Dr. Sarah Chen, Chief Medical Officer
Date: November 2, 2025

"Our telemedicine platform needs better integration with pharmacy systems. 
When I prescribe medication during a video consultation, the prescription should 
automatically be sent to the patient's preferred pharmacy. The patient should 
receive a notification once it's ready for pickup. We need to ensure that 
controlled substances require additional verification steps - maybe a second 
authentication factor from the prescribing physician. Also, the system should 
check for drug interactions with the patient's current medications before 
sending the prescription. All of this needs to comply with HIPAA and maintain 
a complete audit trail. Oh, and if a prescription fails to transmit, the 
physician should be notified immediately so they can handle it manually."
```

### Expected Output (y_new)

Generate the functional requirements following the pattern demonstrated in the training examples. Include:
- Structured FR statements (FR-XXX format)
- Source traceability
- Domain terms identification
- Compliance tags
- Confidence scores

---

## Instructions for Agent

1. **Analyze the training examples** to understand:
   - How FRs are structured ("The system shall...")
   - How source content is mapped to requirements
   - How domain terminology is identified
   - How compliance standards are tagged
   - How confidence scores reflect certainty

2. **Apply the learned pattern** to extract FRs from the new interview notes

3. **Ensure coverage** of all functional aspects mentioned:
   - Pharmacy integration
   - Automatic prescription transmission
   - Patient notifications
   - Controlled substance verification
   - Drug interaction checking
   - HIPAA compliance
   - Audit trail maintenance
   - Error notification

4. **Validate quality** using the metrics framework:
   - Faithfulness to source content
   - Answer relevance to stakeholder needs
   - Technical term coverage
   - Compliance score

5. **Generate output** in the same format as the training examples

---

## Quality Metrics Evaluation

After generating the requirements, evaluate using:

| Metric | Description | Calculation Method |
|--------|-------------|-------------------|
| **Faithfulness** | FRs grounded in source | Count claims traceable to interview / Total claims |
| **Answer Relevance** | FRs address stakeholder needs | Semantic similarity between FRs and interview intent |
| **Technical Term Coverage** | Domain terms captured | Identified medical/pharmacy terms / Total domain terms in source |
| **Compliance Score** | Regulatory alignment | FRs with compliance tags / Total FRs |
| **Recall@k** | Expected FRs in output | Expected requirements found / Total expected requirements |

### Expected Functional Areas to Cover:
1. Pharmacy system integration
2. Prescription transmission automation
3. Patient notification system
4. Controlled substance handling
5. Drug interaction checking
6. HIPAA compliance mechanisms
7. Audit trail logging
8. Error handling and physician alerts

Target: Extract 8-12 FRs covering all functional areas with average confidence ≥ 0.90
