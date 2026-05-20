# oncology-authorization
Authorization workflow for high-value oncology drugs. Functional BA case study with business rules, BPMN, UAT, and financial impact.

# Authorization Workflow for High-Value Oncology Drugs

**Role:** Lead Functional Business Analyst  
**Client:** Public Healthcare System  
**Team:** 3 BAs, 3 UXers, 3 engineers (Engineer/Analyst pairs per user story)  
**Timeline:** 6 months

## 1. Business Problem

Public healthcare units in Mexico faced a critical drug shortage. High-value oncology medications —like abiraterone, costing ~$60,000 MXN per dose— were being dispensed without proper controls. The lack of inventory visibility meant physicians prescribed drugs that weren't in stock. Cancer patients were sent home empty-handed. The financial bleed was massive. The human cost was worse: delayed cancer treatment.

## 2. My Role

As Lead Functional Business Analyst, I gathered requirements from physicians, pharmacists, and hospital administrators. I designed the authorization workflow, defined business rules, documented user stories with acceptance criteria, modeled AS-IS and TO-BE processes in BPMN, coordinated UAT, and managed the backlog in JIRA.

## 3. Requirements Gathering

I conducted active listening sessions with physicians, pharmacists, and administrators, transcribed with Tactiq. The key finding: physicians had zero visibility into pharmacy inventory when prescribing. They prescribed on faith. Pharmacists manually checked stock after the patient arrived. If the drug wasn't there, the patient waited —sometimes days, sometimes indefinitely.

## 4. Proposed Solution (AS-IS / TO-BE)

**AS-IS:**
Physician prescribes → Patient goes to pharmacy → Pharmacist manually checks stock → If unavailable: patient returns home empty-handed.

**TO-BE:**
Physician prescribes → System checks real-time inventory → If available: authorized and dispensed → If unavailable: system suggests therapeutic alternatives based on COFEPRIS formulary.

[View AS-IS / TO-BE Diagram].

## 5. Key Artifacts

### Sample User Story

**As a** physician, **I want** to receive an on-screen notification when a prescribed medication is out of stock, **so that** I can select an authorized therapeutic alternative without making the patient wait.

**Acceptance Criteria:**
- The system must check inventory in real time when the physician selects a medication.
- If stock is zero, an alert must appear in less than 2 seconds.
- The alert must suggest at least 1 therapeutic alternative based on the COFEPRIS-authorized formulary.
- The system must log every instance for audit and inventory planning.

### Backlog & Tracking

Managed in JIRA with Confluence for functional specifications.

## 6. Business Rules & UAT

The most critical business rule for oncology drug authorization:

**"A high-value oncology drug can only be dispensed if ALL of the following are true:**
1. The patient's diagnosis is on the authorized list for that specific drug.
2. The medical unit chief has approved the prescription.
3. The time since the patient's last dose is consistent with the prescribed treatment regimen.

**If ANY condition fails, the system blocks the transaction."**

During UAT, I designed test scripts covering:
- **Happy path:** Valid prescription, all conditions met → drug dispensed.
- **Edge case 1:** Diagnosis not on authorized list → system blocks.
- **Edge case 2:** Chief approval missing → system blocks.
- **Edge case 3:** Dose too soon → system blocks.
- **Edge case 4:** Drug out of stock → system suggests alternatives.

All bugs were documented in JIRA with screenshots and followed up until closure.

## 7. Impact Measurement (KPIs)

| KPI | Before | After |
|:---|:---|:---|
| Oncology drug stockouts | Frequent, unmeasured | Reduced significantly |
| Patient wait time for alternative | Up to 3 days | Immediate (on-screen alternatives) |
| Unauthorized dispensing | Unmeasured | Zero (system-enforced) |
| Inventory traceability | Manual, paper-based | Real-time, automated |

## 8. Financial Impact & Business Case

Using the same methodology as the Payroll project, the financial impact was calculated based on avoided losses:

- **Abiraterone cost per dose:** ~$60,000 MXN.
- **Estimated unauthorized or wasted doses per month (before):** ~50 doses across the hospital network.
- **Monthly loss before:** ~$3,000,000 MXN.
- **Monthly loss after:** Near zero (system-enforced authorization).
- **Annualized savings:** ~$36,000,000 MXN.

Beyond the financials, the human impact was incalculable: cancer patients stopped being sent home without treatment.

### Why This Matters for a Business Analyst

This project didn't just add a feature to a system. It redesigned how life-saving drugs reached patients. The authorization workflow I designed ensured that every dose was traceable, justified, and dispensed only when medically appropriate. That is the real job of a Functional Business Analyst: not just documenting requirements, but designing processes that protect both the business and the people it serves.

## 9. Technologies

BPMN 2.0 (Bizagi), JIRA, Confluence, Tactiq, SQL (data validation during UAT).
