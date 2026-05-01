# DSPM + Zero Trust — Risk Tiering and Continuous Verification

## Overview

Implements a DSPM-aligned Zero Trust governance workflow using synthetic asset inventory and access-event data.

This repository focuses on:

- discovering data assets
- classifying sensitivity and exposure
- computing risk scores
- deriving Zero Trust policy tiers
- evaluating continuous verification signals
- planning destroy actions through a human-in-the-loop register
- mapping controls to MITRE ATT&CK techniques

This is a **governance and risk-tiering framework**, not a live IAM, network enforcement, or deletion execution system.

---

## What This Project Does

Given synthetic asset and access-event datasets, the notebooks:

1. **Load asset inventory**
   - asset type
   - owner team
   - region
   - sensitivity
   - PII / PHI flags
   - encryption posture
   - internet exposure
   - identity plane
   - retention period

2. **Compute risk scores**
   - sensitivity
   - PII / PHI
   - encryption gaps
   - internet exposure
   - retention posture

3. **Derive Zero Trust tiers**
   - `tier0_deny_by_default`
   - `tier1_strict_conditional`
   - `tier2_strong_auth`
   - `tier3_baseline`

4. **Build a controls catalog**
   - private endpoints
   - MFA
   - step-up verification
   - explicit allow per principal

5. **Monitor continuous verification signals**
   - MFA status
   - device compliance
   - trusted network
   - geo anomaly
   - admin / delete-attempt behavior

6. **Create planned destroy register**
   - assets requiring deletion planning
   - required approvals
   - scheduled destroy date
   - pending destroy action

7. **Map controls to MITRE ATT&CK**
   - exfiltration controls
   - credential abuse resistance
   - lateral movement limitation
   - anomaly-triggered verification

---

## DSPM Phase Coverage

| DSPM Phase | Implementation |
|---|---|
| Discover | Load synthetic asset inventory |
| Classify | Sensitivity, PII, PHI, exposure, encryption posture |
| Protect | Zero Trust tier derivation and controls catalog |
| Monitor | Continuous verification using synthetic access events |
| Destroy | Planned / human-in-the-loop destroy intent register |
| Reporting | MITRE ATT&CK control mapping |

---

## Zero Trust Tiering

Assets are assigned Zero Trust tiers based on risk posture:

| Tier | Meaning |
|---|---|
| `tier0_deny_by_default` | Highest-risk assets requiring strongest restrictions |
| `tier1_strict_conditional` | Sensitive assets requiring strict conditional access |
| `tier2_strong_auth` | Assets requiring strong authentication controls |
| `tier3_baseline` | Baseline governance tier |

Tiering is derived from synthetic asset attributes and computed risk scores.

---

## Continuous Verification

Synthetic access events are evaluated using verification signals such as:

- MFA enabled / missing
- device compliance
- trusted vs untrusted network
- geo anomaly
- privileged or destructive action attempts

This supports Zero Trust-style continuous verification analysis.

---

## Destroy Phase

The destroy phase is implemented as a **planned human-in-the-loop workflow**.

The repository generates or includes a destroy intent register with:

- `asset_id`
- `sensitivity`
- `required_approvals`
- `scheduled_for`
- `destroy_action`

Example destroy action:

```text
crypto_shred_or_logical_delete (pending)
