# Defect Log – Retail Banking API QA Simulation

This document records defects identified during functional, negative, compliance, and automation testing of the **Retail Banking API Simulation Project**.

Testing was performed using **Postman**, **Newman CLI**, and **JSON Server** to simulate core banking API behaviors including customer management, account operations, and fund transfers.

Environment
Local API Simulation – JSON Server (localhost:3000)

---

# DEFECT SUMMARY

| Defect ID | Module                 | Severity | Priority | Status |
| --------- | ---------------------- | -------- | -------- | ------ |
| DEF-01    | Transaction Processing | High     | High     | Open   |
| DEF-02    | Transaction Processing | Medium   | Medium   | Open   |
| DEF-03    | Compliance Validation  | Critical | High     | Open   |
| DEF-04    | Transaction Validation | High     | High     | Open   |
| DEF-05    | Customer Management    | High     | Medium   | Open   |

---

# DEF-01 – Duplicate Transaction ID Accepted

Module
Transaction Processing

Severity
High

Priority
High

API Endpoint
POST /transfer

Description
The API allows multiple transactions with the same transaction ID, which should normally be prevented by idempotency validation.

Steps to Reproduce

1. Execute a transfer request with transaction ID **TXN123**.
2. Send the same transfer request again using the identical transaction ID.

Expected Result
The system should reject duplicate transaction IDs and return a validation error.

Actual Result
The second request is processed successfully and another transaction record is created.

Impact
Duplicate transactions may result in **double debit scenarios**, financial inconsistencies, and reconciliation errors.

Status
Open

---

# DEF-02 – Invalid Currency Accepted

Module
Transaction Processing

Severity
Medium

Priority
Medium

API Endpoint
POST /transfer

Description
The API accepts unsupported or invalid currency codes instead of validating against a supported currency list.

Steps to Reproduce

1. Initiate a transfer request.
2. Set currency value to **XYZ** (unsupported currency).

Expected Result
The API should return a validation error indicating unsupported currency.

Actual Result
Transaction is processed successfully with the invalid currency.

Impact
Invalid currency processing can lead to **incorrect financial calculations and reporting issues**.

Status
Open

---

# DEF-03 – Frozen Account Allows Transactions

Module
Compliance Validation

Severity
Critical

Priority
High

API Endpoint
POST /transfer

Description
Transfers can still be executed from accounts marked with **Frozen** status.

Steps to Reproduce

1. Update account status to **Frozen**.
2. Initiate a transfer from the frozen account.

Expected Result
The system should block the transaction and return an account status error.

Actual Result
The transfer request is processed successfully.

Impact
This is a **major compliance and fraud risk**, as frozen accounts should not allow financial operations.

Status
Open

---

# DEF-04 – Negative Transaction Amount Allowed

Module
Transaction Validation

Severity
High

Priority
High

API Endpoint
POST /transfer

Description
The API allows transactions with negative transfer amounts.

Steps to Reproduce

1. Initiate a transfer request.
2. Set the transfer amount to **-500**.

Expected Result
The system should reject negative transaction values.

Actual Result
Transaction is processed successfully.

Impact
Negative transaction amounts may cause **incorrect balance calculations and data corruption**.

Status
Open

---

# DEF-05 – Customer Created Without KYC Validation

Module
Customer Management

Severity
High

Priority
Medium

API Endpoint
POST /customers

Description
The system allows customer creation without mandatory KYC validation fields.

Steps to Reproduce

1. Send a customer creation request without providing KYC status.

Expected Result
Customer creation should fail with validation error.

Actual Result
Customer record is created successfully without KYC verification.

Impact
This violates **KYC compliance requirements**, which are mandatory for banking systems.

Status
Open

---

# Observations

During API testing several validation rules were not enforced by the simulated backend. These defects highlight missing validation logic related to:

• Idempotency protection
• Currency validation
• Account status validation
• Transaction amount validation
• KYC compliance checks

Such validations are critical in production banking systems to prevent fraud, ensure regulatory compliance, and maintain financial data integrity.
