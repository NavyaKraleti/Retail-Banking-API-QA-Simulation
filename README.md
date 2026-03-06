# Retail Banking API – QA Simulation Project

This project simulates a **Retail Banking API testing environment** to demonstrate real-world **QA practices for financial systems**, including API functional testing, negative testing, compliance validation, automation execution, and defect identification.

The project replicates typical banking workflows such as **customer management, account handling, and funds transfer**, and demonstrates how QA engineers validate system behavior under normal, edge-case, and invalid conditions.

---

# Project Objectives

The primary objective of this project is to simulate how **QA engineers test banking APIs** in real-world fintech environments.

Key goals:

• Validate core banking API operations
• Perform functional and negative API testing
• Simulate compliance validation scenarios (KYC, AML)
• Identify defects in transaction processing logic
• Execute automated API testing using Newman CLI
• Document test strategy, scenarios, and defects

---

# System Architecture

The testing architecture follows a simple API automation pipeline.

Test data is executed through Postman collections and automated using Newman CLI against a simulated banking API built with JSON Server.

<p align="center">
  <img src="test-documents/Architecture_Diagram.png" width="600">
</p>

**Architecture Flow**

Test Scenario Data → Postman Collection → Newman CLI Runner → Banking API (JSON Server) → Database (`db.json`)

---

# Technology Stack

| Tool        | Purpose                             |
| ----------- | ----------------------------------- |
| Postman     | API request creation and testing    |
| Newman CLI  | Automated API test execution        |
| JSON Server | Mock backend banking API            |
| Node.js     | API runtime environment             |
| VS Code     | Development and test environment    |
| Draw.io     | Architecture diagram creation       |
| GitHub      | Version control and project hosting |

---

# Project Structure

```
Retail-Banking-API-QA-Simulation
│
├── banking_api_collection.json      # Postman API collection
├── banking_env.json                 # Environment variables
├── transactions.csv                 # Test dataset for automation
│
├── db.json                          # Mock database (runtime)
│
├── test-documents
│   ├── Test_Strategy.md
│   ├── Test_Scenario_Matrix.md
│   ├── Defect_Log.md
│   └── Architecture_Diagram.png
│
└── README.md
```

---

# Test Coverage

The project includes multiple types of testing scenarios commonly used in banking QA.

### Functional Testing

• Customer creation
• Customer retrieval
• Account information validation
• Fund transfer between accounts

### Negative Testing

• Invalid currency transfers
• Negative transaction amounts
• Missing required fields
• Duplicate transaction attempts

### Compliance & Validation

• Frozen account transaction validation
• KYC verification checks
• Transaction validation rules

### Edge Case & Risk Scenarios

• Rapid consecutive transfers
• High value transactions
• Duplicate transaction requests

### End-to-End Flows

• Customer creation → account validation → transfer execution
• Deposit → transfer → balance verification

---

# Automation Execution

API tests can be executed automatically using **Newman CLI**.

### Install Newman

```
npm install -g newman
```

### Run API Tests

```
newman run banking_api_collection.json \
-e banking_env.json \
-d transactions.csv
```

This executes multiple API scenarios sequentially using the provided test dataset.

---

# Defect Analysis

During testing several validation gaps were identified in the simulated banking API, including:

• Duplicate transaction ID acceptance
• Invalid currency validation missing
• Frozen account still allowing transactions
• Negative transfer amount acceptance
• Customer creation without KYC validation

Detailed defect documentation is available in:

```
test-documents/Defect_Log.md
```

---

# QA Artifacts

The project includes the following QA documentation:

| Document             | Description                              |
| -------------------- | ---------------------------------------- |
| Test Strategy        | Testing approach and methodology         |
| Test Scenario Matrix | Coverage of all functional scenarios     |
| Defect Log           | Identified issues and reproduction steps |
| Architecture Diagram | API testing architecture overview        |

---

# Key Learning Outcomes

This project demonstrates practical QA skills including:

• API testing strategy design
• Postman collection development
• Automation execution using Newman
• Negative and edge-case testing
• Defect discovery and documentation
• QA artifact documentation

---

# Future Enhancements

Potential improvements for the project include:

• CI/CD pipeline integration (GitHub Actions)
• Automated test reporting
• Performance testing using JMeter or k6
• Security validation scenarios
• Mock fraud detection rule simulation

---

# Author

Navya Kraleti
Quality Assurance Engineer
API Testing | Data Testing | Automation Testing

---
