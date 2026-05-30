# Azure Sentinel Active Directory SOC Lab (Troubleshooting Case Study)

## Overview
This lab documents Active Directory telemetry ingestion issues in Microsoft Sentinel using Azure Arc, AMA, and DCR.

## Objective
- Ingest Windows Security Events (4624/4625)
- Validate AD authentication logging in Sentinel
- Simulate brute-force attacks
- Build SOC detection using KQL

## Issue
Only 4688 and Heartbeat logs were visible.
SecurityEvent (4624/4625) was missing.

## Status
SOC troubleshooting case study (not fully resolved during lab)
