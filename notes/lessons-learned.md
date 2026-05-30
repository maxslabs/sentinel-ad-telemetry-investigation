# Lessons Learned – Active Directory SOC Telemetry Investigation

## 1. Telemetry Ingestion Is Multi-Layered

Azure Sentinel visibility depends on multiple components working together:
- Azure Arc (endpoint onboarding)
- Azure Monitor Agent (data collection)
- Data Collection Rules (filtering and routing)
- Log Analytics / Sentinel (storage and analysis)

Failure at any layer results in partial or missing visibility.

---

## 2. Connectivity Impacts Security Visibility

Intermittent network connectivity (e.g., unstable or restricted networks) can result in:
- Loss of telemetry continuity
- Partial log ingestion
- False assumptions of system health

---

## 3. “Agent Connected” Does Not Mean “Logs Are Flowing”

A system can appear healthy in Azure Arc while:
- SecurityEvent logs are missing
- Authentication telemetry is not being ingested
- Detection rules are effectively blind

---

## 4. Importance of Incremental Validation

Effective SOC validation follows a layered approach:
- Heartbeat (basic connectivity)
- Process logs (system visibility)
- Authentication logs (security-critical data)

---

## 5. SOC Mindset Shift

This investigation highlights the difference between:
- **Lab mindset:** making systems work
- **SOC mindset:** understanding why visibility fails

---

## 6. Key Takeaway

Security monitoring effectiveness is not determined by agent installation, but by end-to-end telemetry integrity across the pipeline.
