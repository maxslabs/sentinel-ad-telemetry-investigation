# SOC Evidence Mapping System

This document maps evidence collected during the Active Directory SOC ingestion investigation.

---

## Evidence Structure

### 1. Azure Arc Connectivity
- Evidence Type: System status
- Location: Azure Portal / Arc blade
- Purpose: Confirm DC01 is onboarded and reporting

---

### 2. AMA Agent Status
- Evidence Type: Agent telemetry
- Location: Windows Services / Azure Monitor Agent
- Purpose: Validate data pipeline is active

---

### 3. Data Collection Rule (DCR)
- Evidence Type: Configuration
- Location: Azure Monitor / DCR Assignment
- Purpose: Define which logs should be collected (SecurityEvent)

---

### 4. Sentinel Log Verification
- Evidence Type: Query output
- Location: Log Analytics Workspace
- Queries:
  - Heartbeat validation
  - Event ID 4688 process logs
  - Missing 4624 / 4625 authentication logs

---

### 5. Attack Simulation Evidence
- Evidence Type: Security events (expected but missing)
- Source: RDP brute-force simulation (attacker VM)
- Expected Logs:
  - 4625 failed logons
  - 4624 successful logons

---

## Evidence Status Summary

| Evidence Type | Status |
|----------------|--------|
| Arc Connectivity | OK |
| AMA Agent | OK |
| DCR Assignment | Partial / Misconfigured |
| SecurityEvent Logs | Missing |
| Heartbeat Logs | Present |
| Process Logs (4688) | Present |

---

## Key Finding
The pipeline is partially functional, but authentication telemetry is not flowing into Sentinel, creating a visibility gap in SOC monitoring.
