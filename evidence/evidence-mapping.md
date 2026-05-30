# SOC Evidence Mapping System – Active Directory Telemetry Investigation

This document maps collected evidence to specific components of the Azure Sentinel telemetry pipeline.

---

## Evidence Chain (End-to-End)

### 1. Azure Arc Onboarding State
- File: 01-arc-status.png
- Purpose: Validate endpoint registration in Azure Arc
- Finding: DC01 onboarded (status varies between connected/disconnected)

---

### 2. Azure Monitor Agent (AMA)
- File: 02-ama-status.png
- Purpose: Confirm telemetry agent is installed and operational
- Finding: AMA installed and running on DC01

---

### 3. Sentinel Heartbeat Validation
- File: 03-heartbeat.png
- Purpose: Confirm baseline connectivity to Log Analytics workspace
- Finding: Heartbeat logs present (partial connectivity confirmed)

---

### 4. Process Execution Telemetry (4688)
- File: 04-4688.png
- Purpose: Validate system-level SecurityEvent ingestion
- Finding: Process creation events successfully ingested

---

### 5. Authentication Telemetry Gap (4625)
- File: 05-missing-4625.png
- Purpose: Validate failed authentication logging
- Finding: No failed logon events observed in Sentinel

---

### 6. Data Collection Rule (DCR)
- File: 06-dcr-config.png
- Purpose: Define log ingestion scope and filtering rules
- Finding: DCR configured but authentication events not fully ingested

---

## Summary of Evidence Flow

Arc → AMA → Heartbeat → 4688 → Missing 4624/4625

---

## Key Observation

Telemetry pipeline is partially functional but fails at authentication layer, creating a SIEM visibility gap for identity-based attacks.
