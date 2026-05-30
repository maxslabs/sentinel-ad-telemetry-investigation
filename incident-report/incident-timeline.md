# SOC Incident Timeline – AD Ingestion Failure

## Timeline of Events

### Phase 1 – Setup
- Windows Server 2022 (DC01) onboarded to Azure Arc
- Azure Monitor Agent (AMA) installed successfully
- Initial Data Collection Rule (DCR) created

---

### Phase 2 – Expected Behavior
- SecurityEvent logs (4624 / 4625) expected in Sentinel
- RDP brute-force simulation executed from attacker VM

---

### Phase 3 – Observed Behavior
- Only the following logs appeared:
  - Heartbeat (agent connectivity)
  - Event ID 4688 (process creation)

- Missing logs:
  - Event ID 4624 (successful logon)
  - Event ID 4625 (failed logon)

---

### Phase 4 – Investigation
- Verified Azure Arc connectivity → OK
- Verified AMA service → Running
- Verified DCR assignment → Initially missing, later corrected
- Rechecked Sentinel queries → No SecurityEvent ingestion

---

### Phase 5 – Conclusion
- Partial telemetry ingestion confirmed
- SecurityEvent channel not properly flowing into Log Analytics
- Root cause likely DCR filtering or Windows Security channel misconfiguration

---

## Impact
- No authentication visibility in SIEM
- Brute-force detection rules could not function
- SOC monitoring blind spot for login activity
