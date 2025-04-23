# 🔍 Findings – Day #19: Investigating Unusual User Creation with Splunk

## Overview
This lab focused on identifying unauthorized or suspicious user creation and password changes using Splunk to analyze Linux `auditd` logs.

---

## Key Findings

### 👥 1. User Creation Events
- Detected `20` unique users based on distinct UID appearances across the logs.
- SPL query used `dc(uid)` to count distinct users.

### 🔐 2. Password Change Activity
- UID `1015` accessed `/etc/shadow` using the `nano` editor.
- This behavior is consistent with modifying user credentials.
- Based on context, the user associated with UID `1015` is likely `david_wilson`.

---

## Risk Summary

| Indicator | Description |
|-----------|-------------|
| Access to `/etc/shadow` | Credential modification attempt |
| Unusual UID Activity | UID `1015` behavior flagged |
| No username mapping | Must rely on UID + behavior correlation |

---

## Conclusion
This Splunk investigation uncovered user creation activity and flagged suspicious credential file access linked to UID `1015`, potentially identifying privilege escalation or insider threat activity.

