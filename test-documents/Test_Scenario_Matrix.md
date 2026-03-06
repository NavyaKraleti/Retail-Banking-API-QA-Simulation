# Test Scenario Matrix – Retail Banking API

This document lists the major functional, negative, compliance, and edge-case scenarios tested for the Retail Banking API simulation.

| Scenario ID | Module              | Scenario Description                               | Test Type     | API Endpoint                     | Expected Result                         |
| ----------- | ------------------- | -------------------------------------------------- | ------------- | -------------------------------- | --------------------------------------- |
| TS-01       | Environment Setup   | Initialize banking rules and environment variables | Functional    | GET /                            | Environment initialized successfully    |
| TS-02       | Customer Management | Create a new valid customer                        | Functional    | POST /customers                  | Customer created successfully           |
| TS-03       | Customer Management | Retrieve customer list                             | Functional    | GET /customers                   | Customer list returned                  |
| TS-04       | Customer Management | Attempt duplicate customer creation                | Negative      | POST /customers                  | System should reject duplicate customer |
| TS-05       | Customer Management | Create customer with missing fields                | Negative      | POST /customers                  | Validation error returned               |
| TS-06       | Compliance          | Create customer without KYC                        | Compliance    | POST /customers                  | Customer creation rejected              |
| TS-07       | Account Management  | Retrieve account details                           | Functional    | GET /accounts                    | Account details returned                |
| TS-08       | Funds Transfer      | Transfer funds between accounts                    | Functional    | POST /transfer                   | Transaction successful                  |
| TS-09       | Funds Transfer      | Transfer exceeding account balance                 | Negative      | POST /transfer                   | Transaction rejected                    |
| TS-10       | Funds Transfer      | Transfer with invalid currency                     | Negative      | POST /transfer                   | Currency validation error               |
| TS-11       | Compliance          | Transfer from frozen account                       | Compliance    | POST /transfer                   | Transaction blocked                     |
| TS-12       | Edge Case           | Rapid consecutive transfers                        | Risk Scenario | POST /transfer                   | Potential fraud detection               |
| TS-13       | Edge Case           | High value transaction                             | Risk Scenario | POST /transfer                   | AML check triggered                     |
| TS-14       | Negative            | Transfer with negative amount                      | Negative      | POST /transfer                   | Transaction rejected                    |
| TS-15       | Idempotency         | Duplicate transaction request                      | Edge Case     | POST /transfer                   | Duplicate prevented                     |
| TS-16       | End-to-End          | Deposit → Transfer → Verify balances               | E2E           | PATCH /accounts + POST /transfer | Balances updated correctly              |
| TS-17       | End-to-End          | Customer → Account → Transfer flow                 | E2E           | Multiple APIs                    | Complete flow successful                |
| TS-18       | Automation          | Run automated transaction simulation               | Automation    | Newman Runner                    | All test scenarios executed             |
