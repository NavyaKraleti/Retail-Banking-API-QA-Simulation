# Test Strategy – Retail Banking API QA Simulation

## 1. Objective

The objective of this project is to validate the functionality, compliance, and reliability of a Retail Banking API system that handles customer management, account management, and financial transactions.

The testing approach focuses on identifying defects related to financial accuracy, transaction processing, compliance validation, and fraud detection scenarios.

---

## 2. Scope

### In Scope

• Customer onboarding APIs
• Account management APIs
• Transaction processing APIs
• Funds transfer operations
• Compliance validation
• Fraud detection scenarios
• Edge case handling
• Automated scenario simulation

### Out of Scope

• UI testing
• Performance testing at infrastructure level
• Payment gateway integrations
• External banking systems

---

## 3. Testing Types Implemented

Functional Testing
Validation of API functionality including creation, retrieval, and update operations.

Negative Testing
Testing invalid inputs such as negative transaction amounts and missing fields.

Compliance Testing
Validating regulatory rules such as KYC requirements and frozen account restrictions.

Risk Scenario Testing
Detection of suspicious activities including rapid consecutive transfers and high value transactions.

End-to-End Testing
Simulation of real banking workflows such as deposit → transfer → balance verification.

Automation Testing
Automated transaction simulations using Postman Collection Runner and Newman CLI.

---

## 4. Test Environment

| Component         | Tool        |
| ----------------- | ----------- |
| API Simulation    | JSON Server |
| API Testing Tool  | Postman     |
| Automation Runner | Newman CLI  |
| Data Source       | CSV dataset |
| Repository        | GitHub      |
| Development Tool  | VS Code     |

---

## 5. Test Data Strategy

Test data includes:

• Valid customer records
• Customers without KYC validation
• Active and frozen accounts
• High value transaction scenarios
• Negative transaction amounts
• Invalid currency codes

The dataset is executed through automated iterations to simulate real transaction patterns.

---

## 6. Risk Areas

• Duplicate transaction processing
• Invalid currency acceptance
• Negative transaction values
• Transactions on frozen accounts
• Missing KYC compliance
• Suspicious rapid transaction patterns

---

## 7. Entry Criteria

• API server is running
• Environment variables configured
• Test data dataset available
• Postman collection imported

---

## 8. Exit Criteria

Testing is considered complete when:

• All critical APIs are executed
• End-to-end flows are validated
• Major compliance defects are identified
• Automated scenario runs completed successfully