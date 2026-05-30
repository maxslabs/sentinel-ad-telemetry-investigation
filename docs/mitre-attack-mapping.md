# MITRE ATT&CK Mapping – Active Directory SOC Lab

This section maps observed and expected behavior in the lab to MITRE ATT&CK techniques.

---

## 1. Credential Access

### Technique: Brute Force
- **Tactic:** Credential Access
- **Technique ID:** T1110
- **Description:** Repeated authentication attempts against RDP to guess valid credentials.
- **Observed in Lab:** Simulated via attacker VM attempting RDP logins.
- **Expected Logs:** 4625 (failed logons)

---

## 2. Valid Accounts

### Technique: Valid Accounts
- **Tactic:** Initial Access / Persistence
- **Technique ID:** T1078
- **Description:** Successful authentication using legitimate credentials.
- **Observed in Lab:** Expected but not visible due to ingestion issue.
- **Expected Logs:** 4624 (successful logons)

---

## 3. Remote Services

### Technique: Remote Desktop Protocol
- **Tactic:** Lateral Movement / Initial Access
- **Technique ID:** T1021.001
- **Description:** Use of RDP for remote access into Windows Server (DC01).
- **Observed in Lab:** RDP used for brute-force simulation.
- **Expected Logs:** 4624 / 4625 with Logon Type 10

---

## 4. System Monitoring (Defensive Gap Identified)

### Technique: Missing Telemetry Coverage
- **Tactic:** Defense Evasion (visibility gap)
- **Description:** SecurityEvent logs not ingested into Sentinel.
- **Impact:** Detection rules cannot trigger without authentication data.
- **Observed Logs:**
  - Heartbeat (OK)
  - 4688 Process Creation (OK)
  - 4624 / 4625 (Missing)

---

## Key Insight

The attack simulation was successful at the endpoint level, but **SIEM visibility failed due to ingestion misconfiguration**, demonstrating a real-world SOC blind spot scenario.
