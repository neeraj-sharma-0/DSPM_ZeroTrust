# DSPM for Zero Trust — Data Exposure Lifecycle and Policy Enforcement

## Overview

Implements DSPM controls within a **Zero Trust model**, focusing on **data exposure and access decisions** rather than network perimeter security.

This repository applies classification, audit, and policy enforcement to determine **whether data access should be allowed, restricted, or denied**, with structured evidence for each decision.

This is a **data-centric Zero Trust governance framework**, not a full identity or network access system.

---

## Core Objective

> Apply DSPM principles to Zero Trust access decisions, ensuring sensitive data exposure is controlled, audited, and evidenced.

---

## What This Project Does

Given a set of data records and simulated access requests, the system:

1. **Classifies data**
   - sensitivity levels
   - PII types
   - secrets
   - ownership and source

2. **Evaluates access requests**
   - user / role context (simulated)
   - requested resource

3. **Audits exposure risk**
   - computes risk scores
   - assigns severity

4. **Enforces policy decisions**
   - allow / restrict / deny based on thresholds

5. **Generates evidence artifacts**
   - access decisions
   - risk findings
   - SHA256 receipts

6. **Records exposure lifecycle**
   - logs all access attempts
   - produces structured audit trail

---

## DSPM Lifecycle Coverage

| Stage    | Implementation                                      |
|----------|-----------------------------------------------------|
| Discover | Data classification and tagging                     |
| Classify | Sensitivity, PII, secrets, owner, source            |
| Audit    | Risk scoring for access requests                    |
| Enforce  | Policy decision: allow / restrict / deny            |
| Monitor  | Exposure tracking via access logs                   |

---

## Policy Enforcement

Access decisions are made based on:

- sensitivity level
- presence of PII or secrets
- risk score thresholds

Outputs include:

- decision (`allow`, `restrict`, `deny`)
- reason codes
- associated risk metrics

---

## Evidence Output

Artifacts written per run to:
