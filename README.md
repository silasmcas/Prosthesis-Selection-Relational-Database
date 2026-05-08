# Prosthesis Selection Database

**INFO 605 – Fall 2025 | Team 1**  
*Silas McAllister-Spooner, Virginia Muthard, and Phillip Roman*

---

## Overview

A relational database system designed to support evidence-based prosthetic care decisions for a clinical practice. The database tracks patients with unilateral lower-limb amputations, their assigned surgeons and clinicians, prosthetic component selections (foot, knee, hip), and longitudinal clinical outcome scores.

The goal is to transition prosthetic care from subjective, experience-driven workflows into a data-driven system — enabling clinicians to query component success rates by patient demographics, amputation level, and material type.

---

## Project Contents

| File | Description |
|---|---|
| `INFO605_Team01_SQLcode.txt` | Full Oracle SQL schema: `CREATE TABLE`, `INSERT`, `SELECT` queries |
| `Final Write-Up.docx` | Complete project report including requirements, ERD analysis, and business rules |
| `Conceptual Prx ERD.drawio` | Conceptual Entity-Relationship Diagram |
| `Logical Prx ERD.drawio` | Logical (normalized) Entity-Relationship Diagram |

---

## Database Schema

The database is implemented in **Oracle SQL** and contains 8 tables:

| Table | Description |
|---|---|
| `Surgeon` | Surgeon demographics and NPI identifier |
| `Clinician` | Clinician contact and personal info |
| `Patient` | Patient demographics, amputation level, linked to Surgeon and Clinician |
| `Foot` | Foot prosthetic component catalog (manufacturer, make) |
| `Knee` | Knee prosthetic component catalog |
| `Hip` | Hip prosthetic component catalog |
| `Prosthesis` | Individual prosthesis records linking patient, clinician, and components |
| `Visits` | Follow-up visit records with severity scores and outcomes |

### Amputation Levels & Component Rules

| Amputation Level | Foot | Knee | Hip |
|---|---|---|---|
| Transtibial (TT) | ✅ Required | ❌ | ❌ |
| Transfemoral (TF) | ✅ Required | ✅ Required | ❌ |
| Hip Disarticulation (HD) | ✅ Required | ✅ Required | ✅ Required |

---

## Key Business Rules

- Each patient is assigned to exactly **one surgeon** and **one clinician**.
- Each prosthesis belongs to exactly **one patient** and is fit by exactly **one clinician**.
- Component requirements are enforced by amputation level (see table above).
- Materials are limited to: **aluminum**, **titanium**, or **stainless steel**.
- Patients are between **18 and 90 years old** with a single unilateral amputation.
- HIPAA compliance is maintained through access-controlled credential-based login (application layer).

---

## How to Run the SQL

1. Open your Oracle SQL environment (e.g., SQL*Plus, Oracle SQL Developer, or a compatible IDE).
2. Run `INFO605_Team01_SQLcode.txt` in order — tables without foreign keys are created first to satisfy referential integrity.
3. Sample `INSERT` and `SELECT` queries are included at the bottom of the file for testing.

---

## ERD Diagrams

The `.drawio` files can be opened with:
- [draw.io (free, browser-based)](https://app.diagrams.net/)
- VS Code with the **Draw.io Integration** extension

Two diagrams are included:
- **Conceptual ERD** – High-level entity and relationship overview
- **Logical ERD** – Normalized schema with primary/foreign key annotations

---

## Project Scope

**In Scope**
- Patient, Surgeon, and Clinician data management
- Prosthetic component tracking (Foot, Knee, Hip)
- Clinical outcome scores and visit history
- SQL queries for analytical reporting

**Out of Scope**
- Scheduling or appointments
- Billing and insurance
- Inventory management

---

## Future Work

This database is designed as the architectural foundation for a **knowledge-based prosthetic recommender system**, capable of suggesting optimal component combinations based on patient demographics, amputation level, and historical outcome data.

---

## Course Info

- **Course:** INFO 605 – Database Management  
- **Term:** Fall 2025  
- **Institution:** [Your University Name]
