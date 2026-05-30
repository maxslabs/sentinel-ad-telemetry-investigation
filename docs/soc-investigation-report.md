# SOC Incident Report – AD Log Ingestion Failure

## Summary
SecurityEvent logs (4624/4625) were not ingested into Sentinel.

## Observations
- Azure Arc: Connected
- AMA: Running
- DCR: Assigned
- Logs present: Heartbeat + 4688 only

## Conclusion
Partial telemetry ingestion due to configuration or filtering issue.

## Impact
No authentication visibility in SIEM.
