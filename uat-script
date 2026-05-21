# UAT Script: Oncology Drug Authorization Workflow

**Project:** Authorization Workflow for High-Value Oncology Drugs
**Role:** Lead Functional Business Analyst
**Date:** 2022

## Test Case 1: Happy Path – Valid Prescription, All Conditions Met

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Physician selects abiraterone for a patient with prostate cancer (authorized diagnosis). | System displays the medication and checks inventory. | ✅ Pass |
| 2 | Medical unit chief has pre-approved the prescription in the system. | System validates chief approval. | ✅ Pass |
| 3 | Patient's last dose was 28 days ago (consistent with treatment regimen). | System validates dose-time coherence. | ✅ Pass |
| 4 | Drug is in stock. | System authorizes dispensing. Inventory is updated automatically. | ✅ Pass |

## Test Case 2: Edge Case – Diagnosis Not on Authorized List

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Physician selects abiraterone for a patient with breast cancer (NOT an authorized diagnosis). | System displays an alert: "This medication is not authorized for the patient's diagnosis." | ✅ Pass |
| 2 | Physician attempts to override. | System blocks the transaction. Override requires medical unit chief and pharmacy director dual approval. | ✅ Pass |

## Test Case 3: Edge Case – Chief Approval Missing

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Physician prescribes abiraterone for an authorized diagnosis. | System checks authorization conditions. | ✅ Pass |
| 2 | Medical unit chief has NOT approved the prescription. | System displays: "Pending chief approval. Medication cannot be dispensed." | ✅ Pass |
| 3 | Physician attempts to bypass. | System blocks. Chief must approve before pharmacy can dispense. | ✅ Pass |

## Test Case 4: Edge Case – Dose Too Soon

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Physician prescribes abiraterone for an authorized diagnosis with chief approval. | System checks authorization conditions. | ✅ Pass |
| 2 | Patient's last dose was 7 days ago (treatment requires 28-day intervals). | System displays: "Dose too soon. Last dose: [date]. Next eligible date: [date]." | ✅ Pass |
| 3 | Physician attempts to override. | System blocks. Override requires pharmacy director approval with justification. | ✅ Pass |

## Test Case 5: Edge Case – Drug Out of Stock with Alternatives

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Physician prescribes abiraterone. All authorization conditions are met. | System checks inventory. | ✅ Pass |
| 2 | Abiraterone is out of stock. | System displays an alert in less than 2 seconds: "Medication out of stock." | ✅ Pass |
| 3 | System suggests alternatives. | System displays at least 3 therapeutic alternatives based on COFEPRIS formulary (e.g., enzalutamide, docetaxel, cabazitaxel). | ✅ Pass |
| 4 | Physician selects an alternative. | System updates the prescription and routes it to pharmacy with the alternative medication. | ✅ Pass |

## Test Case 6: Edge Case – Drug Out of Stock, No Alternatives Available

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Physician prescribes a rare oncology drug. All authorization conditions are met. | System checks inventory. | ✅ Pass |
| 2 | Drug is out of stock. | System displays alert. | ✅ Pass |
| 3 | No therapeutic alternatives exist in the COFEPRIS formulary. | System displays: "No alternatives available. Pharmacy director and treating physician must be notified." | ✅ Pass |
| 4 | System sends automatic notifications. | Pharmacy director and physician receive email and in-app notification. | ✅ Pass |

## Test Case 7: Edge Case – Multiple Simultaneous Prescriptions

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Two physicians prescribe the same oncology drug simultaneously. Only 1 dose remains in stock. | System processes both requests. | ✅ Pass |
| 2 | First prescription (earlier timestamp) is authorized. | Drug dispensed. Inventory updated to zero. | ✅ Pass |
| 3 | Second prescription (later timestamp) is processed. | System displays: "Out of stock" and suggests alternatives. | ✅ Pass |

## UAT Summary

| Total Test Cases | Passed | Failed | Blocked |
|:---|:---|:---|:---|
| 7 | 7 | 0 | 0 |

All defects were documented in JIRA with screenshots and followed up until closure.
